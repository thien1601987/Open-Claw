# 5S Principles for Low-RAM VM

**Version:** 1.0  
**Date:** 2026-08-07  
**Author:** Hermes Agent

## 📋 Nguyên tắc chính

### 1. Single-task only
- Chỉ chạy 1 task tại một thời điểm
- Không chạy song song nhiều processes nặng

### 2. Complete before next
- Hoàn thành task hiện tại → cleanup → mới chuyển task khác
- Không để dangling processes

### 3. Error handling
- Nếu lỗi → kill process ngay
- Xóa temp files, release memory
- Reset state trước khi thử lại

### 4. Resource awareness
- RAM 2GB = rất hạn chế
- Ưu tiên CLI tools nhẹ (readpst, curl)
- Tránh Python packages nặng khi không cần

### 5. Cleanup discipline
- Xóa temp files sau mỗi task
- Release memory giữa các tasks
- Monitor resource usage

## 💡 Lý do

Máy ảo với RAM 2GB có giới hạn tài nguyên nghiêm ngặt. Việc tuân thủ nguyên tắc 5S giúp:
- Tránh out-of-memory errors
- Đảm bảo task hoàn thành đáng tin cậy
- Tối ưu hiệu suất trên tài nguyên hạn chế
- Dễ dàng debug khi có lỗi

## 🚀 Áp dụng

```bash
# Kiểm tra RAM trước khi chạy task nặng
free -h

# Kill processes không cần thiết
ps aux | grep -E 'python|node' | grep -v grep

# Cleanup temp files
rm -rf /tmp/* 2>/dev/null
```
