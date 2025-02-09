# 📌 Kiểm thử phi chức năng với JMeter

## 🔹 Mô tả bài tập
Bài kiểm thử đánh giá hiệu suất của web lms bằng công cụ Apache JMeter.  
Các bài kiểm thử bao gồm:
- **Load Testing** (Kiểm thử tải)
- **Stress Testing** (Kiểm thử khả năng chịu tải)
- **Bottleneck Analysis** (Phân tích điểm nghẽn)

---

## 🔹 Cài đặt và sử dụng
### 1️⃣ Cài đặt JMeter
Tải và cài đặt Apache JMeter từ trang chủ:  
🔗 [JMeter Download](https://jmeter.apache.org/)

### 2️⃣ Chạy kiểm thử
- Mở **JMeter** và load file **test-plan.jmx**  
- Chạy thử nghiệm với **Thread Group** như sau:
  - Load Testing: 10 → 50 users
  - Stress Testing: tăng đến 100 users, infinite loop
- Xuất kết quả ra file **summary.csv**

---

## 🔹 Phân tích kết quả kiểm thử
### **1. Thời gian phản hồi trung bình**
- **464ms** (dao động từ **6ms** đến **1439ms**)
- Độ lệch chuẩn: **61.22ms**
- Hiệu suất ổn định, nhưng cần tối ưu response time peak.

### **2. Throughput (Lưu lượng xử lý request/giây)**
- **210.38 request/giây**
- Hệ thống có khả năng xử lý tốt dưới tải trung bình.

### **3. Tỷ lệ lỗi (Error Rate)**
- **0.219%** (1 lỗi trên 500 requests)
- Tỷ lệ lỗi thấp, nhưng vẫn cần kiểm tra nguyên nhân.

### **4. Băng thông sử dụng**
- **Received KB/sec**: **9303.12 KB/s**
- **Sent KB/sec**: **220.53 KB/s**
- Tiêu thụ băng thông cao, có thể gây nghẽn trong hệ thống lớn.

---

## 🔹 Kết luận
✅ **Ưu điểm:**  
✔️ Throughput cao (~210 requests/s)  
✔️ Tỷ lệ lỗi thấp (0.219%)  
✔️ Hiệu suất ổn định  

⚠️ **Vấn đề tiềm ẩn:**  
- Thời gian phản hồi tối đa cao (**1439ms**)  
- Tiêu thụ băng thông lớn (**9MB/s**)  

📌 **Khuyến nghị:**  
- Tối ưu request có thời gian phản hồi chậm nhất.  
- Kiểm tra server log để xác định bottleneck.  
- Thực hiện thêm stress test với số user lớn hơn.  

---

## 📎 Tài liệu đính kèm
- `test-plan.jmx` (Kịch bản kiểm thử JMeter)  
- `summary.csv` (Báo cáo hiệu suất)  
