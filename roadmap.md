# Roadmap Tugas Akhir — Arsitektur Zero Trust Adaptif Berbasis Machine Learning

**Disusun oleh:** Rizky Wildansani (Sani) — NIM 23/522276/SV/23644
**Program:** D4 / Sarjana Terapan — Teknologi Rekayasa Internet (TRI), UGM Sekolah Vokasi
**Pembimbing:** [nama dosen pembimbing]
**Topik:** Arsitektur Zero Trust Adaptif Berbasis Machine Learning untuk Deteksi Penyalahgunaan Kredensial Sah pada Trafik Terautentikasi
**Periode:** Oktober 2026 – April 2027 (~7 bulan / ~30 minggu)
**Target:** Laporan final selesai & sidang pada **April 2027**

> Gaya penulisan terinspirasi dari `docs/planning/` internship BMW-Lab (milestone + weekly + exit criteria). Fokus kali ini adalah Tugas Akhir ZTA (bukan O-RAN WG11 — itu proyek internship yang berbeda).

---

## Ruang Lingkup (Scope)
- **Testbed:** container Docker, 3 skenario terkontrol — **A** = tradisional (baseline), **B** = ZTA statis (mikrosegmentasi + mTLS + continuous auth), **C** = ZTA adaptif (B + lapisan deteksi Random Forest, closed-loop ke PDP).
- **Pertanyaan Riset:** RQ1 (kelemahan tradisional), RQ2 (efikasi ZTA statis), RQ3 (efektivitas RF), RQ4 (trade-off overhead).
- **Keluaran:** Laporan Bab I–V (format IEEE / Sarjana Terapan), testbed, presentasi, demo.

---

## Research Objectives (pemetaan ke RQ)
- **O1 (RQ1):** Demonstasikan pola akses tidak sah pada arsitektur tradisional berbasis perimeter (Skenario A).
- **O2 (RQ2):** Ukur efikasi ZTA statis terhadap penyalahgunaan kredensial sah (Skenario B).
- **O3 (RQ3):** Bangun & evaluasi lapisan deteksi Random Forest pada trafik terautentikasi sebagai autentikasi adaptif (Skenario C).
- **O4 (RQ4):** Kuantifikasi *trade-off* antara efektivitas deteksi dan overhead performa (latency, RTT, jitter, throughput) pada A/B/C.

---

## Milestones

| Milestone | Bulan | Fokus | Deliverable Utama | Status |
| :--- | :--- | :--- | :--- | :--- |
| **M0** | Okt 2026 | Penyelesaian dokumen awal + *lock* scope | Bab I–III draft, Intisari, Tinjauan Pustaka, Rencana Test Case, README + repo GitHub, validasi judul/gap dgn pembimbing | SELESAI SEBAGIAN |
| **M1** | Nov 2026 | Testbed Docker dasar + Skenario A | `docker-compose` topologi, container `client/server/attacker/log-collector/monitor`, Skenario A jalan, fitur flow/telemetry terkumpul, TC-1 | PLANNED |
| **M2** | Des 2026 | Implementasi ZTA statis + RF (Skenario B & C) | mikrosegmentasi+mTLS+continuous auth (B); RF (ekstraksi fitur, *train*, `rf-detector`, closed-loop ke PDP) (C); dataset berlabel TC-3a–3d | PLANNED |
| **M3** | Jan 2027 | Eksperimen TC-1…TC-5 | metrik efikasi (P/R/F1/AUC) + overhead (latency/RTT/jitter/throughput) + closed-loop; ulang 3× | PLANNED |
| **M4** | Feb 2027 | Analisis & penulisan Bab IV–V | Hasil & Pembahasan, Kesimpulan & Saran, finalisasi Daftar Pustaka | PLANNED |
| **M5** | Mar 2027 | Revisi & finalisasi laporan | konsultasi pembimbing, formatting IEEE/terapan, cek plagiasi, slide + video demo | PLANNED |
| **M6** | Apr 2027 | Sidang & penyerahan | gladi, ujian, revisi pasca-sidang, push repo final | PLANNED |

---

## Rencana Rinci per Fase

### Fase 0 — Penyelesaian Dokumen Awal (Oktober 2026) · M0
*Status: SELESAI SEBAGIAN.* Yang sudah ada: Bab I–III draft, Intisari, Tinjauan Literatu, Rencana Test Case (TC-1…TC-5), README + repo GitHub.

| Minggu | Task | Deliverable |
| :--- | :--- | :--- |
| 1–2 (6–17 Okt) | Konsultasi pembimbing: validasi judul & pernyataan gap (G1–G4). Verifikasi dengan baca *full-text* Pokhrel 2024 & Winslow 2026 (Methodology) agar klaim gap akurat. | Catatan konsultasi; gap final |
| 3–4 (20–31 Okt) | Finalisasi Bab I (rumusan masalah, batasan, manfaat) & kunci skenario + metrik; susun `roadmap.md` ini. | Bab I final; `roadmap.md` |

### Fase 1 — Persiapan Testbed (November 2026) · M1
- Setup Docker + `docker-compose`; definisikan topologi container: `client`, `server-app`, `attacker`, `log-collector`, `monitor`.
- Implementasi **Skenario A** (flat network, tanpa ZTA).
- Alat ukur: `tcpdump`/flow exporter (fitur), `iperf`/`netperf` (overhead).
- Jalankan **TC-1** (baseline lateral movement dgn kredensial valid).
- **Exit M1:** testbed Docker jalan; Skenario A teruji; fitur terkumpul.

### Fase 2 — Implementasi ZTA & RF (Desember 2026) · M2
- **Skenario B:** `ztp-gateway` (PEP — mikrosegmentasi + mTLS), `pdp`, `auth` (PA).
- **Skenario C:** `rf-detector` — ekstraksi fitur (flow/Sysmon-like), *train* RF (scikit-learn, offline), *deploy* container, closed-loop ke PDP (step-up auth / blokir).
- Generate **dataset berlabel**: TC-3a (replay token / impossible travel), 3b (eskalasi privilege), 3c (eksfiltrasi), 3d (credential stuffing) — kelas normal vs abuse.
- Uji **TC-2, TC-3, TC-5**.
- **Exit M2:** ketiga skenario jalan; RF terintegrasi; dataset berlabel siap.

### Fase 3 — Eksperimen (Januari 2027) · M3
- Jalankan **TC-1…TC-5** pada beban kerja identik A/B/C; ulangi 3× (per Bab III draf).
- Kumpulkan: P/R/F1/AUC (TC-3), % diblokir (TC-2), overhead (TC-4), false-positive & recovery time (TC-5).
- Setiap hasil dicatat ke `daily-log.md` + di-*link* ke *commit hash* (traceability).
- **Exit M3:** data eksperimen lengkap & konsisten.

### Fase 4 — Analisis & Penulisan (Februari 2027) · M4
- Analisis perbandingan A vs B vs C; jawab RQ1–RQ4.
- Tulis **Bab IV** (Hasil & Pembahasan) + **Bab V** (Kesimpulan & Saran).
- Gabung `Daftar_Pustaka_Tambahan_ZTA_Adaptif.docx` ke `[16]+`; pastikan sitasi IEEE konsisten.
- **Exit M4:** draf lengkap Bab I–V.

### Fase 5 — Revisi & Finalisasi (Maret 2027) · M5
- Konsultasi pembimbing (2–3×), revisi.
- Formatting (TNR 12pt, 1.5 spasi, IEEE), cek plagiasi, perbaiki diagram arsitektur.
- Slide presentasi 5–7 menit + video demo testbed ~5 menit.
- **Exit M5:** laporan final + slide + demo siap.

### Fase 6 — Sidang & Penyerahan (April 2027) · M6
- Gladi/residensi, sidang/ujian.
- Revisi pasca-sidang, penyerahan akhir ke perpustakaan/UGM.
- **Push repo final** (testbed + laporan) ke GitHub.
- **Exit M6:** LULUS / selesai.

---

## Test Case → Milestone Map
| Test Case | Skenario | Milestone |
| :--- | :--- | :--- |
| TC-1 (kelemahan tradisional) | A | M1 → M3 |
| TC-2 (efikasi ZTA statis) | B | M2 → M3 |
| TC-3 (deteksi RF — inti) | C | M2 → M3 |
| TC-4 (overhead performa) | A/B/C | M3 |
| TC-5 (loop adaptif) | C | M2 → M3 |

---

## Konvensi Waktu (Time-Block)
- **Senin–Jumat:** 08:00–12:00 (pagi) · 13:00–17:00 (siang); 12:00–13:00 istirahat.
- **Sabtu:** fleksibel (catch-up). **Minggu:** istirahat.
- **Daily-log:** log harian progres (terinspirasi BMW SOP §3.2) — tiap *claim* hasil di-*link* ke *section* dokumen atau *commit hash* 7 digit.

---

## Success Criteria (Exit Criteria)
- [x] **M0:** dokumen awal final; judul & gap disetujui pembimbing.
- [ ] **M1:** testbed Docker jalan; Skenario A teruji; fitur terkumpul.
- [ ] **M2:** Skenario B & C jalan; RF terintegrasi; dataset berlabel siap.
- [ ] **M3:** TC-1…TC-5 selesai; metrik lengkap (3 ulangan).
- [ ] **M4:** Bab IV–V tertulis; RQ1–RQ4 terjawab.
- [ ] **M5:** laporan final + slide + demo siap.
- [ ] **M6:** sidang lulus; repo final *push*.

---

## Blockers & Open Questions
| Item | Dampak | Resolusi |
| :--- | :--- | :--- |
| Akses/izin Docker di lab atau PC pribadi | Gateness M1 | Pastikan Docker terinstal & kompatibel; uji container ringan dulu |
| Pemilihan tools PDP/PEP (OPA vs custom; nginx/Envvy untuk mTLS) | Desain Skenario B/C | Eksplorasi OPA + Envoy/nginx; pilih yg ringan & reproducible |
| Ketersediaan dataset *abuse* | TC-3 butuh data berlabel | Generate sendiri (normal vs TC-3a–3d) — sudah direncanakan M2 |
| Konfirmasi gaya sitasi IEEE (konflik pedoman §2.14 vs §3.4) | Daftar Pustaka | Tanya pembimbing sebelum finalisasi (M4) |
| Jadwal sidang UGM pasti di April 2027 | M6 | Konfirmasi tanggal dgn koordinator TA/sekolah |

---

**Last updated:** 2026-10-03 · **Status:** M0 in progress · **Next review:** konsultasi pembimbing (Minggu 1–2 Okt)
