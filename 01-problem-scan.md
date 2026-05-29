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
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Repetitive | Đối soát doanh thu chuyến đi + hóa đơn VAT thủ công theo ca; ước tính 3-5 phút/chuyến, sai lệch 0.3-0.7% doanh thu/tháng (~150-350 triệu VNĐ với 50 tỷ doanh thu). |
| 2 | Xanh SM | Time-consuming | Xử lý khiếu nại/hoàn tiền qua ticket thủ công (thu thập log, GPS, phí chờ); 12-20 phút/ticket, backlog 8-12% gây rò rỉ CSAT và chi phí cơ hội ~80-120 triệu VNĐ/tháng. |
| 3 | Xanh SM | AI-upgrade | Kiểm tra tuân thủ quy trình an toàn (đón/trả đúng điểm, tốc độ, nghỉ giữa ca) từ nhiều nguồn dữ liệu rời rạc; ước tính 2-4 giờ/ngày/nhân sự, bỏ sót 5-8% vi phạm gây rủi ro phạt ~100-200 triệu VNĐ/tháng. |
| 4 | Xanh SM | Stakeholder Pain | Lập kế hoạch ca + phân bổ xe theo khu vực dựa trên file Excel thủ công; 1-2 giờ/ngày/điều phối, sai lệch nhu cầu 6-10% làm tăng thời gian chờ trung bình 1-2 phút/chuyến (~200-400 triệu VNĐ/tháng thất thoát doanh thu). |
| 5 | Xanh SM | Time-consuming | Tổng hợp báo cáo sự cố pin/sạc (tiếp nhận, phân loại, chuyển đối tác); 10-15 phút/vụ, trung bình 25-40 vụ/ngày, chi phí nhân công và downtime ~120-180 triệu VNĐ/tháng. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Đối soát doanh thu chuyến đi + hóa đơn VAT │
│ thủ công theo ca để phát hiện sai lệch và treo giao dịch.   │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên kế toán/đối soát doanh thu    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xuất báo cáo trip log theo ca                           │
│   2. Xuất báo cáo billing/thu tiền                           │
│   3. Đối chiếu bằng Excel theo mã chuyến                     │
│   4. Gắn cờ sai lệch và gửi lại điều tra                     │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 3-5 phút/chuyến)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3: tự động so     │
│ khớp, phát hiện lệch, tạo danh sách ngoại lệ                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ "Giảm thời gian đối soát 3-5 phút/chuyến -> dưới 30s"        │
│ "Tỷ lệ sai lệch chưa xử lý trong T+1 < 2%"                   │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Xử lý khiếu nại/hoàn tiền thủ công gây     │
│ backlog và kéo dài thời gian phản hồi khách hàng.           │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH + điều phối khiếu nại    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận ticket/ghi nhận phản hồi khách                     │
│   2. Thu thập log chuyến, GPS, phí chờ                       │
│   3. Phân loại lỗi, đề xuất phương án hoàn tiền              │
│   4. Trình duyệt và phản hồi khách                           │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 12-20 phút/ticket)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3: tổng hợp     │
│ bằng chứng, tóm tắt, gợi ý quyết định theo policy            │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ "Giảm thời gian xử lý 12-20 phút -> dưới 5 phút"             │
│ "Tỷ lệ ticket đóng trong 24h > 90%"                          │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Kiểm tra tuân thủ quy trình an toàn dựa    │
│ trên nhiều nguồn dữ liệu rời rạc đang làm thủ công.         │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Điều phối vận hành + QA an toàn         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Lấy dữ liệu GPS, hành trình, tốc độ theo ca             │
│   2. Kết hợp dữ liệu check-in/out và nghỉ giữa ca            │
│   3. Đối chiếu quy định an toàn và lập danh sách vi phạm     │
│   4. Gửi cảnh báo và yêu cầu giải trình                      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ 2-4 giờ/ngày)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3: hợp nhất     │
│ dữ liệu, phát hiện bất thường, tạo báo cáo vi phạm           │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ "Giảm thời gian kiểm tra 2-4 giờ/ngày -> dưới 30 phút"       │
│ "Tỷ lệ vi phạm phát hiện đúng > 95%"                         │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```