# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600426
**Name:** Tran Huu Gia Huy
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Agent correctly identified the highest-priced electronics product from clean, validated data. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Agent returned an extreme outlier. Garbage data contains duplicate IDs, wrong data types, null values, and unrealistic prices that severely mislead the agent. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai khi dung Garbage Data vi du lieu dau vao co nhat luong kem, dan den ket qua bi sai lech nghiem trong. Cu the:

**Duplicate IDs:** Hai record cung ID=1 (Laptop va Banana) lam agent khong phan biet duoc dau la san pham dung, gay nhieu thong tin trung lap.

**Wrong data types:** Record ID=2 co gia la "ten dollars" (string thay vi number). Khi pandas doc CSV, gia tri nay tro thanh NaN hoac bi ep kieu sai, lam sai logic tinh toan va sap xep.

**Extreme Outliers:** Record "Nuclear Reactor" voi gia $999,999 la gia tri bat thuong cuc do. Agent dung logic `idxmax()` de tim product co gia cao nhat, nen outlier nay chiem vi tri "best deal", tra ve ket qua vo ly.

**Null values:** Record co ID=None, gia=0, category=None lam agent co the gap loi khi truy cap cot, hoac bo qua nhung record quan trong.

Tat ca cac van de tren cho thay rang du lieu khong duoc validate va lam sach truoc khi dua vao he thong se khiem AI agent dua ra quyet dinh sai lam. Chat luong du lieu dau vao la yeu to quyet dinh den do chinh xac cua bat ky he thong AI nao.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

(Viet ket luan cua ban o day)

Toi dong y rang "Quality Data > Quality Prompt". Du co viet prompt hay den dau, neu du lieu dau vao bi nhiem, ket qua se bi sai (garbage in, garbage out). Trong khi do, du lieu sach da duoc validate va transform giup agent dua ra cau tra loi chinh xac ngay ca voi prompt don gian. Data observability va ETL pipeline la nen tang can thiet de dam bao AI hoat dong dang tin cay.
