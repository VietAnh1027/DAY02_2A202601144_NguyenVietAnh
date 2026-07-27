## Đóng góp của Việt Anh trong nhóm

| Hoạt động | Việt Anh đã làm gì? | Kết quả |
| --- | --- | --- |
| Scan cá nhân | Đưa ra 5 problems (Chấm điểm văn bản, Chatbot CSKH, Chốt lịch họp, Lọc CV, OCR hóa đơn) | Nhóm có danh sách candidate rất phong phú, mạnh về mảng tự động hóa và trích xuất dữ liệu |
| Pitch | Pitch đề tài "OCR trích xuất Hóa đơn" và "Lọc CV" | Đề tài OCR Hóa đơn được vào top 3 shortlist với điểm số cao (30 điểm) |
| Challenge | So sánh phương pháp Keyword match cũ với LLM Clustering cho bài toán Feedback/Review của nhóm | Giúp nhóm chốt hướng dùng LLM & Vector thay vì dùng rule-based dễ lọt lỗi |
| Workflow | Hỗ trợ vẽ current/future workflow cho bài toán được chọn (Phân tích Feedback/Review) | Làm nổi bật được bottleneck ở bước "Đọc & Gán tag thủ công" của PO/BA |
| Research | Tìm hiểu các tool xử lý Feedback có sẵn (Appbot, Zendesk, MonkeyLearn) | Nhóm nhận ra điểm yếu của các tool cũ với tiếng Việt và chốt không cần build lại hệ thống từ đầu |
| Rule / Workflow / Agent | Lập luận chọn nền tảng là Workflow, kết hợp Agent chỉ ở bước Trigger cảnh báo lỗi khẩn cấp | Nhóm thống nhất decision chốt scope vừa phải, tránh rủi ro báo động giả (Alert fatigue) |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
| --- | --- | --- | --- | --- |
| Scan | Gợi ý thêm các bước thủ công trong bài toán OCR và Lọc CV | Liệt kê chi tiết pain point của người làm nhân sự/kế toán | Gợi ý các success metric chung chung | Sửa thành metric giảm thời gian cụ thể (VD: 8-10 giờ -> < 2 giờ) |
| Workflow | Nhờ AI chuyển mô tả luồng xử lý Feedback thành sơ đồ Mermaid | Nhanh hơn khi map các nguồn data (App Store, Fanpage) về chung 1 luồng | AI gộp chung khâu AI gom cụm và AI đánh giá độ nghiêm trọng | Tách lại luồng rõ ràng, thêm nhánh phụ cho Agent cảnh báo realtime |
| Research | Hỏi về các công cụ Text Analysis và NLP | Cung cấp keyword tốt như Text Clustering, Vector Embedding | Đề xuất hướng đi tự train model riêng khá nặng nề | Chuyển sang hướng dùng Prompt LLM có sẵn cho tinh gọn |
| Problem Statement | Nhờ AI phản biện boundary (ranh giới) của hệ thống | Chỉ ra rủi ro AI tự đánh giá lỗi sai sẽ làm phiền team Dev | Đề xuất hệ thống tự động hóa hoàn toàn (Full Agent) | Ép lại vào Workflow có Human-in-the-loop (PO bắt buộc phải review) |

## Bài học của Việt Anh

* Problem tốt nhất để nhóm chọn không nhất thiết là problem của cá nhân mình đưa ra (nhóm đã chọn bài Feedback thay vì OCR Hóa đơn), mà là problem có pain point hiển hiện rõ nhất và tạo ra impact cốt lõi (cứu tỷ lệ gỡ app).
* Vẽ workflow giúp thấy rõ ranh giới của AI: Ở bài Feedback, AI làm rất tốt phần "chân tay" là đọc và gom cụm từ lóng, nhưng việc quyết định ưu tiên sửa lỗi nào vẫn phải là "điểm kiểm soát" của PO.
* Agent không phải đích đến mặc định để giải quyết mọi thứ. Trong case này, Workflow là trục chính, Agent chỉ đóng vai trò như một màng lọc trigger (báo động Slack) cho các lỗi thực sự nhạy cảm (crash, thanh toán).
* Research các tool cũ giúp định hình được điểm yếu của giải pháp Non-AI (như keyword filter không bắt được từ lóng mỉa mai), từ đó làm bật lên giá trị cốt lõi của LLM.

Nếu làm lại:

```text
Tôi sẽ extract thử một tập data gồm 200-500 reviews thực tế trên App Store/Google Play sớm hơn để test khả năng hiểu "từ lóng tiếng Việt" của LLM bằng Prompt, thay vì chỉ giả định trên giấy rằng AI sẽ gom cụm chính xác 100%.

```