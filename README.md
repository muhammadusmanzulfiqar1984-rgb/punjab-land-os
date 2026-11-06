# Punjab Land OS

**CLRMIS Internal Back-Office Simulation & Zero-Sum Land Share Redistribution Engine**

Built for court production in **WP No. 50498/2026 & Crl. Org. No. 62314/2026** before the Lahore High Court against PLRA (Punjab Land Records Authority).

---

## What This Is

A forensic land-records tool that replicates the visual language and logic of the **PLRA CLRMIS internal data entry system** — the back-office operator interface a Patwari uses when executing a Fard Badar (land mutation/correction).

The tool is designed to demonstrate to the court:

1. **How the internal manipulation interface works** — the CLRMIS operator screen used to enter and modify Fard Badars
2. **The zero-sum proof** — any change to a Khata share must be offset by an equal opposite change elsewhere; the system enforces this mathematically

---

## Case Context

| Field | Detail |
|---|---|
| **Petitioner** | Mian Muhammad Usman s/o Muhammad Zulfiqar — NIC 35202-4251249-9 |
| **Case Ref** | WP No. 50498/2026 · Crl. Org. 62314/2026 (LHC) |
| **Respondent** | Punjab Land Records Authority (PLRA) |
| **Disputed Record** | Fard Badar No. 199 |
| **Mauza** | Chak No. 72/NP, Taj Garh Qanungoi |
| **Tehsil & District** | Rahim Yar Khan, Punjab |
| **Joint Khata** | No. 14 · Khewat ID 1913713 |
| **Khata Total (Fixed)** | 3,180,340 sqft = 11,692.43 Marlas = 584K 12.43M |
| **Petitioner's lawful share** | ~43.00 Marlas |
| **CLRMIS after FB-199** | 33.02 Marlas |
| **Deficit caused by FB-199** | ≈ 9.98 Marlas = 2,715 sqft |

---

## Data

| File | Description |
|---|---|
| `data/khata14_persons.json` | 1,410 NIC-aggregated owner records; total = 3,180,340 sqft (verified) |
| `data/khata14_data.json` | Raw CLRMIS export data |
| `data/Khata14_CategoryA.xlsx` | Category A family members (Petitioner + 3 family members) |

**Category A Persons (Petitioner's Family)**

| Person | NIC | Current (Marlas) |
|---|---|---|
| Muhammad Zulfiqar s/o Abdul Ghafoor | 3130320357489 | 188.62 M |
| Muhammad Farooq s/o Abdul Sattar | 4420361529293 | 65.25 M |
| **Muhammad Usman (Petitioner)** | **35202-4251249-9** | **33.02 M** ⚠ |
| Muhammad Umar Zulfiqar | 3130328374897 | 21.83 M |

---

## The Tool

**`clrmis-khata14-tool.html`** — Single-file, zero-dependency HTML application

Three modules:

### 1. Scenario Calculator
Select any owner → enter a proposed new share → system computes the mandatory zero-sum redistribution across all other owners. Proves that FB-199's reduction of Petitioner's share *must* have increased someone else's share by exactly 2,715 sqft.

### 2. What-If Comparator
Full 1,410-owner table with editable proposed Marla values. Live imbalance counter. Demonstrates the zero-sum constraint interactively.

### 3. Full Redistribution
Complete zero-sum redistribution engine. Lock/unlock individual owners. Export formal CLRMIS-headed record for court annexure.

---

## Zero-Sum Principle (Legal Argument)

The Khata total is physically fixed land. It cannot change. Therefore:

```
Total Sqft (before FB-199) = Total Sqft (after FB-199) = 3,180,340 sqft

Petitioner lost:  43.00M − 33.02M = 9.98M ≈ 2,715 sqft
Therefore:        Some other owner(s) GAINED 2,715 sqft via FB-199
```

This is the mechanistic proof of the manipulation. The tool makes the court compute it themselves.

---

## Technical Notes

- **feet_per_marla = 272** (Rahim Yar Khan district standard)
- **1 Kanal = 20 Marlas**
- Data source: CLRMIS export, Punjab Land Records Authority
- All Urdu names rendered using Noto Nastaliq Urdu (Google Fonts)
- Zero external dependencies — runs fully offline

---

## Legal Document

`docs/LEGAL_CASE_DOCUMENT.md` — Full legal case document (Parts I–VI) for WP 50498/2026.

---

*This repository is produced for court production. All data is sourced from official CLRMIS records. Petitioner: Mian Muhammad Usman, usman@mmusman.com*
