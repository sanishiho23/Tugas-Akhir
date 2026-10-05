# Week 1 Roadmap — Initiation, Scope Lock & Bab I Finalization

**Duration:** 6–10 Oktober 2026 (Senin–Jumat)
**Owner:** Rizky Wildansani (Sani)
**Milestone:** M0 (maps ke weekly report M0, due Jumat 10 Okt)
**Topic:** T1 + T2 — Architecture & Trends AND Data Integration & AI Analytics (+ Initiation). **Security lens:** ZTA adaptif detection (credential abuse). Federated learning = deferred.
**Reference:** [researchplan.md](researchplan.md) · [roadmap.md](roadmap.md) · [Rencana_Test_Case_ZTA_Adaptif.docx](../../Rencana_Test_Case_ZTA_Adaptif.docx) · [daily-log.md](../../daily-log.md)

---

## Overview
Minggu inisiasi. Tujuannya bukan output teknis berat, tetapi: (1) kunci *scope* & judul dengan pembimbing, (2) verifikasi pernyataan *gap* (G1–G4) dari *full-text* literatur, (3) finalisasi Bab I (rumusan masalah, batasan, manfaat), (4) rapikan repo & dokumen. Mirror BMW-Lab Week 1 (initiation + scope adoption), tapi untuk Tugas Akhir ZTA.

> **Instruksi pengendali:** fokus TA = ZTA adaptif + RF (Skenario C) sebagai kontribusi; Skenario A & B sebagai baseline. Jangan overclaim "algoritma baru" — posisikan sebagai *evaluasi empiris terkontrol + testbed reproducible*.

## Time-Block Convention
- **Pagi:** 08:00–12:00
- **Istirahat:** 12:00–13:00
- **Siang:** 13:00–17:00
- **Sabtu:** fleksibel (catch-up); **Minggu:** istirahat

## Goals
1. Konsultasi pembimbing: validasi judul + pernyataan *gap* (G1–G4).
2. Verifikasi *gap*: baca *full-text* Pokhrel 2024 & Winslow 2026 (Methodology) agar klaim akurat (bukan sekadar abstrak).
3. Finalisasi Bab I (1.1–1.6): rumusan masalah, batasan, manfaat, sistematika.
4. *Lock* skenario & metrik (3 skenario A/B/C, RQ1–RQ4, TC-1…TC-5).
5. Serahkan "weekly report" Minggu 1 ke pembimbing (progres + scope).

---

## Daily Plan

### Senin, 6 Okt — Kickoff & Scope Alignment
- Siapkan agenda konsultasi; susun draf pertanyaan untuk pembimbing (judul, gap, batasan).
- Review draf Bab I–III & `Rencana_Test_Case_ZTA_Adaptif.docx`; tandai bagian yang perlu disetujui.
- **Output:** agenda konsultasi; daftar terbuka.

### Selasa, 7 Okt — Konsultasi Pembimbing (priority)
- Validasi judul + *gap* G1–G4; konfirmasi pemilihan sitasi IEEE (konflik pedoman §2.14 vs §3.4).
- **Output:** catatan persetujuan *scope*; judul final.

### Rabu, 8 Okt — Verifikasi Gap (Literatur)
- Baca *full-text* Pokhrel 2024 (SIGCOMM ZTA workshop) & Winslow 2026 (ZTNA micro-seg logs); cek apakah mereka benar-benar tidak lakukan perbandingan A/B/C + overhead.
- **Output:** catatan verifikasi *gap* (evidence-linked ke paper).

### Kamis, 9 Okt — Finalisasi Bab I
- Tulis/perbaiki 1.1 Latar Belakang, 1.2 Rumusan Masalah (RQ1–RQ4), 1.3 Tujuan, 1.4 Batasan, 1.5 Manfaat, 1.6 Sistematika.
- **Output:** Bab I final (lokal, sebelum commit).

### Jumat, 10 Okt — Weekly Report & Commit
- Susun ringkasan progres mingguan; `git add -A && git commit` & (bila diizinkan) `git push`.
- **Output:** weekly report M0; commit repo.

---

## Week 1 Exit Criteria
- [ ] Judul & *gap* disetujui pembimbing.
- [ ] *Gap* G1–G4 terverifikasi dari *full-text* (bukan sekadar abstrak).
- [ ] Bab I final (1.1–1.6).
- [ ] Skenario A/B/C + RQ + TC terkunci.
- [ ] Weekly report M0 diserahkan.

## Blockers & Open Questions
| Item | Impact | Resolution |
| :--- | :--- | :--- |
| Gaya sitasi IEEE pasti | Daftar Pustaka | Tanya pembimbing (Selasa) |
| Apakah Pokhrel/Winslow sudah bandingkan A/B/C | Klaim *gap* | Baca *full-text* (Rabu) |
| Jadwal konsultasi pembimbing | M0 | Koordinasi Senin |

## Week 2 Preview
**W2 (13–17 Okt) = T2 Literature & gap:** finalisasi Tinjauan Pustaka, pastikan 7 sub-bagian + tabel perbandingan metode (Bab II.1).

Cadence berikutnya: **W3 → T1/T4** (Dasar Teori + Bab III), **W4 → T4 testbed design**, **W5–W10 → implementasi A/B/C + RF**, **W11–W14 → eksperimen**, **W15–W18 → analisis & penulisan**, **W19–W27 → revisi, finalisasi, sidang**.

---
**Last updated:** 2026-10-05 · **Status:** In Progress (M0) · **Next review:** Jumat 10 Okt (weekly report)
