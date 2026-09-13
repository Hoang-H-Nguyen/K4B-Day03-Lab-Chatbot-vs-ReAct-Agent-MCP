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
[
  {
    "step": 1,
    "query": "Chào bạn, bạn có thể giới thiệu quy chế học vụ cơ bản của Đại học VinUni không?",
    "action_type": "FINAL_ANSWER",
    "thought": "Gemini phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Chào bạn! Rất vui được hỗ trợ bạn.\n\nVới tư cách là Trợ lý Tác tử Học vụ của VinUni, tôi xin chia sẻ một số quy chế học vụ cơ bản mà sinh viên cần nắm vững để đảm bảo quá trình học tập thuận lợi:\n\n1.  **Hệ thống tín chỉ:** VinUni áp dụng hệ thống tín chỉ theo tiêu chuẩn quốc tế. Sinh viên cần hoàn thành đủ số tín chỉ quy định cho chương trình đào tạo của mình để đủ điều kiện tốt nghiệp.\n2.  **Đánh giá kết quả học tập:** Kết quả học tập thường được đánh giá qua nhiều thành phần (điểm chuyên cần, bài tập, bài kiểm tra giữa kỳ, dự án, và thi cuối kỳ). Điểm số thường được tính theo thang điểm 4.0 (GPA).\n3.  **Quy định về học vụ:**\n    *   **Cảnh báo học vụ:** Sinh viên có thể bị cảnh báo học vụ nếu điểm trung bình tích lũy (CGPA) rơi xuống dưới mức quy định (thường là dưới 2.0).\n    *   **Đăng ký môn học:** Sinh viên cần chủ động đăng ký môn học đúng thời hạn thông qua hệ thống quản lý học vụ của trường.\n    *   **Chính sách liêm chính học thuật:** VinUni đề cao sự trung thực trong học tập. Mọi hành vi gian lận (đạo văn, quay cóp,...) đều bị xử lý nghiêm khắc theo quy định của nhà trường.\n4.  **Tư vấn học tập:** Mỗi sinh viên đều có một Cố vấn học tập (Academic Advisor). Bạn nên thường xuyên liên hệ với Cố vấn để được định hướng về lộ trình học tập, chọn môn hoặc giải quyết các vấn đề phát sinh.\n\n**Lưu ý:** Các quy định chi tiết có thể thay đổi tùy theo từng năm học và từng ngành đào tạo. Để có thông tin chính xác nhất cho trường hợp cụ thể của bạn (ví dụ: kiểm tra tình trạng học vụ hiện tại hoặc đặt lịch hẹn với Cố vấn), bạn có thể cung cấp **Mã sinh viên**, tôi sẽ giúp bạn tra cứu thông tin hoặc hỗ trợ đặt lịch hẹn.\n\nBạn có muốn tôi tra cứu thông tin cụ thể nào liên quan đến hồ sơ học vụ của bạn không?",
    "latency_ms": 4119.23
  },
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
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
    "latency_ms": 1417.45
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  },
  {
    "step": 1,
    "query": "Đặt schedule appoinment tư vấn cho sinh viên SV2026002 vào chiều 15/10/2026  17 giờ với giáo sư A",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "datetime_str": "17:00 15/10/2026",
      "advisor_name": "giáo sư A",
      "student_id": "SV2026002"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026002-99",
      "student_id": "SV2026002",
      "datetime": "17:00 15/10/2026",
      "advisor": "giáo sư A",
      "message": "Đặt lịch thành công cho sinh viên SV2026002 với giáo sư A vào lúc 17:00 15/10/2026."
    },
    "latency_ms": 1129.91
  },
  {
    "step": 2,
    "query": "Đặt schedule appoinment tư vấn cho sinh viên SV2026002 vào chiều 15/10/2026  17 giờ với giáo sư A",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Đặt lịch thành công cho sinh viên SV2026002 với giáo sư A vào lúc 17:00 15/10/2026.",
    "latency_ms": 10.0
  },
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
    "latency_ms": 1426.56
  },
  {
    "step": 2,
    "query": "Tôi là sinh viên SV2026001 và muốn đặt một buổi tư vấn học vụ với cố vấn học tập của tôi vào ngày 21/09/2026. Hãy kiểm tra cố vấn của tôi trước, sau đó tìm và đặt một khung giờ còn trống trong ngày đó.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  },
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV9999999.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV9999999"
    },
    "observation": {
      "status": "NOT_FOUND",
      "message": "Không tìm thấy dữ liệu sinh viên có mã 'SV9999999'"
    },
    "latency_ms": 926.63
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV9999999.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Không tìm thấy dữ liệu sinh viên có mã 'SV9999999'",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 4 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 4 lượt.
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
