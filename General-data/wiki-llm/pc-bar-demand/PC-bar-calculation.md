# 📊 **PC BAR — HƯỚNG DẪN TÍNH TOÁN NHU CẦU (Merged Complete Guide)**
## *Định mức · Phân loại · Công thức · Excel Template · Ví dụ thực tế*

> **Gộp từ 2 file:** `PC-bar.md` (Spec/Reference) + `calculation-basic-pcbar.md` (Calculation Guide)  
> **Cập nhật:** 2026-07-24 | **Phiên bản:** 2.0

---

## 🎯 **MỤC ĐÍCH & OUTPUT CHUẨN**

| Input bạn cung cấp | Output hệ thống trả về |
|-------------------|----------------------|
| **Mặc định (không cung cấp gì)** | Nhu cầu PC bar tháng theo **Sản xuất chuẩn** (190 ea/shift, 26 shifts) → **Tấn 7.1mm / 9.0mm / 10.7mm** |
| **Sản lượng dự kiến (ea/shift hoặc ea/tháng)** | Nhu cầu PC bar tương ứng → **Tấn theo loại cáp** |
| **Kế hoạch sản xuất chi tiết (Mix D300/D350/D400/D500/D600 + B/C)** | Nhu cầu PC bar chi tiết → **Tấn theo loại cáp + tổng hợp** |
| **Dự án riêng (Project A: A400 20km, Project B: B500 15km...)** | Cộng dồn vào nhu cầu tháng → **Grand Total** |

---

## 1️⃣ **THAM SỐ NHÀ MÁY (FACTORY PARAMETERS)**

| Tham số | Ký hiệu | Giá trị mặc định | Đơn vị | Có thay đổi được? |
|---------|---------|------------------|--------|-------------------|
| Tốc độ khuôn | `r` | 13 | mould/hour | ✅ |
| Giờ làm chuẩn | `h_std` | 8 | hours/shift | ✅ |
| Giờ tăng ca | `h_ot` | 4 | hours | ✅ (0–4) |
| Hệ số khuôn dài | `f_long` | 1.1 | - | ✅ (1.0–1.2) |
| Ngày làm/tháng | `D` | 26 | days | ✅ (24–28) |
| Số ca/ngày | `S` | 1 | shifts/day | ✅ (1–2) |

### **Sản lượng / Shift (Capacity)**
```
EA_per_shift = (h_std + h_ot) × r × f_long
             = (8 + 4) × 13 × 1.1
             = 171.6 ea/shift  ≈ 172 ea
```
> **Chuẩn 8h (không OT):** 104 ea/shift  
> **Tăng ca 10h:** 143 ea/shift  
> **Tăng ca 12h:** 172 ea/shift

### **Sản lượng / Tháng**
```
Shifts_per_month = D × S
EA_per_month     = EA_per_shift × Shifts_per_month
```

---

## 2️⃣ **PHÂN LOẠI PHC & ĐỊNH MỨC PC BAR (RATE TABLE)**

*Nguồn: Sheet "PC" trong Schedule Master | Cập nhật 2026-07-24*

### **2.1. Nhóm A (Standard)**

| PHC | Đường kính | Dày (mm) | Sợi cáp (N) | Cáp PC | Đinh mức (kg/m) | **Rate (ton/ea)** | **Rate (ton/m)** |
|-----|------------|----------|-------------|--------|-----------------|-------------------|------------------|
| A300-60 | 300 | 60 | 6 | 7.1mm | 1.9 | **0.0247** | 0.0019 |
| A300-65 | 300 | 65 | 6 | 7.1mm | 1.9 | 0.0247 | 0.0019 |
| A300-70 | 300 | 70 | 6 | 7.1mm | 1.9 | 0.0247 | 0.0019 |
| A350-60 | 350 | 60 | 7 | 7.1mm | 2.2 | **0.0286** | 0.0022 |
| A350-65 | 350 | 65 | 7 | 7.1mm | 2.2 | 0.0286 | 0.0022 |
| A350-70 | 350 | 70 | 7 | 7.1mm | 2.2 | 0.0286 | 0.0022 |
| **A400-65** | **400** | **65** | **10** | **7.1mm** | **3.2** | **0.0416** | **0.0032** |
| A400-70 | 400 | 70 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| A400-75 | 400 | 75 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| A400-80 | 400 | 80 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| A400-85 | 400 | 85 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| A400-90 | 400 | 90 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| A500-80 | 500 | 80 | 9 | 9.0mm | 4.5 | **0.0585** | 0.0045 |
| A500-85 | 500 | 85 | 9 | 9.0mm | 4.5 | 0.0585 | 0.0045 |
| A500-90 | 500 | 90 | 9 | 9.0mm | 4.5 | 0.0585 | 0.0045 |
| A500-95 | 500 | 95 | 9 | 9.0mm | 4.5 | 0.0585 | 0.0045 |
| A500-100 | 500 | 100 | 9 | 9.0mm | 4.5 | 0.0585 | 0.0045 |
| A600-90 | 600 | 90 | 12 | 9.0mm | 6.0 | **0.0780** | 0.0060 |
| A600-95 | 600 | 95 | 12 | 9.0mm | 6.0 | 0.0780 | 0.0060 |
| A600-100 | 600 | 100 | 12 | 9.0mm | 6.0 | 0.0780 | 0.0060 |
| A600-105 | 600 | 105 | 12 | 9.0mm | 6.0 | 0.0780 | 0.0060 |
| A600-110 | 600 | 110 | 12 | 9.0mm | 6.0 | 0.0780 | 0.0060 |

### **2.2. Nhóm B (High Load)**

| PHC | D (mm) | Dày | N (sợi) | Cáp PC | ĐM (kg/m) | **Rate (ton/ea)** |
|-----|--------|-----|---------|--------|-----------|-------------------|
| B300-60/65/70 | 300 | 60-70 | 8 | 9.0mm | 4.0 | **0.0520** |
| B350-60/65/70/75 | 350 | 60-75 | 10 | 9.0mm | 5.0 | **0.0650** |
| B400-65/70/75 | 400 | 65-75 | 12 | 9.0mm | 6.0 | **0.0780** |
| B500-90 | 500 | 90 | 18 | 9.0mm | 9.0 | **0.1170** |
| B600-90/95/100/105 | 600 | 90-105 | 18 | 10.7mm | 12.7 | **0.1651** |
| B800-110 | 800 | 110 | 27 | 10.7mm | 12.7 | **0.1651** |

### **2.3. Nhóm C (Extra High Load)**

| PHC | D (mm) | Dày | N (sợi) | Cáp PC | ĐM (kg/m) | **Rate (ton/ea)** |
|-----|--------|-----|---------|--------|-----------|-------------------|
| C300-60/65 | 300 | 60-65 | 10 | 9.0mm | 5.0 | **0.0650** |
| C350-60/65 | 350 | 60-65 | 12 | 9.0mm | 6.0 | **0.0780** |
| C400-65/70 | 400 | 65-70 | 15 | 9.0mm | 7.5 | **0.0975** |
| C500-90/95 | 500 | 90-95 | 18 | 10.7mm | 12.7 | **0.1651** |
| C600-95/105 | 600 | 95-105 | 24 | 10.7mm | 12.7 | **0.1651** |
| C800-110/115/120 | 800 | 110-120 | 27 | 12.6mm | 17.0* | **0.2210** |

> **Lưu ý:** \* C800 dùng cáp 12.6mm (định mức 17.0 kg/m) — xác nhận khi có đơn.

---

## 3️⃣ **CÔNG THỨC TÍNH TOÁN (CALCULATION FORMULAS)**

### **3.1. Các biến cơ bản**

| Biến | Ý nghĩa | Công thức |
|------|---------|-----------|
| `Rate_ton_per_ea` | Khối lượng cáp PC / 1 đoạn (13m) | `ĐM (kg/m) × 13 / 1000` |
| `Rate_ton_per_m` | Khối lượng cáp PC / 1 mét cọc | `ĐM (kg/m) / 1000` |
| `EA_per_shift` | Sản lượng / shift | `(h_std + h_ot) × r × f_long` |
| `Shifts_per_month` | Số shift / tháng | `D × S` |

### **3.2. 5 Cách tính nhu cầu (Use Cases)**

| # | Cách tính | Công thức | Khi nào dùng |
|---|-----------|-----------|--------------|
| **[1] Theo mét dài dự án** | `KL = Rate_ton_per_m × Tổng_mét` | Biết tổng km cọc (báo giá, hợp đồng) |
| **[2] Theo số đoạn sản xuất** | `KL = Rate_ton_per_ea × Số_đoạn` | Biết kế hoạch sản xuất (ea) |
| **[3] Ngược: Từ KL ra số đoạn** | `Số_đoạn = KL × 1000 / (ĐM × 13)` | Kiểm tra: KL đã mua đủ bao nhiêu đoạn |
| **[4] Theo năng suất ngày** | `KL/ngày = h × 13 × Rate_ton_per_ea` | Kiểm soát hàng ngày |
| **[5] Theo năng suất tháng** | `KL/tháng = EA_per_month × Rate_ton_per_ea` | **Lập kế hoạch mua hàng tháng** |

---

## 4️⃣ **WORKFLOW TÍNH NHU CẦU THÁNG (STEP-BY-STEP)**

### **BƯỚC 1: CẬP NHẬT THAM SỐ (Parameters)**
```yaml
# File: params.yaml hoặc Sheet "PARAMETERS"
r: 13              # mould/hour
h_std: 8           # giờ chuẩn
h_ot: 4            # giờ OT
f_long: 1.1        # hệ số khuôn dài
D: 26              # ngày/tháng
S: 1               # ca/ngày
```
→ Tự động ra: `EA_per_shift = 172`, `Shifts_per_month = 26`

### **BƯỚC 2: NHẬP KẾ HOẠCH SẢN XUẤT (Monthly Mix)**
*Sheet: `MONTHLY_MIX` — Điền từng tháng*

| Month | PHC_Type | Diameter | Thickness | PC_Type | EA_per_shift | Ghi chú |
|-------|----------|----------|-----------|---------|--------------|---------|
| 2026-09 | A300 | 300 | 60 | 7.1mm | 30 | |
| 2026-09 | A350 | 350 | 65 | 7.1mm | 60 | |
| 2026-09 | A400 | 400 | 65 | 7.1mm | 60 | |
| 2026-09 | A500 | 500 | 85 | 9.0mm | 40 | |
| 2026-09 | **TOTAL** | | | | **190** | ≤ 172? Cần điều chỉnh |

> **Validation:** `Σ EA_per_shift ≤ EA_per_shift_capacity`  
> Nếu vượt → Tăng `h_ot` hoặc `S` (2 ca/ngày)

### **BƯỚC 3: TỰ ĐỘNG TÍNH (Calculation Engine)**

```python
# Pseudocode
for each row in MONTHLY_MIX:
    rate = RATE_TABLE[PHC_Type]  # ton/ea
    demand_shift = EA_per_shift × rate
    demand_month = demand_shift × Shifts_per_month
    aggregate by PC_Type

# Output: Monthly_Demand_By_PC_Type
```

### **BƯỚC 4: CỘNG DỰ ÁN RIÊNG (Projects)**
*Sheet: `PROJECTS`*

| Project | PHC | Length_m | PC_Type | Rate (ton/m) | EA_Needed | Ton_Needed | Priority |
|---------|-----|----------|---------|--------------|-----------|------------|----------|
| Project A | A400 | 20,000 | 7.1mm | 0.0032 | 1,538 | **64.00** | High |
| Project B | B500 | 15,000 | 9.0mm | 0.0045 | 1,154 | **67.50** | Medium |

### **BƯỚC 5: OUTPUT — NHU CẦU THÁNG (Final Demand)**

| Nguồn | 7.1mm (ton) | 9.0mm (ton) | 10.7mm (ton) | 12.6mm (ton) | Tổng (ton) |
|-------|-------------|-------------|--------------|--------------|------------|
| Sản xuất thường (Mix tháng) | 128.78 | 60.84 | 0.00 | 0.00 | 189.62 |
| Project A (A400 20km) | 64.00 | — | — | — | 64.00 |
| Project B (B500 15km) | — | 67.50 | — | — | 67.50 |
| **GRAND TOTAL** | **192.78** | **128.34** | **0.00** | **0.00** | **321.12** |

---

## 5️⃣ **EXCEL TEMPLATE DESIGN (5 SHEETS)**

### **Sheet 1: PARAMETERS**
| A | B | C |
|---|---|---|
| Mould_per_hour | 13 | |
| Std_hours | 8 | |
| OT_hours | 4 | |
| Long_factor | 1.1 | |
| Days_per_month | 26 | |
| Shifts_per_day | 1 | |
| **EA_per_shift** | `=(B2+B3)*B1*B4` | **171.6** |
| **Shifts_per_month** | `=B5*B6` | **26** |

### **Sheet 2: RATE_TABLE** (Master Data — Read-only)
| Diameter | PHC | Thickness | Strands | PC_Type | Rate_kg_per_m | Rate_ton_per_ea | Rate_ton_per_m |
|----------|-----|-----------|---------|---------|---------------|-----------------|----------------|
| 300 | A300 | 60 | 6 | 7.1mm | 1.9 | 0.0247 | 0.0019 |
| 350 | A350 | 65 | 7 | 7.1mm | 2.2 | 0.0286 | 0.0022 |
| 400 | A400 | 65 | 10 | 7.1mm | 3.2 | 0.0416 | 0.0032 |
| 500 | A500 | 85 | 9 | 9.0mm | 4.5 | 0.0585 | 0.0045 |
| 600 | A600 | 90 | 12 | 9.0mm | 6.0 | 0.0780 | 0.0060 |
| ... B300...C800 | ... | ... | ... | ... | ... | ... | ... |

### **Sheet 3: MONTHLY_MIX** (Input — Điền tháng)
| Month | PHC | Diameter | Thickness | PC_Type | EA_per_shift | Validated |
|-------|-----|----------|-----------|---------|--------------|-----------|
| 2026-09 | A300 | 300 | 60 | 7.1mm | 30 | ✅ |
| 2026-09 | A350 | 350 | 65 | 7.1mm | 60 | ✅ |
| 2026-09 | A400 | 400 | 65 | 7.1mm | 60 | ✅ |
| 2026-09 | A500 | 500 | 85 | 9.0mm | 40 | ✅ |
| **SUM** | | | | | **190** | ⚠️ >172 |

> **Validation:** `SUM(EA_per_shift) ≤ EA_per_shift_capacity`

### **Sheet 4: CALCULATION** (Auto — Không sửa)
| Label | Formula | Result |
|-------|---------|--------|
| PC_71_per_shift | `=SUMPRODUCT(IF(PC_Type="7.1mm", EA_per_shift*Rate_ton_per_ea))` | 4.953 |
| PC_90_per_shift | `=SUMPRODUCT(IF(PC_Type="9.0mm", EA_per_shift*Rate_ton_per_ea))` | 2.340 |
| PC_107_per_shift | `=SUMPRODUCT(IF(PC_Type="10.7mm", EA_per_shift*Rate_ton_per_ea))` | 0.000 |
| **Shifts_per_month** | `=Params!B5*Params!B6` | 26 |
| **7.1mm/Month** | `=PC_71_per_shift*Shifts_per_month` | **128.78** |
| **9.0mm/Month** | `=PC_90_per_shift*Shifts_per_month` | **60.84** |
| **10.7mm/Month** | `=PC_107_per_shift*Shifts_per_month` | 0.00 |

### **Sheet 5: PROJECTS** (Input — Dự án riêng)
| Project | PHC | Length_m | PC_Type | Rate_t_per_m | EA_Needed | Ton_Needed | Status |
|---------|-----|----------|---------|--------------|-----------|------------|--------|
| Project A | A400 | 20000 | 7.1mm | 0.0032 | 1538 | 64.00 | Planned |
| Project B | B500 | 15000 | 9.0mm | 0.0045 | 1154 | 67.50 | Pending |

### **Sheet 6: FINAL_DEMAND** (Output Dashboard)
| Source | 7.1mm | 9.0mm | 10.7mm | 12.6mm | Total |
|--------|-------|-------|--------|--------|-------|
| Production (Monthly Mix) | 128.78 | 60.84 | 0.00 | 0.00 | 189.62 |
| Project A | 64.00 | 0.00 | 0.00 | 0.00 | 64.00 |
| Project B | 0.00 | 67.50 | 0.00 | 0.00 | 67.50 |
| **GRAND TOTAL** | **192.78** | **128.34** | **0.00** | **0.00** | **321.12** |

---

## 6️⃣ **VÍ DỤ THỰC TẾ (WORKED EXAMPLES)**

### **Ví dụ 1: Tính nhu cầu tháng 9/2026 (Mặc định)**
> **Input:** Không cung cấp gì → Dùng Mix mặc định (190 ea/shift)

| Loại cáp | /shift | × 26 shifts | Tháng |
|----------|--------|-------------|-------|
| **7.1mm** (D300+D350+D400) | 4.953 ton | × 26 | **128.78 ton** |
| **9.0mm** (D500) | 2.340 ton | × 26 | **60.84 ton** |
| **TỔNG** | 7.293 ton | × 26 | **189.62 ton** |

---

### **Ví dụ 2: Bạn cung cấp sản lượng dự kiến**
> **Input:** "Tháng 10 sản xuất: D300=20, D350=50, D400=80, D500=60, D600=30 ea/shift, 2 ca/ngày, 26 ngày"

| Mix Input | EA/shift | PC_Type | Rate | /shift (ton) |
|-----------|----------|---------|------|--------------|
| D300 | 20 | 7.1mm | 0.0247 | 0.494 |
| D350 | 50 | 7.1mm | 0.0286 | 1.430 |
| D400 | 80 | 7.1mm | 0.0416 | 3.328 |
| D500 | 60 | 9.0mm | 0.0585 | 3.510 |
| D600 | 30 | 9.0mm | 0.0780 | 2.340 |
| **TỔNG** | **240** | | | **11.102** |

> **Shifts:** 2 ca/ngày × 26 = 52 shifts  
> **Output:**
> - **7.1mm:** (0.494+1.430+3.328) × 52 = **273.10 ton**
> - **9.0mm:** (3.510+2.340) × 52 = **304.20 ton**

---

### **Ví dụ 3: Dự án riêng (Project Based)**
> **Input:** "Project X: B400 10km, Project Y: C500 5km"

| Project | PHC | Length (m) | PC_Type | Rate (ton/m) | Ton |
|---------|-----|------------|---------|--------------|-----|
| Project X | B400 | 10,000 | 9.0mm | 0.0060 | **60.00** |
| Project Y | C500 | 5,000 | 10.7mm | 0.0127 | **63.50** |

> **Cộng vào sản xuất thường tháng đó**

---

### **Ví dụ 4: Tính ngược (Reverse Calculation)**
> **Câu hỏi:** "Kho còn 200 ton PC 7.1mm → đủ sản xuất A400 bao nhiêu đoạn / km?"

| Loại | Rate (ton/ea) | Rate (ton/m) | Tính |
|------|---------------|--------------|------|
| A400 7.1mm | 0.0416 | 0.0032 | |
| **Số đoạn** | `200 / 0.0416` | | **4,808 đoạn** |
| **Tổng mét** | `4,808 × 13` | `200 / 0.0032` | **62,500 m (62.5 km)** |

---

## 7️⃣ **QUY TRÌNH HÀNG THÁNG (MONTHLY SOP)**

| Tuần | Hoạt động | Người chịu trách nhiệm | Output |
|------|-----------|----------------------|--------|
| Tuần 1 (tháng trước) | Sale gửi kế hoạch đơn hàng → Planner cập nhật `MONTHLY_MIX` | Planner / Sale | Mix tháng |
| Tuần 2 | Supply Chain kiểm tra `FINAL_DEMAND` vs Tồn kho + GIT | Supply Chain | Gap analysis |
| Tuần 3 | Ra PO mua PC Bar (7.1mm / 9.0mm / 10.7mm) | Procurement | PO Number |
| Tuần 4 | Theo dõi giao hàng, cập nhật GIT | Warehouse | Updated Inventory |
| **Ngày 1 tháng mới** | Khóa `MONTHLY_MIX`, tính `FINAL_DEMAND` chính thức | Planner | Locked Demand |

---

## 8️⃣ **VALIDATION RULES (KIỂM TRA TỰ ĐỘNG)**

| Rule | Công thức | Error nếu |
|------|-----------|-----------|
| Capacity check | `Σ EA_per_shift ≤ EA_per_shift_capacity` | Vượt năng suất |
| Mix completeness | Mọi PHC trong Mix phải có trong `RATE_TABLE` | Missing rate |
| Project feasibility | `Project_EA ≤ EA_per_month_capacity` | Vượt capacity |
| Inventory safety | `Tồn + GIT ≥ Demand_month × Safety_factor` | Nguy cơ hết hàng |

---

## 9️⃣ **FILE TRÊN GOOGLE DRIVE**

| File | Đường dẫn | Vai trò |
|------|-----------|---------|
| **PC-bar-merged.md** | `My Drive / Tencent / wiki-llm / PC bar demand forecast / PC-bar-merged.md` | **File này (Complete Guide)** |
| **PC-bar.md** | `My Drive / Tencent / wiki-llm / PC bar demand forecast / PC-bar.md` | Archive (Spec only) |
| **calculation-basic-pcbar.md** | `My Drive / Tencent / wiki-llm / PC bar demand forecast / calculation-basic-pcbar.md` | Archive (Calc only) |
| **Excel Template** | `My Drive / Tencent / wiki-llm / PC bar demand forecast / PC_Bar_Demand_Template.xlsx` | *(Tạo sau)* |

---

## 🔟 **QUICK REFERENCE CARD (DÁN MÁY TÍNH)**

```
┌─────────────────────────────────────────────────────────────┐
│  PC BAR QUICK CALC                                          │
├──────────────┬──────────────┬──────────────┬────────────────┤
│ PHC          │ PC_Type      │ ton/ea       │ ton/m          │
├──────────────┼──────────────┼──────────────┼────────────────┤
│ A300         │ 7.1mm        │ 0.0247       │ 0.0019         │
│ A350         │ 7.1mm        │ 0.0286       │ 0.0022         │
│ A400         │ 7.1mm        │ 0.0416       │ 0.0032         │
│ A500         │ 9.0mm        │ 0.0585       │ 0.0045         │
│ A600         │ 9.0mm        │ 0.0780       │ 0.0060         │
│ B300         │ 9.0mm        │ 0.0520       │ 0.0040         │
│ B400         │ 9.0mm        │ 0.0780       │ 0.0060         │
│ B500         │ 9.0mm        │ 0.1170       │ 0.0090         │
│ B600         │ 10.7mm       │ 0.1651       │ 0.0127         │
│ C400         │ 9.0mm        │ 0.0975       │ 0.0075         │
│ C500         │ 10.7mm       │ 0.1651       │ 0.0127         │
├──────────────┼──────────────┼──────────────┼────────────────┤
│ FORMULAS:    │ KL = Rate × Qty          │                  │
│ Project (m): │ ton = Rate_ton/m × m     │                  │
│ Production:  │ ton = Rate_ton/ea × ea   │                  │
│ Monthly:     │ ton = /shift × D × S     │ (D=26, S=1/2)    │
└─────────────────────────────────────────────────────────────┘
```

---

## 📞 **HỖ TRỢ & CẬP NHẬT**

| Cần gì? | Làm sao |
|---------|---------|
| Tính nhu cầu tháng | Gửi Mix (ea/shift) hoặc Project (km) → Tôi tính trả về ton/loại |
| Thay đổi tham số | Cập nhật `PARAMETERS` → Tự động tính lại |
| Thêm loại PHC mới | Cập nhật `RATE_TABLE` + `MONTHLY_MIX` |
| Tạo Excel file | Yêu cầu → Tôi gen file `.xlsx` với 6 sheet trên |
| Kiểm tra file gốc | Xem `PC-bar.md` (Spec) hoặc `calculation-basic-pcbar.md` (Calc) |

---

*File này gộp hoàn toàn từ `PC-bar.md` (Spec/Reference) + `calculation-basic-pcbar.md` (Calculation Guide).  
Hai file gốc đã lưu archive trong cùng folder Drive.*  

**Cập nhật:** 2026-07-24 | **Version:** 2.0 (Merged) | **Author:** Hermes Agent