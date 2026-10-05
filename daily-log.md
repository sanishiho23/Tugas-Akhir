# Daily Log — Tugas Akhir ZTA Adaptif

**SOP:** terinspirasi BMW-Lab Internship §3.2 (Milestones di atas, Daily Logs di bawah). Setiap *task bullet* ber-timestamp `hh:mm–hh:mm` dan terhubung ke bukti (*section* dokumen atau *commit hash* 7 digit) agar dapat diverifikasi.
**Owner:** Rizky Wildansani · **Repo:** github.com/sanishiho23/Tugas-Akhir
**Acuan:** `docs/planning/researchplan.md` (cadence W1–W27, M0–M6) · `docs/planning/week-1-roadmap.md` (W1)

---

## Milestones
- **M0** (Okt 2026) — Dokumen awal + *lock* scope — **IN PROGRESS (W1)**
- **M1** (Nov 2026) — Testbed Docker + Skenario A — PLANNED
- **M2** (Des 2026) — ZTA statis + RF (Skenario B & C) — PLANNED
- **M3** (Jan 2027) — Eksperimen TC-1…TC-5 — PLANNED
- **M4** (Feb 2027) — Bab IV–V — PLANNED
- **M5** (Mar 2027) — Revisi & finalisasi — PLANNED
- **M6** (Apr 2027) — Sidang & penyerahan — PLANNED

---

## 2026-10-05 (Senin)
**Short-term Goal:**
Siapkan struktur *planning* TA (researchplan, week-1-roadmap, daily-log) & rapikan repo.

**Daily Plan:**
- 15:00–15:30 — Reorganisasi repo ke folder `docs/` `literatur/` `panduan/` `testbed/`
- 15:30–16:30 — Buat `docs/planning/researchplan.md` (tema, T1–T4, threat model, cadence mingguan W1–W27)
- 16:30–17:00 — Buat `docs/planning/week-1-roadmap.md` (M0, goals, daily plan 6–10 Okt)
- 17:00–17:20 — Buat `daily-log.md` (milestones + log hari ini)

**Daily Log:**
- 15:00–15:30 — Reorganisasi repo ke folder `docs/` `literatur/` `panduan/` `testbed/` (commit `1f622ea`). [evidensi: commit `1f622ea`]
- 15:30–16:30 — Buat `docs/planning/researchplan.md` (tema, T1–T4, threat model, cadence mingguan W1–W27). [evidensi: `docs/planning/researchplan.md` + commit `9c72ad1`]
- 16:30–17:00 — Buat `docs/planning/week-1-roadmap.md` (M0, goals, daily plan 6–10 Okt). [evidensi: `docs/planning/week-1-roadmap.md` + commit `9c72ad1`]
- 17:00–17:20 — Buat `daily-log.md` (milestones + log hari ini). [evidensi: `daily-log.md` + commit `9c72ad1`]

**Unplanned work (appeared during the day; recorded per SOP §3.2):**
- 16:16–16:25 — Literature search (academic-literature-search ×3, WebSearch; Perplexity unavailable) + pertegas batasan TA vs O-RAN mTLS di Bab I.4 & Bab II.1 + 9 referensi baru (commit `9221f48`). [evidensi: commit `9221f48`, `docs/Proyek_Akhir_ZTA_Draft.docx`]
- 16:25–16:43 — Tambah `Panduan-Etika-Akademik-Pemanfaatan-AI-1.pdf` (UGM) ke `panduan/` (commit `eb3c92b`). [evidensi: commit `eb3c92b`, `panduan/Panduan-Etika-Akademik-Pemanfaatan-AI-1.pdf`]

---

## 2026-10-06 (Selasa)
**Short-term Goal:**
M0: Konsultasi pembimbing — validasi judul & *gap* G1–G4.

**Daily Plan:**
- 08:00–12:00 — Siapkan agenda konsultasi; review draf Bab I–III & `Rencana_Test_Case_ZTA_Adaptif.docx`; tandai bagian perlu disetujui.
- 13:00–17:00 — Susun daftar terbuka (pertanyaan: judul, *gap*, batasan, gaya sitasi IEEE).

**Daily Log (planned):**
- (isi saat dilaksanakan — lihat `docs/planning/week-1-roadmap.md` W1 Selasa)

---

## 2026-10-07 (Rabu)
**Short-term Goal:**
M0: Verifikasi *gap* G1–G4 dari *full-text* Pokhrel 2024 & Winslow 2026.

**Daily Plan:**
- 08:00–12:00 — Baca *full-text* Pokhrel 2024 (SIGCOMM ZTA workshop) & Winslow 2026 (ZTNA micro-seg logs); cek apakah benar-benar tidak ada perbandingan A/B/C + overhead.
- 13:00–17:00 — Catat verifikasi *gap* (evidence-linked ke paper).

**Daily Log (planned):**
- (isi saat dilaksanakan — lihat `docs/planning/week-1-roadmap.md` W1 Rabu)

---

## 2026-10-08 (Kamis)
**Short-term Goal:**
M0: Finalisasi Bab I (1.1–1.6).

**Daily Plan:**
- 08:00–12:00 — Tulis 1.1 Latar Belakang, 1.2 Rumusan Masalah (RQ1–RQ4).
- 13:00–17:00 — Tulis 1.3 Tujuan, 1.4 Batasan, 1.5 Manfaat, 1.6 Sistematika.

**Daily Log (planned):**
- (isi saat dilaksanakan — lihat `docs/planning/week-1-roadmap.md` W1 Kamis)

---

## 2026-10-09 (Jumat)
**Short-term Goal:**
M0: Finalisasi Bab I & kunci skenario/metrik (3 skenario A/B/C, RQ1–RQ4, TC-1…TC-5).

**Daily Plan:**
- 08:00–12:00 — *Lock* skenario & metrik; pastikan Bab I final (lokal).
- 13:00–17:00 — Re-check exit criteria W1 (judul & *gap* disetujui, Bab I final, skenario terkunci).

**Daily Log (planned):**
- (isi saat dilaksanakan)

---

## 2026-10-10 (Sabtu)
**Short-term Goal:**
M0: Weekly report M0 & commit repo.

**Daily Plan:**
- 08:00–12:00 — Susun ringkasan progres mingguan (M0).
- 13:00–17:00 — `git add -A && git commit` & (bila diizinkan) `git push`; serahkan weekly report ke pembimbing.

**Daily Log (planned):**
- (isi saat dilaksanakan)

---

## Upcoming weeks (skeleton — follows the cadence in `docs/planning/researchplan.md`)

**M0 / Week 1 (6–10 Okt) — T1+T2 + Initiation** *(ongoing — mirrors `week-1-roadmap.md`)*

**M0 / Week 2 (13–17 Okt) — T2 Literature & gap** → Tinjauan Pustaka (7 sub-bagian + tabel perbandingan metode, Bab II.1)

**M0 / Week 3 (20–24 Okt) — T1/T4 Dasar Teori + Bab III** → NIST 800-207, arsitektur, rancangan purwarupa

**M1 / Week 4 (27–31 Okt) — T4 Testbed design** → `docker-compose` (container `pdp`/`ztp-gateway`/`auth`/`rf-detector`)

**M1 / Week 5 (3–7 Nov) — T4 Skenario A** → TC-1 (tradisional)

**M2 / Week 6 (10–14 Nov) — T4 Skenario B** → TC-2 (ZTA statis)

**M2 / Week 7 (17–21 Nov) — T3 RF training** → TC-3 (RF)

**M2 / Week 8 (24–28 Nov) — T3 RF deploy + dataset** → TC-3a–3d, TC-5

**M2 / Week 9 (1–5 Des) — Integration & debug** → A/B/C jalan

**M2 / Week 10 (8–12 Des) — Finalize testbed** → arsitektur dok

**M3 / Week 11 (15–19 Des) — Experiments start** → TC-1…5

**M3 / Week 12 (22–26 Des) — Experiments (ringan)** → metrik

**M3 / Week 13 (29 Des–2 Jan) — Repeat 3×** → metrik

**M3 / Week 14 (5–9 Jan) — Complete experiments** → dataset final

**M4 / Week 15 (12–16 Jan) — Analysis** → RQ1–RQ4, Bab IV

**M4 / Week 16 (19–23 Jan) — Bab IV–V draft** → hasil

**M4 / Week 17 (26–30 Jan) — Daftar Pustaka** → [16]+

**M4 / Week 18 (2–6 Feb) — Full draft self-review** → Bab I–V

**M5 / Week 19 (9–13 Feb) — Konsultasi #1** → revisi

**M5 / Week 20 (16–20 Feb) — Revisi #2** → revisi

**M5 / Week 21 (23–27 Feb) — Formatting + cek plagiasi** → IEEE

**M5 / Week 22 (2–6 Mar) — Slide + demo** → presentasi

**M5 / Week 23 (9–13 Mar) — Gladi** → polish

**M6 / Week 24 (16–20 Mar) — Pre-sidang buffer** —

**M6 / Week 25 (23–27 Mar) — Sidang prep** —

**M6 / Week 26 (30 Mar–3 Apr) — Sidang / ujian** —

**M6 / Week 27 (6–10 Apr) — Revisi pasca-sidang + serah** —

> **Catatan "4 bulan pokok":** window eksekusi intensif **W4–W18 (Nov 2026–Feb 2027)** = testbed + eksperimen + penulisan inti — harus tuntas sebelum sidang prep (Mar 2027). W1–W3 = persiapan dokumen; W19–W27 = finalisasi & sidang.
