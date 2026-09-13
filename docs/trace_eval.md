# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:**  Nguyễn Huy Hoàng
> **Mã Sinh Viên / Mã Học viên:** 2A202602738  
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni: Tra cứu điểm GPA, lịch thi và đặt lịch tư vấn học vụ với Cố vấn.
---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Một yêu cầu có thể cần nhiều bước: xác định sinh viên → tra GPA → tra các môn/lịch thi → kiểm tra lịch trống của cố vấn → tạo lịch tư vấn. |
| **2. Tool Interaction** | 5 / 5 | Có thể tương tác với nhiều hệ thống/tool: Student Information System để tra GPA, Exam Schedule DB để tra lịch thi, Calendar/Advising System để đặt lịch tư vấn. |
| **3. Dynamic Decision** | 5 / 5 | Kết quả của bước trước có thể quyết định bước tiếp theo. Ví dụ: tìm GPA → xác định môn cần tư vấn → kiểm tra lịch cố vấn phù hợp → kiểm tra slot còn trống → đặt lịch. Nếu slot đầu tiên không còn, Agent phải tìm slot khác. |
| **4. Long Horizon Goal** | 3 / 5 | Có thể theo đuổi một mục tiêu xuyên suốt nhiều bước, ví dụ: “Giúp sinh viên kiểm tra tình hình học tập và đặt được một buổi tư vấn phù hợp.” Tuy nhiên, mức độ long-horizon vẫn không quá dài. |
| **TỔNG ĐIỂM AGENTIC FIT** | **17 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
  {
    "step": 1,
    "query": "Tôi là sinh viên SV2026001 và muốn đặt một buổi tư vấn học vụ với cố vấn học tập của tôi vào ngày 21/09/2026. Hãy kiểm tra cố vấn của tôi trước, sau đó tìm và đặt một khung giờ còn trống trong ngày đó.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "email": "an.nv@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 1096.3
  },
  {
    "step": 2,
    "query": "Tôi là sinh viên SV2026001 và muốn đặt một buổi tư vấn học vụ với cố vấn học tập của tôi vào ngày 21/09/2026. Hãy kiểm tra cố vấn của tôi trước, sau đó tìm và đặt một khung giờ còn trống trong ngày đó.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "datetime_str": "09:00 21/09/2026",
      "advisor_name": "PGS.TS Nguyễn Văn A",
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "09:00 21/09/2026",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 09:00 21/09/2026."
    },
    "latency_ms": 1217.47
  },
  {
    "step": 3,
    "query": "Tôi là sinh viên SV2026001 và muốn đặt một buổi tư vấn học vụ với cố vấn học tập của tôi vào ngày 21/09/2026. Hãy kiểm tra cố vấn của tôi trước, sau đó tìm và đặt một khung giờ còn trống trong ngày đó.",
    "action_type": "FINAL_ANSWER",
    "thought": "Gemini phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Chào bạn, tôi đã hoàn tất việc đặt lịch tư vấn học vụ cho bạn.\n\nDưới đây là thông tin chi tiết về buổi hẹn:\n*   **Mã sinh viên:** SV2026001\n*   **Cố vấn học tập:** PGS.TS Nguyễn Văn A\n*   **Thời gian:** 09:00, ngày 21/09/2026\n*   **Mã đặt lịch:** BK-SV2026001-99\n\nChúc bạn có một buổi tư vấn hiệu quả! Nếu cần hỗ trợ thêm, bạn hãy cho tôi biết nhé.",
    "latency_ms": 1728.52
  }
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 5 lượt.
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
