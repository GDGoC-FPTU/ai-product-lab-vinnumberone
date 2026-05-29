# 02-deep-dive-report.md

# Deep-Dive Report: AI Demand Prediction & Driver Repositioning for Xanh SM

## 1. Quyết định lựa chọn

### Bài toán được chọn

Xanh SM cần dự đoán nhu cầu đặt xe theo khu vực trong 15–30 phút tới để chủ động điều phối tài xế đến đúng điểm nóng trước khi khách phát sinh nhu cầu.

Lý do lựa chọn:

* Tác động trực tiếp đến trải nghiệm khách hàng.
* Ảnh hưởng lớn đến doanh thu và hiệu suất vận hành.
* Có sẵn nguồn dữ liệu lớn để huấn luyện mô hình AI.
* Có thể triển khai thử nghiệm trên phạm vi nhỏ trước khi mở rộng toàn hệ thống.

---

# 2. Problem Statement (6-field)

| Field                       | Nội dung chi tiết                                                                                                                                                                                                                                                |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Actor / Operator**     | Tài xế Xanh SM, đội vận hành điều phối và khách hàng đặt xe.                                                                                                                                                                                                     |
| **2. Current Workflow**     | Hệ thống ghi nhận vị trí tài xế → Khách đặt xe → Hệ thống ghép tài xế gần nhất → Nếu khu vực thiếu xe thì khách phải chờ hoặc hủy chuyến → Đội vận hành phân tích dữ liệu và điều phối thủ công. Công cụ sử dụng gồm GPS, ứng dụng tài xế và dashboard vận hành. |
| **3. Bottleneck**           | Hệ thống chỉ phát hiện tình trạng thiếu xe sau khi nhu cầu đã phát sinh. Việc điều phối hiện tại mang tính phản ứng và phụ thuộc nhiều vào thao tác thủ công của đội vận hành.                                                                                   |
| **4. Business Impact**      | Thời gian chờ trung bình của khách khoảng 8 phút trong giờ cao điểm. Tỷ lệ hủy chuyến do chờ lâu khoảng 12%. Điều này làm giảm doanh thu, giảm hiệu suất tài xế và ảnh hưởng đến chất lượng dịch vụ.                                                             |
| **5. Success Metric**       | Giảm thời gian chờ trung bình xuống dưới 5 phút; giảm tỷ lệ hủy chuyến xuống dưới 7%; tăng số chuyến/tài xế/giờ cao điểm thêm 10–15%; độ chính xác dự báo nhu cầu đạt trên 85%.                                                                                  |
| **6. Operational Boundary** | AI được phép thu thập dữ liệu, phân tích nhu cầu và đề xuất điều phối tài xế. AI không được tự ý thay đổi giá cước, áp dụng chế tài với tài xế hoặc đưa ra quyết định vận hành quy mô lớn mà không có sự phê duyệt của đội điều phối.                            |

---

# 3. Future-State Flow & AI Fit

## 3.1 AI Fit Classification

### Kết quả đánh giá

* [ ] Rule / State-Machine
* [ ] LLM Feature
* [x] Agentic Loop

### Lý do lựa chọn

Bài toán yêu cầu hệ thống:

1. Liên tục quan sát dữ liệu vận hành.
2. Dự báo nhu cầu trong tương lai.
3. Đưa ra đề xuất điều phối.
4. Theo dõi kết quả sau điều phối.
5. Điều chỉnh hành động dựa trên dữ liệu mới.

Quy trình này phù hợp với mô hình Agentic Loop (Observe → Predict → Decide → Act → Monitor).

---

## 3.2 Future-State Flow

```text
Dữ liệu GPS tài xế
Dữ liệu lịch sử đặt xe
Dữ liệu thời tiết
Dữ liệu sự kiện khu vực
                ↓
[AI Agent thu thập và phân tích dữ liệu]
                ↓
[AI dự báo nhu cầu đặt xe theo khu vực]
                ↓
[AI xác định điểm nóng và đề xuất điều phối]
                ↓
[Đội vận hành phê duyệt đề xuất]
                ↓
         Được duyệt?
          /      \
        Có       Không
         ↓         ↓
[AI gửi đề xuất]  [Fallback]
[cho tài xế]      [Quay về quy trình hiện tại]
         ↓
[Tài xế di chuyển đến khu vực dự báo]
         ↓
[Khách phát sinh nhu cầu]
         ↓
[Ghép chuyến nhanh hơn]
         ↓
[AI theo dõi KPI và học từ dữ liệu mới]
```

---

## 3.3 Human-in-the-Loop (HITL)

Các bước bắt buộc có sự tham gia của con người:

1. Phê duyệt các đề xuất điều phối quy mô lớn.
2. Xử lý các tình huống bất thường như:

   * Mưa lớn.
   * Tai nạn giao thông.
   * Sự kiện tập trung đông người.
3. Giám sát KPI và đánh giá hiệu quả mô hình.

---

## 3.4 Fallback Strategy

Khi AI không đủ độ tin cậy:

* Confidence Score dưới 80%.
* Thiếu dữ liệu GPS hoặc dữ liệu đầu vào bất thường.
* Xuất hiện các tình huống chưa từng có trong dữ liệu huấn luyện.

Hệ thống sẽ:

1. Không thực hiện điều phối tự động.
2. Gửi cảnh báo cho đội vận hành.
3. Quay về quy trình điều phối thủ công hiện tại.
4. Lưu dữ liệu để phục vụ huấn luyện và cải thiện mô hình.

---

# 4. Evaluate

## 4.1 AI Readiness Checklist

| Checklist                                     | Đánh giá | Giải thích                                                                          |
| --------------------------------------------- | -------- | ----------------------------------------------------------------------------------- |
| Có sẵn dữ liệu mẫu/logs sạch để test?         | ✅ Có     | Xanh SM đang sở hữu dữ liệu GPS, lịch sử đặt xe, thời gian chờ và tỷ lệ hủy chuyến. |
| Rủi ro khi AI sai có nằm trong tầm kiểm soát? | ✅ Có     | Có Human-in-the-Loop và cơ chế Fallback về quy trình hiện tại.                      |
| Stakeholders sẵn sàng thay đổi quy trình?     | ✅ Có     | Tài xế, đội vận hành và doanh nghiệp đều hưởng lợi trực tiếp nếu dự án thành công.  |

---

## 4.2 Quyết định cuối cùng

### Kết quả

* [x] GO (Bắt đầu xây dựng Prototype)
* [ ] NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline)
* [ ] NO-GO (Không khả thi / Rule-based tốt hơn)

---

## 4.3 Justification

Nhóm quyết định lựa chọn phương án GO vì bài toán có tính khả thi cao cả về dữ liệu, kỹ thuật và giá trị kinh doanh.

Về dữ liệu, Xanh SM đã sở hữu lượng lớn dữ liệu vận hành thực tế như lịch sử đặt xe, dữ liệu GPS tài xế, tỷ lệ hủy chuyến và thời gian chờ khách. Đây là các nguồn dữ liệu quan trọng để xây dựng hệ thống dự báo nhu cầu.

Về kỹ thuật, bài toán phù hợp với các mô hình Machine Learning và Agentic AI hiện nay. Hệ thống có thể học từ dữ liệu lịch sử để dự báo nhu cầu trong từng khu vực và từng khung giờ với độ chính xác kỳ vọng trên 85%.

Về quản trị rủi ro, AI chỉ đóng vai trò hỗ trợ ra quyết định. Các đề xuất điều phối vẫn được đội vận hành phê duyệt trước khi áp dụng trên diện rộng. Khi hệ thống không đủ tự tin hoặc gặp lỗi, quy trình hiện tại vẫn có thể vận hành bình thường thông qua cơ chế Fallback.

Về chi phí, nhóm ước tính giai đoạn Prototype kéo dài khoảng 4–8 tuần với quy mô thử nghiệm tại một khu vực giới hạn (ví dụ: nội thành Hà Nội hoặc TP.HCM). Chi phí chủ yếu đến từ hạ tầng xử lý dữ liệu, nhân sự AI/Data và tích hợp hệ thống. So với lợi ích kỳ vọng như giảm thời gian chờ khách, giảm tỷ lệ hủy chuyến và tăng hiệu suất khai thác tài xế, chi phí đầu tư ban đầu được đánh giá là hợp lý.

Do đó, nhóm đề xuất triển khai Prototype trên phạm vi hẹp để đo lường hiệu quả thực tế trước khi mở rộng trên toàn hệ thống Xanh SM.
