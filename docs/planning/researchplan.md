# Research Plan — Tugas Akhir ZTA Adaptif (Okt 2026 – Apr 2027)

**Disusun oleh:** Rizky Wildansani (Sani) — NIM 23/522276/SV/23644
**Program:** D4 / Sarjana Terapan — Teknologi Rekayasa Internet (TRI), UGM Sekolah Vokasi
**Pembimbing:** [nama dosen pembimbing]
**Periode:** 2026-10 – 2027-04 (~6 bulan; *core execution* ~4 bulan = Nov 2026–Feb 2027)
**Target:** Laporan final selesai & sidang April 2027
**Repo:** github.com/sanishiho23/Tugas-Akhir

> Gaya terinspirasi `researchplan.md` internship BMW-Lab, diubah ke konteks Tugas Akhir ZTA (bukan O-RAN WG11).

---

## Adopted Research Title
> **Arsitektur Zero Trust Adaptif Berbasis Machine Learning untuk Deteksi Penyalahgunaan Kredensial Sah pada Trafik Terautentikasi**

## Research Theme (the one research)
> Merancang purwarupa ZTA adaptif (ZTA statis + lapisan deteksi Random Forest) dan menguji efikasi serta overhead-nya dibandingkan ZTA statis dan tradisional melalui **tiga skenario terkontrol pada testbed container Docker**, dengan fokus mendeteksi *abuse* kredensial sah pasca-autentikasi.

Per review draf: kontribusi utama = ZTA adaptif + RF (Skenario C); Skenario A & B = baseline pembanding. Publikasi jurnal (federated learning) **ditunda**.

## Four Component Topics (the 4 supporting topics)
| # | Topic | Anchoring Tools | ZTA angle |
| :--- | :--- | :--- | :--- |
| **T1** | Architecture & Technology (ZTA / NIST 800-207, Docker testbed) | NIST SP 800-207, docker-compose | Desain sistem ZTA (PDP/PEP/PA) di container |
| **T2** | Data Integration & AI Analytics (fitur trafik, RF) | flow / Sysmon logs, scikit-learn | Fitur anomali + model RF (lapisan adaptif) |
| **T3** | Evaluate ML Software / Model (Random Forest vs alternatif) | scikit-learn, pandas | Pemilihan & justifikasi RF (lit. Tsiknas/Sandhu/CMC) |
| **T4** | Deployment & Computing (containerization) | Docker, Docker Compose | Di mana tiap kontrol di-terminate (container PDP/PEP/PA/RF) |

## Security Framing — the lens
Setiap T1–T4 dibaca lewat lensa ZTA: *"apakah ZTA adaptif benar-benar mendeteksi abuse kredensial sah di trafik terautentikasi?"* — diukur sebagai **efikasi deteksi** (P/R/F1/AUC) vs **overhead** (latency/RTT/jitter/throughput).

**Executed scope:** ZTA adaptif (ZTA statis + RF) pada testbed Docker, 3 skenario. Federated learning = *deferred* (future work).

### ZTA Threat Model (test lens, dari NIST SP 800-207 "assume breach")
Adversary *already inside* dengan kredensial sah → abuse pasca-autentikasi:
- **Replay token / impossible travel** → TC-3a (terdeteksi via RF)
- **Eskalasi privilege** → TC-3b
- **Eksfiltrasi data** → TC-3c
- **Credential stuffing** → TC-3d

Setiap kasus diharapkan **terdeteksi** (RF flag) → PDP melakukan step-up auth / blokir (closed-loop = "adaptif").

### Topic → security mapping
| Topic | Security question | TA anchor |
| :--- | :--- | :--- |
| **T1** | Arsitektur ZTA apa yang di-terminate di tiap container? | PDP / PEP / PA (NIST 800-207) |
| **T2** | Fitur apa yang membedakan trafik normal vs abuse? | flow/Sysmon features → RF |
| **T3** | Model ML apa paling efektif & efisien? | Random Forest (justifikasi lit.) |
| **T4** | Di mana tiap kontrol di-deploy di testbed? | container `pdp`/`ztp-gateway`/`auth`/`rf-detector` |

## Lab Realities
- **Testbed:** Docker Desktop di PC pribadi/lab (tanpa hardware khusus), reproducible via `docker-compose`.
- **Dataset abuse:** di-generate sendiri (berlabel) — TC-3a…3d.
- **Tools:** OPA/Keycloak (PDP/PA, opsional), nginx/Envoy (mTLS PEP), scikit-learn (RF), tcpdump/iperf (metrik).

## Phase Inventory (endpoints = containers)
1. `client`, `server-app` — entitas sah & sumber daya
2. `attacker` — pegangan kredensial sah, lakukan abuse
3. `ztp-gateway` — PEP (mikrosegmentasi + mTLS)
4. `pdp` — policy engine (PDP)
5. `auth` — continuous auth (PA)
6. `rf-detector` — Skenario C (skor anomali → PDP)
7. `log-collector` (fitur), `monitor` (metrik)

## Topic-per-Week Cadence (Okt 2026 – Apr 2027)
| Week | Dates | Topic | Milestone | RQ / TC |
| :--- | :--- | :--- | :--- | :--- |
| **W1** | 6–10 Okt | T1+T2 + Initiation | M0 | lock scope, Bab I |
| **W2** | 13–17 Okt | T2 Literature & gap | M0 | Tinjauan Pustaka |
| **W3** | 20–24 Okt | T1/T4 Dasar Teori + Bab III | M0 | NIST 800-207, arsitektur |
| **W4** | 27–31 Okt | T4 Testbed design | M1 | docker-compose |
| **W5** | 3–7 Nov | T4 Skenario A | M1 | TC-1 |
| **W6** | 10–14 Nov | T4 Skenario B | M2 | TC-2 |
| **W7** | 17–21 Nov | T3 RF training | M2 | TC-3 |
| **W8** | 24–28 Nov | T3 RF deploy + dataset | M2 | TC-3a–3d, TC-5 |
| **W9** | 1–5 Des | Integration & debug | M2 | A/B/C jalan |
| **W10** | 8–12 Des | Finalize testbed | M2 | arsitektur dok |
| **W11** | 15–19 Des | Experiments start | M3 | TC-1…5 |
| **W12** | 22–26 Des | Experiments (ringan) | M3 | metrik |
| **W13** | 29 Des–2 Jan | Repeat 3× | M3 | metrik |
| **W14** | 5–9 Jan | Complete experiments | M3 | dataset final |
| **W15** | 12–16 Jan | Analysis | M4 | RQ1–RQ4, Bab IV |
| **W16** | 19–23 Jan | Bab IV–V draft | M4 | hasil |
| **W17** | 26–30 Jan | Daftar Pustaka | M4 | [16]+ |
| **W18** | 2–6 Feb | Full draft self-review | M4 | Bab I–V |
| **W19** | 9–13 Feb | Konsultasi #1 | M5 | revisi |
| **W20** | 16–20 Feb | Revisi #2 | M5 | revisi |
| **W21** | 23–27 Feb | Formatting + cek plagiasi | M5 | IEEE |
| **W22** | 2–6 Mar | Slide + demo | M5 | presentasi |
| **W23** | 9–13 Mar | Gladi | M5 | polish |
| **W24** | 16–20 Mar | Pre-sidang buffer | M6 | — |
| **W25** | 23–27 Mar | Sidang prep | M6 | — |
| **W26** | 30 Mar–3 Apr | Sidang / ujian | M6 | — |
| **W27** | 6–10 Apr | Revisi pasca-sidang + serah | M6 | — |

> **Catatan "4 bulan pokok":** window eksekusi intensif **W4–W18 (Nov 2026–Feb 2027)** = testbed + eksperimen + penulisan inti — harus tuntas sebelum sidang prep (Mar 2027). W1–W3 = persiapan dokumen; W19–W27 = finalisasi & sidang.

## TA Scope (laporan)
- **IN:** perbandingan 3 skenario (A tradisional, B ZTA statis, C ZTA adaptif+RF) pada testbed Docker; efikasi deteksi (P/R/F1/AUC) + overhead (latency/RTT/jitter/throughput); closed-loop adaptif.
- **OUT / future:** federated learning ZTA, publikasi jurnal (ditunda).

## Out of Scope
- Federated learning / blockchain ZTA (hanya literatur).
- Deep telecom/RF layer (bukan domain TA).
- Top-tier journal dalam periode TA.

## Deliverables
- Laporan Bab I–V (IEEE / Sarjana Terapan).
- Intisari (ID, ≤250 kata).
- Testbed Docker (docker-compose, skrip RF).
- Slide presentasi 5–7 menit + video demo ~5 menit.
- Repo GitHub (README, planning, docs, literatur, panduan, testbed).

---
**Last updated:** 2026-10-05 · **Status:** W1 in progress · **Framework:** 1 research (ZTA adaptif + RF deteksi abuse kredensial sah) + 4 topics (T1–T4) + Security = lensa ZTA adaptif
