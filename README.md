# Tugas Akhir — Arsitektur Zero Trust Adaptif Berbasis Machine Learning

**Judul:**
> Arsitektur Zero Trust Adaptif Berbasis Machine Learning untuk Deteksi Penyalahgunaan Kredensial Sah pada Trafik Terautentikasi

**Penulis:** Rizky Wildansani (Sani) — NIM 23/522276/SV/23644
**Program:** Proyek Akhir, Sarjana Terapan — UGM Sekolah Vokasi (TRI)
**Repo GitHub:** https://github.com/sanishiho23/Tugas-Akhir

---

## Deskripsi Singkat
Penelitian ini merancang purwarupa ZTA adaptif (ZTA statis + lapisan deteksi Random Forest)
dan menguji efikasi serta overhead-nya dibandingkan ZTA statis dan tradisional melalui
**tiga skenario terkontrol pada testbed container Docker**, dengan fokus mendeteksi
*abuse* kredensial sah pasca-autentikasi.

- **Skenario A** — arsitektur tradisional (baseline / perimeter)
- **Skenario B** — ZTA statis (micro-segmentation + mTLS + continuous auth)
- **Skenario C** — ZTA adaptif (B + lapisan deteksi Random Forest → closed-loop ke PDP)

---

## Struktur Repo

### Dokumen (hasil sendiri)
| File | Isi |
|---|---|
| `Proyek_Akhir_ZTA_Draft.docx` | Draf Bab I–III (IEEE [1]–[15]) |
| `Intisari_Proyek_Akhir_ZTA.docx` | Intisari (Bahasa Indonesia, ≤250 kata) |
| `Tinjauan_Literatur_ZTA_Adaptif.docx` | Tinjauan pustaka + RQ1–RQ4 |
| `Daftar_Pustaka_Tambahan_ZTA_Adaptif.docx` | Referensi tambahan (IEEE, entry web = perlu verifikasi) |
| `Rencana_Test_Case_ZTA_Adaptif.docx` | Rencana test case (TC-1…TC-5, gap-based) |

### Literatur / Referensi
- `1-Theory and Application of Zero Trust Security A Brief Survey.pdf`
- `2- 3696-12860-1-PB.pdf`
- `An_Artificial_Intelligence_Approach_for_Deploying_Zero_Trust_Architecture_ZTA.pdf`
- `Zero Trust Architecture.pdf`

### Contoh & Panduan
- `Contoh Skripsi ZTA.pdf`, `Implementasi ZTA.pdf` — contoh laporan
- `Ver-1.5-PEDOMAN-PENULISAN-PROYEK-AKHIR-DTEDI-1.docx-1.pdf` — pedoman penulisan DTEDI v1.2
- `Booklet-Panduan-Etika-Akademik-pada-Pendidikan-Tinggi-UGM-V3.pdf` — etika akademik UGM

---

## Status
- [x] Draft Bab I–III
- [x] Rencana test case (gap-based, TC-1…TC-5)
- [x] Daftar pustaka + referensi tambahan
- [ ] Implementasi testbed Docker (Skenario A/B/C)
- [ ] Eksperimen & hasil (Bab IV–V)

## Catatan
- Sitasi: IEEE numbered `[n]`. Ada konflik di pedoman DTEDI (§2.14 vs §3.4) — konfirmasi dengan pembimbing.
- Beberapa referensi web ditandai *[perlu verifikasi]* (jangan fabrikasi metadata).
- Testbed / skrip Docker akan ditambahkan pada folder terpisah saat implementasi.
