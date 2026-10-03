# Tugas Akhir — Arsitektur Zero Trust Adaptif Berbasis Machine Learning

**Judul:**
> Arsitektur Zero Trust Adaptif Berbasis Machine Learning untuk Deteksi Penyalahgunaan Kredensial Sah pada Trafik Terautentikasi

> Repositori ini mengikuti SOP penulisan Proyek Akhir DTEDI/UGM (lihat `Ver-1.5-PEDOMAN-PENULISAN-PROYEK-AKHIR-DTEDI-1.docx-1.pdf`) dan struktur dokumentasi terinspirasi dari BMW-Lab Internship SOP (Profil → Ringkasan → Struktur → Konvensi → Checklist).

---

## 1. Profil
- **Nama:** Rizky Wildansani (Sani)
- **NIM:** 23/522276/SV/23644
- **Email:** rizkywildansani@mail.ugm.ac.id
- **Universitas:** Universitas Gadjah Mada (UGM)
- **Program:** D4 / Sarjana Terapan — Teknologi Rekayasa Internet (TRI), Sekolah Vokasi
- **IPK:** [isi IPK]
- **Topik:** Arsitektur Zero Trust Adaptif berbasis Machine Learning untuk Deteksi Penyalahgunaan Kredensial Sah pada Trafik Terautentikasi
- **Pembimbing:** [nama dosen pembimbing]
- **Portfolio:** [LinkedIn] · [CV] · [GitHub]

---

## 2. Ringkasan Proyek
**Ruang lingkup (Proyek Akhir, 2 semester):** merancang purwarupa ZTA adaptif (ZTA statis + lapisan deteksi Random Forest) dan menguji efikasi serta overhead-nya dibandingkan ZTA statis dan tradisional melalui **tiga skenario terkontrol pada testbed container Docker**, dengan fokus mendeteksi *abuse* kredensial sah pasca-autentikasi.

**Komponen ZTA (basis NIST SP 800-207):**

| Komponen | Fungsi | Implementasi (Docker) |
|---|---|---|
| **PDP** (Policy Decision Point) | Memutuskan allow / deny | container `pdp` (policy engine) |
| **PEP** (Policy Enforcement Point) | Memaksa mikrosegmentasi + mTLS | container `ztp-gateway` |
| **PA** (Policy Administration) | Autentikasi berkelanjutan | container `auth` |
| **Lapisan deteksi RF** | Skor anomali → masuk ke PDP | container `rf-detector` (Skenario C) |

**Skenario (load-bearing, per rancangan):**
- **A** = tradisional (flat network, baseline / perimeter)
- **B** = ZTA statis (mikrosegmentasi + mTLS + continuous auth)
- **C** = ZTA adaptif (B + RF, closed-loop ke PDP → "adaptif")

**Ditunda / pengembangan lanjutan (bukan bagian eksekusi inti TA):** eksperimen Bab IV–V (hasil pengujian) dan perluasan ke publikasi jurnal (adaptive ZTA + federated learning).

**Pertanyaan Riset (RQ):**
- **RQ1:** Bagaimana pola akses tidak sah dapat terjadi pada arsitektur tradisional berbasis perimeter?
- **RQ2:** Sejauh mana efikasi ZTA statis terhadap penyalahgunaan kredensial sah?
- **RQ3:** Seberapa efektif Random Forest mendeteksi anomali pada trafik terautentikasi sebagai lapisan autentikasi adaptif?
- **RQ4:** Apa *trade-off* antara efektivitas deteksi dan overhead performa (latency, RTT, jitter, throughput)?

**Rencana uji (gap-based, TC-1…TC-5):** lihat `Rencana_Test_Case_ZTA_Adaptif.docx`
- TC-1: validasi kelemahan perimeter tradisional (RQ1, Skenario A)
- TC-2: efikasi ZTA statis vs penyalahgunaan kredensial (RQ2, Skenario B)
- TC-3: deteksi abuse kredensial sah oleh RF (RQ3, Skenario C) — inti kontribusi
- TC-4: *trade-off* overhead performa (RQ4, A/B/C)
- TC-5: bukti *loop* adaptif (closed-loop, RQ2+RQ3, Skenario C)

---

## 3. Struktur Repositori (folder berbasis topik)
```
.
├── README.md                       # file ini (SOP DTEDI §profil + struktur BMW-Lab)
├── .gitignore
├── docs/                           # dokumen hasil sendiri
│   ├── Proyek_Akhir_ZTA_Draft.docx
│   ├── Intisari_Proyek_Akhir_ZTA.docx
│   ├── Tinjauan_Literatur_ZTA_Adaptif.docx
│   ├── Daftar_Pustaka_Tambahan_ZTA_Adaptif.docx
│   └── Rencana_Test_Case_ZTA_Adaptif.docx
├── literatur/                      # referensi PDF
│   ├── 1-Theory and Application of Zero Trust Security A Brief Survey.pdf
│   ├── 2- 3696-12860-1-PB.pdf
│   ├── An_Artificial_Intelligence_Approach_for_Deploying_Zero_Trust_Architecture_ZTA.pdf
│   └── Zero Trust Architecture.pdf
├── panduan/                        # pedoman & contoh
│   ├── Ver-1.5-PEDOMAN-PENULISAN-PROYEK-AKHIR-DTEDI-1.docx-1.pdf
│   ├── Booklet-Panduan-Etika-Akademik-pada-Pendidikan-Tinggi-UGM-V3.pdf
│   ├── Contoh Skripsi ZTA.pdf
│   └── Implementasi ZTA.pdf
└── testbed/                        # (akan ditambahkan) docker-compose, skrip RF, collector
```

> **Catatan:** saat ini seluruh file dokumen/literatur/panduan berada di *root* repositori. Pengorganisasian ke subfolder `docs/`, `literatur/`, `panduan/` akan dilakukan pada pembaruan berikutnya tanpa mengubah nama file.

---

## 4. Konvensi Dokumentasi
- **Log harian** → `daily-log.md`, format terinspirasi BMW SOP: `### yyyy-mm-dd`, daftar *Short-term Goal*, dan *task bullet* ber-timestamp `hh:mm–hh:mm` yang terhubung ke bukti (section dokumen atau hash commit 7 digit). Memudahkan *traceability* progres TA.
- **Sitasi** → IEEE numbered `[n]`. Ada konflik di pedoman DTEDI (§2.14 vs §3.4) — konfirmasi dengan pembimbing sebelum finalisasi.
- **Evidence links** → tiap klaim hasil mengacu ke bagian dokumen atau *commit hash* (7 digit) supaya dapat diverifikasi oleh penguji.
- **Penamaan file** → `<Jenis>_<Topik>.docx` (mis. `Proyek_Akhir_ZTA_Draft.docx`).

---

## 5. Checklist Penyelesaian Tugas Akhir (SOP DTEDI)

**GitHub / Repositori:**
- [x] Dokumen utama (README, draft Bab I–III, intisari, tinjauan pustaka)
- [x] Daftar pustaka + referensi tambahan
- [x] Rencana test case (TC-1…TC-5, gap-based)
- [ ] Testbed Docker (`docker-compose`, skrip RF, collector)
- [ ] Panduan instalasi / penggunaan
- [ ] Arsitektur & *call flow* (diagram PDP↔PEP↔RF)

**Laporan:**
- [x] Draf Bab I–III
- [ ] Bab IV–V (hasil & analisis)
- [x] Intisari (Bahasa Indonesia, ≤250 kata)
- [ ] Laporan final (format IEEE / Sarjana Terapan)

**Presentasi & Demo:**
- [ ] Slide presentasi 5–7 menit (use case, arsitektur, I/O, hasil & analisis)
- [ ] Video demo testbed (~5 menit, subtitle ID/EN)

---

## 6. Referensi
- **Pedoman:** `Ver-1.5-PEDOMAN-PENULISAN-PROYEK-AKHIR-DTEDI-1.docx-1.pdf` (DTEDI v1.2)
- **Etika akademik UGM:** `Booklet-Panduan-Etika-Akademik-pada-Pendidikan-Tinggi-UGM-V3.pdf`
- **Contoh laporan:** `Contoh Skripsi ZTA.pdf`, `Implementasi ZTA.pdf`
- **Repo GitHub:** https://github.com/sanishiho23/Tugas-Akhir
