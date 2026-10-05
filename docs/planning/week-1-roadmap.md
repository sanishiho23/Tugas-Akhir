# Week 1 Roadmap — Initiation, Scope Lock & Bab I Finalization

**Duration:** 6–10 Oktober 2026 (Selasa–Sabtu)
**Owner:** Rizky Wildansani (Sani)
**Milestone:** M0 (maps ke weekly report M0, due Sabtu 10 Okt)
**Topic:** T1 + T2 — Architecture & Trends AND Data Integration & AI Analytics (+ Initiation). **Security lens:** ZTA adaptif detection (credential abuse). Federated learning = deferred.
**Reference:** [researchplan.md](researchplan.md) · [roadmap.md](roadmap.md) · [Rencana_Test_Case_ZTA_Adaptif.docx](../../Rencana_Test_Case_ZTA_Adaptif.docx) · [daily-log.md](../../daily-log.md)

---

## Overview
Minggu inisiasi. Tujuannya bukan output teknis berat, tetapi: (1) siapkan agenda & konsultasi pembimbing untuk kunci *scope* & judul, (2) verifikasi pernyataan *gap* (G1–G4) dari *full-text* literatur, (3) finalisasi Bab I (rumusan masalah, batasan, manfaat), (4) *lock* skenario & metrik, (5) rapikan repo & serahkan weekly report. Mirror BMW-Lab Week 1 (initiation + scope adoption), tapi untuk Tugas Akhir ZTA. Urutan harian di bawah **selaras dengan `daily-log.md`** (6–10 Okt = Selasa–Sabtu).

> **Instruksi pengendali:** fokus TA = ZTA adaptif + RF (Skenario C) sebagai kontribusi; Skenario A & B sebagai baseline. Jangan overclaim "algoritma baru" — posisikan sebagai *evaluasi empiris terkontrol + testbed reproducible*.

## Time-Block Convention
- **Pagi:** 08:00–12:00
- **Istirahat:** 12:00–13:00
- **Siang:** 13:00–17:00
- **Sabtu:** fleksibel (catch-up); **Minggu:** istirahat

## Goals
1. Konsultasi pembimbing: validasi judul + pernyataan *gap* (G1–G4) & keputusan sitasi IEEE.
2. Verifikasi *gap*: baca *full-text* Pokhrel 2024 & Winslow 2026 agar klaim akurat (bukan sekadar abstrak).
3. Finalisasi Bab I (1.1–1.6): rumusan masalah, batasan, manfaat, sistematika.
4. *Lock* skenario & metrik (3 skenario A/B/C, RQ1–RQ4, TC-1…TC-5).
5. Serahkan "weekly report" Minggu 1 ke pembimbing & *commit* repo.

---

## Daily Plan

### Selasa, 6 Okt — Kickoff & Konsultasi Pembimbing
- 08:00–12:00 — Siapkan agenda konsultasi; review draf Bab I–III & `Rencana_Test_Case_ZTA_Adaptif.docx`; tandai bagian yang perlu disetujui.
- 13:00–17:00 — Validasi judul + *gap* G1–G4 dengan pembimbing; konfirmasi gaya sitasi IEEE (konflik pedoman §2.14 vs §3.4); susun daftar terbuka pertanyaan.
- **Output:** agenda konsultasi; catatan persetujuan *scope*; judul final.

**Checklist & Evidence**
- [ ] Agenda konsultasi + draf pertanyaan (judul, *gap*, batasan, sitasi IEEE) disusun → [evidensi: daily-log 2026-10-06]
- [ ] Draf Bab I–III & `Rencana_Test_Case_ZTA_Adaptif.docx` di-review & ditandai → [evidensi: daily-log 2026-10-06]
- [ ] Judul + *gap* G1–G4 divalidasi pembimbing → [evidensi: daily-log 2026-10-06]
- [ ] Gaya sitasi IEEE diputuskan (§2.14 vs §3.4) → [evidensi: daily-log 2026-10-06]

### Rabu, 7 Okt — Verifikasi Gap (Literatur)
- 08:00–12:00 — Baca *full-text* Pokhrel 2024 (SIGCOMM ZTA workshop) & Winslow 2026 (ZTNA micro-seg logs); cek apakah mereka benar-benar tidak lakukan perbandingan A/B/C + overhead.
- 13:00–17:00 — Catat verifikasi *gap* (evidence-linked ke paper).
- **Output:** catatan verifikasi *gap* (evidence-linked ke paper).

**Checklist & Evidence**
- [ ] *Full-text* Pokhrel 2024 & Winslow 2026 dibaca → [evidensi: daily-log 2026-10-07]
- [ ] Catatan verifikasi *gap* G1–G4 (evidence-linked) → [evidensi: daily-log 2026-10-07]

### Kamis, 8 Okt — Finalisasi Bab I (1.1–1.6)
- 08:00–12:00 — Tulis 1.1 Latar Belakang, 1.2 Rumusan Masalah (RQ1–RQ4).
- 13:00–17:00 — Tulis 1.3 Tujuan, 1.4 Batasan, 1.5 Manfaat, 1.6 Sistematika.
- **Output:** Bab I final (lokal, sebelum commit).

**Checklist & Evidence**
- [ ] Bab I 1.1–1.6 final (lokal) → [evidensi: daily-log 2026-10-08, `docs/Proyek_Akhir_ZTA_Draft.docx`]

### Jumat, 9 Okt — Lock Skenario/Metrik + Re-check Bab I
- 08:00–12:00 — *Lock* skenario & metrik; pastikan Bab I final (lokal).
- 13:00–17:00 — Re-check exit criteria W1 (judul & *gap* disetujui, Bab I final, skenario terkunci).
- **Output:** skenario A/B/C + RQ1–RQ4 + TC-1…TC-5 terkunci.

**Checklist & Evidence**
- [ ] Skenario A/B/C + RQ1–RQ4 + TC-1…TC-5 terkunci → [evidensi: daily-log 2026-10-09]
- [ ] Bab I final di-re-check (1.1–1.6) → [evidensi: daily-log 2026-10-09, `docs/Proyek_Akhir_ZTA_Draft.docx`]

### Sabtu, 10 Okt — Weekly Report & Commit
- 08:00–12:00 — Susun ringkasan progres mingguan (M0).
- 13:00–17:00 — `git add -A && git commit` & (bila diizinkan) `git push`; serahkan weekly report ke pembimbing.
- **Output:** weekly report M0; commit repo.

**Checklist & Evidence**
- [ ] Weekly report M0 disusun & diserahkan → [evidensi: daily-log 2026-10-10]
- [ ] `git commit` (push bila diizinkan) → [evidensi: commit hash]

---

## Week 1 Exit Criteria
- [ ] Judul & *gap* G1–G4 disetujui pembimbing (06 Okt).
- [ ] *Gap* G1–G4 terverifikasi dari *full-text* (bukan sekadar abstrak) (07 Okt).
- [ ] Bab I final (1.1–1.6) (08 Okt).
- [ ] Skenario A/B/C + RQ1–RQ4 + TC-1…TC-5 terkunci (09 Okt).
- [ ] Weekly report M0 diserahkan + repo di-commit (10 Okt).

## Blockers & Open Questions
| Item | Impact | Resolution |
| :--- | :--- | :--- |
| Gaya sitasi IEEE pasti | Daftar Pustaka | Tanya pembimbing (06 Okt) |
| Apakah Pokhrel/Winslow sudah bandingkan A/B/C | Klaim *gap* | Baca *full-text* (07 Okt) |
| Jadwal konsultasi pembimbing | M0 | Koordinasi (06 Okt) |

## Week 2 Preview
**W2 (13–17 Okt) = T2 Literature & gap:** finalisasi Tinjauan Pustaka, pastikan 7 sub-bagian + tabel perbandingan metode (Bab II.1).

Cadence berikutnya: **W3 → T1/T4** (Dasar Teori + Bab III), **W4 → T4 testbed design**, **W5–W10 → implementasi A/B/C + RF**, **W11–W14 → eksperimen**, **W15–W18 → analisis & penulisan**, **W19–W27 → revisi, finalisasi, sidang**.

---
**Last updated:** 2026-10-05 · **Status:** In Progress (M0) · **Next review:** Sabtu 10 Okt (weekly report)
