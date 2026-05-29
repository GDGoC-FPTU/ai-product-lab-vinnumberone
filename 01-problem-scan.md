
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinpearl** | Lặp lại | Tiếp nhận và xử lý các yêu cầu lặp lại của khách lưu trú như gọi xe điện, đặt spa, yêu cầu khăn tắm hoặc hỏi thông tin dịch vụ. |
| 2 | **Vinpearl** | Tốn thời gian | Điều phối nhân viên buồng phòng dựa trên tình trạng check-in/check-out và mức độ ưu tiên của từng phòng. (mất 15-20 min/nhân viên/ngày). |
| 3 | **Vinpearl** | Pain từ người khác | Ban quản lý khó phát hiện sớm các nguyên nhân gây đánh giá 1–2 sao do dữ liệu phản hồi khách hàng phân tán trên nhiều nền tảng. |
| 4 | **Vinpearl** | Tốn thời gian | Lập kế hoạch bảo trì định kỳ cho hàng nghìn thiết bị trong khách sạn và resort. |
| 5 | **Vinpearl** | AI-upgrade | Đề xuất dịch vụ phù hợp (spa, nhà hàng, tour, golf) dựa trên lịch sử lưu trú và hành vi của khách hàng. |


---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Khách lưu trú liên tục yêu cầu các dịch vụ như    │
│ gọi xe điện, đặt spa, đặt nhà hàng, xin thêm khăn hoặc      │
│ hỏi thông tin dịch vụ nhưng hiện vẫn cần nhân viên tiếp nhận │
│ và xử lý thủ công.                                          │
│                                                             │
│ Công ty thành viên: [x] Vinpearl                            │
│                                                             │
│ Ai đang đau? Khách hàng (chờ phản hồi), CSKH/Lễ tân         │
│ (xử lý quá nhiều yêu cầu lặp lại)                           │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Khách gọi hotline / chat trên App                      │
│   → 2. Nhân viên tiếp nhận yêu cầu                          │
│   → 3. Xác định bộ phận phụ trách                           │
│   → 4. Chuyển tiếp yêu cầu tới bộ phận liên quan            │
│   → 5. Theo dõi và phản hồi lại khách                       │
│                                                             │
│ Bước nào tốn nhất? Bước 2-4 (⏱ 3-5 phút/yêu cầu)           │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4             │
│ (Hiểu ý định khách → Tạo ticket → Điều phối tự động)        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian phản hồi đầu tiên từ 2 phút → dưới 15 giây  │
│ Tự động xử lý ≥ 60% yêu cầu phổ biến.                       │
│                                                             │
│ Quick Architecture:                                         │
│ [x] AI Agent + LLM + Workflow Orchestration                │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Điều phối nhân viên buồng phòng chưa tối ưu khiến │
│ nhiều phòng chưa sẵn sàng khi khách đến nhận phòng.         │
│                                                             │
│ Công ty thành viên: [x] Vinpearl                            │
│                                                             │
│ Ai đang đau? Khách hàng (phải chờ check-in), Supervisor     │
│ Housekeeping, Nhân viên buồng phòng                         │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Supervisor nhận danh sách check-out                    │
│   → 2. Phân công nhân viên dọn phòng thủ công               │
│   → 3. Nhân viên cập nhật trạng thái qua điện thoại/Zalo    │
│   → 4. Supervisor theo dõi tiến độ từng phòng              │
│   → 5. Báo lễ tân khi phòng sẵn sàng                        │
│                                                             │
│ Bước nào tốn nhất? Bước 2-4 (⏱ 1-2 giờ/ngày)               │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4             │
│ (Tự động phân công → Tối ưu tuyến dọn → Dự báo hoàn thành) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian turnaround mỗi phòng từ 45 phút → 35 phút. │
│ Tăng tỷ lệ phòng sẵn sàng trước giờ check-in lên >95%.     │
│                                                             │
│ Quick Architecture:                                         │
│ [x] Optimization Engine + Prediction Model                 │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Ban quản lý khó phát hiện sớm nguyên nhân khiến   │
│ khách hàng đánh giá 1-2 sao trên Google, Agoda, Booking và │
│ TripAdvisor do phải đọc và tổng hợp thủ công.              │
│                                                             │
│ Công ty thành viên: [x] Vinpearl                            │
│                                                             │
│ Ai đang đau? Marketing, Operations Manager, Giám đốc Resort │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Thu thập review từ nhiều nền tảng                      │
│   → 2. Nhân viên đọc từng phản hồi                          │
│   → 3. Gắn tag nguyên nhân thủ công                         │
│   → 4. Tổng hợp báo cáo Excel                               │
│   → 5. Đề xuất hành động cải thiện                           │
│                                                             │
│ Bước nào tốn nhất? Bước 2-4 (⏱ 3-5 giờ/ngày)               │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4             │
│ (Phân tích sentiment → Gom nhóm vấn đề → Sinh báo cáo)     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian tổng hợp review từ 4 giờ → 15 phút/ngày.    │
│ Phát hiện tự động ≥ 90% nhóm khiếu nại chính.              │
│                                                             │
│ Quick Architecture:                                         │
│ [x] LLM + RAG + Sentiment Analytics                        │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*
