# 📝 REPLY TEMPLATE — FORMAT TRẢ LỜI CHUẨN

> **Áp dụng cho mọi câu hỏi của user** — Tự động áp dụng khi trả lời

---

## 📋 **QUY TẮC FORMAT**

| Quy tắc | Chi tiết |
|---------|---------|
| **Độ dài** | **≤ 200 từ** (tính cả table, bullet) |
| **Tập trung** | Chỉ trả lời **trọng tâm câu hỏi** |
| **Không làm** | So sánh, hướng dẫn cách làm, markdown how-to |
| **Chỉ làm** | Kết quả: bullet points, tables, **bold headers/keywords** |
| **Ngôn ngữ** | Tiếng Việt, ngắn gọn, súc tích, đủ thông tin |

---

## 📋 **STRUCTURE TRẢ LỜI**

### **1. HEADER (1 dòng)**
**Chủ đề chính** — *Giá trị cốt lõi*

### **2. TABLE CHÍNH (nếu có số liệu)**
| Hạng mục | Giá trị |
|----------|---------|
| **Key 1** | Value 1 |
| **Key 2** | Value 2 |

### **3. BULLET POINTS (nếu cần)**
- **Key:** Value
- **Key:** Value

### **4. FOOTER (1 dòng tóm tắt)**
> **Kết luận:** [Kết luận trọng tâm, có số liệu nếu có]

---

## 📋 **VÍ DỤ ÁP DỤNG**

### **Case: Hỏi giá A500-90**
**Báo giá A500-90 C80 (Pmax 343t, 50km, 14m, profit 10%)**

| Hạng mục | Giá trị (VNĐ/m) |
|----------|-----------------|
| **Ex-Work (FOB C80)** | 573,000 |
| **Logistics 50km (14m)** | 45,500 |
| **DAP** | 618,500 |
| **Sale Price (+10%)** | 61,850 |
| **TỔNG GIÁ BÁN** | **680,350** |

> **Kết luận:** **C80 đủ Pmax 383t > 343t. C90 cao hơn ~7%.**

---

## 📋 **QUY TẮC NGOẠI LỆ**

| Trường hợp | Xử lý |
|------------|-------|
| User hỏi "cách làm" | Chỉ đưa **kết quả cuối**, không hướng dẫn bước |
| User hỏi so sánh | Chỉ nêu **khác biệt trọng tâm** trong 1 table nhỏ |
| Dữ liệu lớn | Chỉ **tóm tắt key metrics** trong table |
| Không có dữ liệu | Nêu **thiếu gì** để tính, không đoán |

---

## ✅ **CHECKLIST TRƯỚC KHI GỬI**

- [ ] ≤ 200 từ
- [ ] Có **bold headers/keywords**
- [ ] Có **table** nếu có số liệu
- [ ] Có **bullet** nếu cần liệt kê
- [ ] **Không** có so sánh không cần thiết
- [ ] **Không** có markdown how-to
- [ ] Có **footer tóm tắt** 1 dòng

---

*File: `reply-template.md` | Folder: `Tencent/wiki-llm/templates` | Version: 1.0*