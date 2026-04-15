[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572468&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** email@example.com
**Name:** Tran Huu Gia Huy
**Student ID:** AI20K-2A202600426 (AI20K-202600426)

---

## Mo ta

Bai lab xay dung ETL pipeline xu ly du lieu tu JSON sang CSV, bao gom 4 buoc: Extract (doc JSON), Validate (loai bo record gia <= 0 va category rong), Transform (tinh giam gia 10%, chuan hoa category Title Case, them timestamp), va Load (luu CSV). Pipeline xu ly 5 records tu raw_data.json, giu lai 3 records hop le, loai 2 records khong hop le. Stress test voi agent simulation cho thay du lieu sach giup agent tra loi chinh xac, trong khi du lieu rac dan den ket qua sai lam.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Total records extracted:** 5
- **Valid records kept:** 3 (Laptop, Chair, Monitor)
- **Invalid records dropped:** 2 (Mystery Box: price=-10, Phone: empty category)
- **Output:** processed_data.csv voi 3 records, co cot discounted_price va processed_at
- **Stress test:** Clean data -> Agent tra loi dung (Laptop $1200). Garbage data -> Agent tra loi sai (Nuclear Reactor $999999).
