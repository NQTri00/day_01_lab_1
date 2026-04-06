# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Temperature thấp có xu hướng cho câu trả lời với thông tin số liệu khách quan trong khi temperature cao thường bổ sung các thông tin mơ hồ như: 'đủ để chứa cả tòa nhà chọc trời' (1.0), 'ví như một thế giới khác' (1.5), ...

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt ở khoảng 0.3 vì temperature 0.5 vẫn duy trì sự chính xác của thông tin, chưa thêm thắt các chi tiết mơ hồ, mà cũng không khô khan như temperature 0.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o đắt hơn khoảng 16.67 lần so với GPT-4o-mini (chỉ tính phần output).

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Trường hợp nên dùng GPT-4o: Xử lý các nhiệm vụ phức tạp đòi hỏi reasoning sâu hoặc hiểu ngữ cảnh, ví dụ: tư vấn pháp lý, phân tích tài chính phức tạp, viết content marketing, hoặc hỗ trợ kỹ thuật (debug code, thiết kế hệ thống). Trường hợp nên dùng GPT-4o-mini: Các tác vụ thông thường, khối lượng lớn và cần chi phí thấp như chatbot hỗ trợ khách hàng cơ bản, trả lời FAQ, dịch thuật đơn giản, tóm tắt nội dung, hoặc bất kỳ workload có hàng chục nghìn lượt gọi mỗi ngày mà không đòi hỏi câu trả lời chất lượng cao.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng trong các ứng dụng như trợ lý ảo hoặc chatbot, giúp giảm latency vì người dùng có thể đọc ngay từng chữ được tạo ra thay vì phải nhìn màn hình chờ vài giây cho một khối văn bản dài, có thể sẽ tạo cảm giác đỡ mất kiên nhẫn hơn. Ngược lại, non-streaming phù hợp hơn cho các tác vụ xử lý ngầm, khi mà hệ thống tự động hóa chỉ cần nhận được kết quả hoàn chỉnh cuối cùng cho tác vụ tiếp theo mà không có yếu tố con người ngồi chờ để đọc màn hình.

## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
