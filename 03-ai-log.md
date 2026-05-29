Trong bài học Lab này, em đã sử dụng AI (Mô hình ngôn ngữ lớn) làm cộng sự tư duy để thực hiện quá trình scoping bài toán công nghệ cho Vin Smart Future.

### AI đã giúp ích gì?
- **Brainstorm ý tưởng nghiệp vụ:** AI hỗ trợ đắc lực trong việc quét nhanh các pain point thực tế tại các công ty thành viên Vingroup từ 4 thấu kính (Lenses), đặc biệt là đề xuất chi tiết các bước trong quy trình thủ công hiện tại.
- **Chuẩn hóa cấu trúc an toàn:** Hỗ trợ sinh nhanh khung code mẫu Python tích hợp Pydantic (`Structured Output`) để ép mô hình trả về định dạng JSON nghiêm ngặt theo đúng thiết kế ban đầu.

### AI đã sai sót hoặc thiếu sót điểm gì?
- ban đầu khi được yêu cầu giải quyết bài toán phân loại phản ánh của cư dân, AI có xu hướng thiết kế một hệ thống Agent tự trị (Autonomous Agent) phức tạp để tự động gửi mail phản hồi và tự động đóng ticket. 
- Giải pháp này vi phạm nghiêm trọng ranh giới an toàn vận hành, dễ dẫn đến rủi ro phản hồi sai lệch gây khiếu nại pháp lý hoặc tranh chấp tài chính của cư dân Vinhomes.

### em đã điều chỉnh và sửa đổi như thế nào?
- em đã kéo AI về mặt đất bằng cách ép buộc hạ cấp kiến trúc từ "Autonomous Agent" xuống "LLM Feature".
- em trực tiếp tái cấu trúc bộ luật cho System Prompt, bổ sung flag bắt buộc `DRAFT_ONLY` và thiết lập vùng cấm xử lý `LEGAL_FINANCE` để kích hoạt cơ chế `REJECT_TO_HUMAN` (Trả về cho con người xử lý). Điều này đảm bảo AI luôn đóng vai trò trợ lý đề xuất, giữ con người làm trung tâm kiểm duyệt (Human-in-the-loop).