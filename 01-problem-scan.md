# Lab 02 — Phase 1 & 2: Problem Scan & Quick Assess

## 🔍 Phase 1 — SCAN (Cá nhân)

### 📝 Danh sách bài toán vận hành đề xuất (Vin Smart Future)

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|----------------|------|---------------------|
| 1 | **VinFast** | AI-upgrade | Tự động đề xuất lộ trình sạc tối ưu và trạm sạc trống phù hợp với loại cổng sạc (CCS2/GBT) của từng dòng xe điện (VF5, VF8, VF9). |
| 2 | **Xanh SM** | Tốn thời gian | Tóm tắt lý do khách hàng hủy chuyến từ cuộc gọi ghi âm và ghi chú của tài xế để tìm pattern lỗi hệ thống. |
| 3 | **Vinhomes** | Lặp lại | Phân loại tự động các khiếu nại (ví dụ: mất nước, hỏng đèn, ồn ào) gửi qua App Vinhomes Resident đến đúng ban quản lý từng tòa nhà. |
| 4 | **VinFast** | AI-upgrade | Khách hàng mô tả tình trạng lỗi xe bằng tiếng Việt, hệ thống tự động phân tích và phân loại mã lỗi kỹ thuật ban đầu. |
| 5 | **Vinmec** | Tốn thời gian | Trích xuất thông tin lâm sàng từ bệnh án điện tử, xét nghiệm và ghi chú của bác sĩ để soạn thảo bản tóm tắt xuất viện bằng ngôn ngữ dễ hiểu cho bệnh nhân. |

---

## 🃏 Phase 2 — QUICK-ASSESS (Top 3 Thẻ bài toán)

### QUICK PROBLEM CARD #1
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tự động đề xuất lịch trình sạc tối ưu và  │
│ trạm sạc trống phù hợp với cổng sạc của từng dòng xe điện.  │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế xe điện VinFast (VF5, VF8, VF9) │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xe báo pin yếu dưới 20% ──> 2. Tài xế dừng xe, tự mở   │
│   bản đồ tra cứu thủ công vị trí các trạm sạc xung quanh ──> │
│   3. Tài xế tự lọc xem trạm nào còn trụ trống và hỗ trợ đúng │
│   loại cổng sạc của xe mình ──> 4. Tự di chuyển đến trạm.   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 10 phút/lượt)    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3            │
│ (Tự động nhận diện dòng xe, loại cổng sạc, check API trạm   │
│ trống và tự động draft lộ trình tối ưu đẩy lên màn hình xe) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian tìm kiếm và kiểm tra trạm sạc từ 10 min ──>  │
│ under 1 min; nâng tỷ lệ gợi ý đúng loại cổng sạc lên 100%.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

### QUICK PROBLEM CARD #2
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Phân tích lý do khách hàng hủy chuyến từ  │
│ dữ liệu ghi âm cuộc gọi tổng đài và ghi chú của tài xế.      │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Chuyên viên phân tích dữ liệu vận hành │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Thu thập danh sách ID các cuốc xe bị khách hàng hủy ──>│
│   2. Chuyên viên nghe thủ công file ghi âm cuộc gọi hủy và   │
│   đọc ghi chú tài xế ──> 3. Phân loại lý do hủy chuyến vào  │
│   file Excel ──> 4. Làm biểu đồ báo cáo pattern lỗi hằng tuần.│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ 15 phút/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3            │
│ (Dùng LLM Speech-to-Text trích xuất hội thoại, tự động phân │
│ tích ngữ cảnh và gắn tag lý do hủy chuyến vào hệ thống)     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian phân tích lý do hủy từ 15 min ──> under 30s   │
│ mỗi cuốc xe; xử lý được 100% lượng cuốc hủy trong ngày.     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

### QUICK PROBLEM CARD #3
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân loại và điều hướng phản ánh  │
│ của cư dân trên ứng dụng Vinhomes Resident về đúng ban QL.  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH trung tâm & Cư dân      │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi text/hình ảnh phản ánh lên App Vinhomes ──>  │
│   2. Nhân viên CSKH trung tâm đọc và phân loại bằng tay ──>   │
│   3. Chuyển tiếp (route) thủ công ticket đến ban quản lý của│
│   từng tòa nhà/phòng ban cụ thể ──> 4. Kỹ thuật viên xử lý.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ 12 phút/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3            │
│ (Đọc hiểu nội dung phản ánh bằng NLP, tự động gắn tag loại   │
│ sự cố và route thẳng đến đúng hòm thư ban quản lý tòa nhà)  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian điều hướng phản ánh từ 12 min ──> under 10s; │
│ Tỷ lệ phân loại đúng và điều hướng chính xác đạt trên 95%.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘