# ZTA_TEST_SCOPE

Dokumen ini memuat **ruang lingkup pengujian (test scope)** untuk purwarupa
Arsitektur Zero Trust Adaptif berbasis Machine Learning: perangkat yang dipakai
(*tools*), prasyarat (*requirements*), dan langkah kerja (*steps*). Semua terikat
ke rencana uji **TC-1 sampai TC-5** dan *research question* **RQ1 sampai RQ4**
lihat juga `docs/Rencana_Test_Case_ZTA_Adaptif.docx` dan `docs/Laporan_Proyek_Akhir_ZTA_contoh.docx`.

Tujuan pengujian: membuktikan secara empiris bahwa ZTA adaptif (Skenario C = ZTA
statis + Random Forest) lebih baik menangani penyalahgunaan kredensial sah
pasc authentikasi dibanding ZTA statis (B) dan tradisional (A), sekaligus
mengukur *overhead* yang timbul.

---

## 1. Arsitektur Testbed (sekilas)

Empat *container* Docker, dihubungkan lewat *bridge network* dan mTLS:

| Container | Peran ZTA | Ada di skenario |
|-----------|-----------|----------------|
| `pdp` | Policy Decision Point (PDP) | A, B, C |
| `ztp-gateway` | Policy Enforcement Point (PEP): mikrosegmentasi + mTLS | B, C |
| `auth` | Policy Administration (PA): autentikasi berkelanjutan | B, C |
| `rf-detector` | Lapisan deteksi anomali Random Forest, menutup loop ke PDP | C saja |

- **Skenario A** (tradisional): hanya `pdp`, jaringan *flat*, autentikasi di gerbang awal.
- **Skenario B** (ZTA statis): `pdp` + `ztp-gateway` + `auth`.
- **Skenario C** (ZTA adaptif): B + `rf-detector`; skor anomali RF dimasukkan ke PDP (closed-loop).

---

## 2. Tools / Perangkat

| Kategori | Tool | Keperluan |
|----------|------|-----------|
| Containerization | Docker Engine 24+, Docker Compose v2 | Menjalankan 4 container & mengisolasi jaringan |
| Bahasa / ML | Python 3.11+, `scikit-learn`, `pandas`, `numpy` | Training & inferensi Random Forest, ekstraksi fitur |
| ML serving | Skrip `rf-detector` (Flask/FastAPI opsional) | Mengekspos skor anomali ke PDP |
| Metrik jaringan | `iperf3` | Throughput |
| | `ping` / `fping` | RTT, latency tambahan |
| | `mtr` atau `owping` (opsional) | Jitter |
| Capture / fitur | `tshark` (Wireshark CLI) atau `scapy` | Ambil statistik flow, entropi, volume byte |
| Simulasi serangan | Python scripts / `curl` / `k6` | Replay token, impossible travel, eskalasi, eksfiltrasi |
| Orchestration | Bash / Python runner | Jalankan TC berurutan & kumpulkan log |
| Version control | `git` | Pelacakan versi & kolaborasi (repo GitHub) |

---

## 3. Requirements / Prasyarat

### 3.1 Hardware
- Host dengan Docker: minimal **8 GB RAM, 4 vCPU, 20 GB disk**.
- Jika butuh beban tinggi: VM/cloud (NTUST atau akses remote, Nov 2026 - Jan 2027 per program TEEP).

### 3.2 Software
- OS: Linux / macOS / Windows + WSL2.
- Docker Engine + Docker Compose v2 terpasang.
- Python 3.11 dan `pip install scikit-learn pandas numpy`.
- (Opsional) Wireshark (`tshark`) untuk *capture* trafik.

### 3.3 Dataset / Traffic
- **Baseline trafik normal** (Skenario A/B/C tanpa serangan) untuk melatih RF.
- **Labeled abuse**: TC-3a replay token, TC-3b impossible travel, TC-3c eskalasi privilege,
  TC-3d eksfiltrasi — dibuat lewat skrip simulasi serangan dan divalidasi manual.

### 3.4 Akses
- Repo GitHub `sanishiho23/Tugas-Akhir`.
- Dokumen `docs/Rencana_Test_Case_ZTA_Adaptif.docx` untuk detail tiap TC.

---

## 4. Steps / Langkah Pengujian

### Step 0 - Persiapan
```bash
git clone <repo> && cd <repo>/testbed
docker compose build
docker compose up -d
# cek container sehat: pdp, ztp-gateway, auth, (rf-detector hanya untuk C)
docker compose ps
```

### Step 1 - Koleksi baseline & training RF (TC-3 pra-syarat)
1. Hasilkan trafik normal pada Skenario B/C.
2. Ekstrak fitur: statistik flow, durasi sesi, volume byte, entropi, *inter-arrival time*.
3. Latih `RandomForestClassifier` (kelas: normal vs anomali dari TC-3a..3d).
4. Kalibrasi *threshold* skor anomali (keseimbangan deteksi vs *false-positive*).

### Step 2 - Skenario A (TC-1, RQ1)
- Jalankan tanpa ZTA; simulasikan akses tidak sah.
- Catat rasio akses lolos sebagai *baseline* kelemahan perimeter.

### Step 3 - Skenario B (TC-2, RQ2)
- Aktifkan `ztp-gateway` + `auth`; ulangi serangan.
- Catat efikasi ZTA statis menahan penyalahgunaan kredensial sah.

### Step 4 - Skenario C (TC-3a..3d RQ3 + TC-5 RQ2+RQ3)
- Aktifkan `rf-detector`; jalankan tiap kasus abuse.
- Catat **precision, recall, F1-score** deteksi RF.
- Buktikan *loop adaptif*: skor RF -> PDP -> akses ditarik (TC-5).

### Step 5 - TC-4 (RQ4, overhead)
- Pada A/B/C jalankan `iperf3` + `ping`.
- Ukur latency tambahan, RTT, jitter, throughput; **ulangi minimal 3x** agar adil.

### Step 6 - Kumpulkan & isi tabel
- Rangkum hasil ke Bab IV: 4.1 efikasi pencegahan, 4.2 performa deteksi,
  4.3 overhead, 4.4 bukti loop adaptif.

---

## 5. Metrics (pemetaan RQ)

| RQ | Metrik | Instrumen | Skenario |
|----|--------|-----------|----------|
| RQ1 | Rasio akses tidak sah lolos | log gateway | A |
| RQ2 | Efikasi pencegahan ZTA statis | log gateway | B |
| RQ3 | Precision / Recall / F1-score deteksi RF | skrip evaluasi | C |
| RQ4 | Latency, RTT, jitter, throughput | iperf3, ping | A/B/C |

---

## 6. Pemetaan TC -> RQ -> Skenario

| TC | Fokus | RQ | Skenario |
|----|-------|----|----------|
| TC-1 | Kelemahan perimeter tradisional | RQ1 | A |
| TC-2 | Efikasi ZTA statis vs abuse | RQ2 | B |
| TC-3a | Replay token | RQ3 | C |
| TC-3b | Impossible travel | RQ3 | C |
| TC-3c | Eskalasi privilege | RQ3 | C |
| TC-3d | Eksfiltrasi | RQ3 | C |
| TC-4 | Trade-off overhead | RQ4 | A/B/C |
| TC-5 | Bukti loop adaptif | RQ2 + RQ3 | C |

---

## 7. Exit Criteria (kapan scope dianggap selesai)
- Keempat container berjalan & sehat pada Skenario C.
- Model RF terlatih dengan *threshold* terkalibrasi.
- TC-1 sampai TC-5 tereksekusi; metrik tercatat minimal 3 ulangan.
- Tabel Bab IV (4.1-4.4) terisi dari hasil pengukuran.

---

## 8. Limitations
- Uji dilakukan di testbed skala laboratorium, bukan produksi.
- Angka *overhead* bersifat relatif antar skenario, bukan angka absolut produksi.
- RF dipakai sebagai komponen yang diintegrasikan, bukan algoritma baru.
