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
> *Câu trả lời của bạn*
   Khi temperature tăng từ 0.0 lên 1.5, phản hồi có xu hướng trở nên đa dạng, sáng tạo và ít lặp lại hơn. Ở temperature thấp, câu trả lời thường ổn định, an toàn và dễ dự đoán; ở temperature cao, mô hình có thể đưa ra cách diễn đạt thú vị hơn nhưng cũng dễ thiếu nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Câu trả lời của bạn*
Tôi sẽ đặt temperature khoảng 0.2–0.5 cho chatbot hỗ trợ khách hàng, vì mục tiêu chính là trả lời chính xác, ổn định và nhất quán. Không nên đặt quá cao vì chatbot chăm sóc khách hàng cần hạn chế phản hồi sáng tạo quá mức hoặc sai lệch thông tin.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
  GPT-4o đắt hơn GPT-4o-mini khoảng 33 lần cho workload này. Vì cả giá input và output của GPT-4o đều cao hơn GPT-4o-mini khoảng 33.33 lần, nên tổng chi phí cũng có thể ước tính cao hơn khoảng 33 lần.


**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
GPT-4o xứng đáng khi cần xử lý các tác vụ phức tạp, yêu cầu độ chính xác và lập luận cao, ví dụ tư vấn chuyên sâu, phân tích tài liệu dài, hỗ trợ ra quyết định hoặc xử lý yêu cầu quan trọng của khách hàng. GPT-4o-mini phù hợp hơn cho các tác vụ đơn giản, khối lượng lớn và cần tiết kiệm chi phí, ví dụ chatbot FAQ, phân loại tin nhắn, trả lời câu hỏi cơ bản hoặc tạo phản hồi ngắn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang trả lời ngay lập tức, ví dụ chatbot hội thoại, trợ lý viết nội dung, giải thích bài học hoặc trả lời từng bước. Streaming giúp giảm cảm giác chờ đợi vì người dùng thấy câu trả lời xuất hiện dần trên màn hình. Ngược lại, non-streaming phù hợp hơn khi cần nhận toàn bộ kết quả một lần để xử lý tiếp bằng code, ví dụ phân loại dữ liệu, trả về JSON, chấm điểm, tính toán tự động hoặc các tác vụ backend không cần hiển thị từng phần cho người dùng.


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
