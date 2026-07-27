## Scan rộng

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Trả lời thủ công các câu hỏi khách hàng giống nhau (giờ mở cửa, đổi trả, cách đặt hàng) | Nhân viên CSKH | Lặp lại hàng chục lần/ngày |
| 2 | Tốn thời gian | Nhắn tin qua lại để chốt giờ họp phù hợp với nhiều người có lịch khác nhau | PM, team member | 15-20 phút/lần chốt lịch |
| 3 | Tốn thời gian | Đọc và lọc thủ công nhiều CV để chọn ứng viên phù hợp cho 1 vị trí | Nhà tuyển dụng, HR | 3-5 phút/CV, khoảng 10 giờ/vị trí |
| 4 | Lặp lại | Nhập tay thông tin từ hóa đơn/chứng từ giấy vào Excel hoặc phần mềm kế toán | Kế toán, nhân viên kho | Lặp lại mỗi ngày, dễ sai số liệu |
| 5 | Tốn thời gian | Giảng viên phải đọc toàn bộ khóa luận/luận văn (40-80 trang), ghi chú lỗi và đối chiếu tiêu chí thang điểm để chấm điểm | Giảng viên chấm | Mỗi bài mất 40-50 phút chấm, vào mùa bảo vệ khóa luận, giảng viên phải chấm hàng chục bài trong vài ngày, thường phải chấm dồn buổi tối/cuối tuần |

## Top 3
| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | 	Nhập liệu hóa đơn/chứng từ vào hệ thống | Workflow rõ ràng, lặp lại hằng ngày, tốn thời gian và dễ sai sót, có metric đo được | Độ chính xác OCR với hóa đơn viết tay, bị mờ hoặc đa định dạng có đủ tin cậy để bỏ qua bước kiểm tra thủ công không |
| 2 | Chấm khóa luận, luận văn | Pain rất thật (giảng viên quá tải mùa bảo vệ), AI có thể hỗ trợ đọc nhanh, tóm tắt, ánh xạ nội dung sang band điểm | AI có "hiểu" đủ sâu để gợi ý điểm đáng tin không, kiểm nghiệm quality khó |
| 3 | Lọc và xếp hạng CV ứng viên | Nhiều người bị ảnh hưởng như HR, quản lý tuyển dụng, impact rộng vì ảnh hưởng trực tiếp đến chất lượng tuyển dụng | Rủi ro thiên vị, dữ liệu CV đa dạng khó chuẩn hóa |

## Problem Card #1 — Nhập liệu hóa đơn/chứng từ vào hệ thống kế toán

**Problem 1 câu:**
Mỗi ngày kế toán mất khoảng 60-90 phút gõ tay số liệu từ hóa đơn giấy/ảnh chụp vào Excel hoặc phần mềm kế toán, trong đó bước đối chiếu và sửa lỗi nhập liệu tốn nhất và dễ gây sai số liệu cuối tháng.

**Actor:**
Kế toán/nhân viên kho chịu trách nhiệm nhập chứng từ hằng ngày và đối soát công nợ cuối tháng.

**Thời điểm / bối cảnh:**
Diễn ra liên tục mỗi ngày làm việc, dồn cao điểm vào cuối tháng khi phải chốt sổ và đối soát.

**Current workflow:**

```text
1. Nhận hóa đơn giấy/ảnh chụp từ bộ phận mua hàng, kho, chi nhánh
2. Sắp xếp, phân loại hóa đơn theo loại chi phí/nhà cung cấp
3. Đọc tay từng dòng thông tin (ngày, số HĐ, mã hàng, số lượng, đơn giá, thuế)
4. Gõ tay vào Excel/phần mềm kế toán
5. Đối chiếu số liệu vừa nhập với hóa đơn gốc
6. Sửa lỗi nhập sai (sai số, sai đơn vị, thiếu dòng)
7. Lưu trữ, đánh dấu hóa đơn đã xử lý
```

**Bottleneck:**
Bước 3 và 5 — đọc tay + đối chiếu chiếm khoảng 40-50 phút/ngày, và là nơi phát sinh lỗi nhiều nhất do mỏi mắt, hóa đơn mờ hoặc định dạng không đồng nhất.

**Impact:**
60-90 phút/ngày/kế toán. Với đội 3-4 kế toán, tổng công sức có thể lên đến 300 phút/ngày. Sai số liệu bị phát hiện muộn có thể làm lệch báo cáo tài chính, gây mất thời gian điều tra và sửa lại cuối tháng.

**Success metric:**
Giảm thời gian nhập liệu xuống dưới 20 phút/ngày/người, giảm tỉ lệ lỗi nhập liệu xuống dưới 1%.

**Non-AI alternative:**
Dùng template Excel có công thức kiểm tra (validate) hoặc thuê thêm nhân sự nhập liệu, nhưng không giải quyết được gốc vấn đề là phải đọc và gõ tay từng dòng.

**AI hypothesis:**
AI (OCR + trích xuất dữ liệu) đọc hóa đơn, tự động điền các trường thông tin vào hệ thống; kế toán chỉ cần kiểm tra và xác nhận trước khi lưu.

**Quick gut:**
Workflow.

### Draft current workflow

```text
CURRENT STATE — 75 phút

[1 Nhận & phân loại hóa đơn: 10']
→ [2 Đọc tay từng dòng: 20']  <-- bottleneck
→ [3 Gõ tay vào hệ thống: 15']
→ [4 Đối chiếu với hóa đơn gốc: 15']  <-- bottleneck
→ [5 Sửa lỗi nhập sai: 10']
→ [6 Lưu trữ, đánh dấu: 5']
```

### Draft future workflow

```text
FUTURE STATE — 18 phút

[1 Chụp/scan hóa đơn: 3']
→ [2 AI OCR trích xuất dữ liệu: 1']
→ [3 AI tự điền vào hệ thống: 1']
→ [4 Kế toán kiểm tra & xác nhận: 10']  <-- human boundary
→ [5 Lưu trữ tự động: 3']

Fallback: AI đọc sai/không rõ → kế toán nhập tay dòng đó.
```

## Problem Card #2 — Chấm khóa luận, luận văn

**Problem 1 câu:**
Mỗi mùa bảo vệ, giảng viên mất khoảng 60-90 phút đọc và chấm một khóa luận/luận văn, trong đó bước đọc toàn văn để đánh giá lập luận và tìm lỗi tốn nhất và dễ dẫn đến chấm không đồng nhất giữa các bài.

**Actor:**
Giảng viên hướng dẫn/phản biện chịu trách nhiệm đọc, nhận xét và cho điểm khóa luận/luận văn của sinh viên.

**Thời điểm / bối cảnh:**
Cao điểm vào mùa bảo vệ khóa luận (cuối kỳ), khi giảng viên phải chấm hàng chục bài trong vài ngày, thường phải làm dồn vào buổi tối/cuối tuần.

**Current workflow:**

```text
1. Nhận file khóa luận/luận văn (40-80 trang) từ sinh viên
2. Đọc toàn văn từ đầu đến cuối
3. Ghi chú lỗi (chính tả, ngữ pháp, cấu trúc, lập luận)
4. Đối chiếu nội dung với rubric chấm điểm
5. Kiểm tra tính trung thực học thuật (đạo văn, trích dẫn)
6. Viết nhận xét tổng hợp
7. Cho điểm theo từng tiêu chí trong rubric
```

**Bottleneck:**
Bước 2 và 3 — đọc toàn văn + ghi chú lỗi chiếm khoảng 45-60 phút/bài, và là nơi dễ phát sinh sự thiếu đồng nhất (bài chấm đầu ngày kỹ hơn bài chấm cuối ngày khi giảng viên đã mệt).

**Impact:**
60-90 phút/bài/giảng viên. Với 20-30 khóa luận/mùa, một giảng viên có thể mất 20-40 giờ chỉ để chấm. Việc chấm không đồng nhất có thể ảnh hưởng đến công bằng điểm số giữa các sinh viên.

**Success metric:**
Giảm thời gian chấm xuống dưới 30 phút/bài, tăng tính đồng nhất giữa các bài (đo bằng độ lệch điểm giữa 2 giảng viên chấm cùng 1 bài).

**Non-AI alternative:**
Dùng rubric chi tiết hơn + chấm theo cặp (2 giảng viên đối chiếu điểm), nhưng vẫn không giảm được thời gian đọc toàn văn.

**AI hypothesis:**
AI đọc khóa luận, tóm tắt nội dung chính, gợi ý điểm theo từng tiêu chí rubric và chỉ ra lỗi cụ thể (lập luận yếu, thiếu trích dẫn, cấu trúc lỏng lẻo); giảng viên review và điều chỉnh điểm cuối cùng.

**Quick gut:**
Workflow.

### Draft current workflow

```text
CURRENT STATE — 80 phút

[1 Nhận file: 2']
→ [2 Đọc toàn văn: 40']  <-- bottleneck
→ [3 Ghi chú lỗi: 15']  <-- bottleneck
→ [4 Đối chiếu rubric: 10']
→ [5 Kiểm tra đạo văn/trích dẫn: 5']
→ [6 Viết nhận xét: 6']
→ [7 Cho điểm: 2']
```

### Draft future workflow

```text
FUTURE STATE — 28 phút

[1 Upload file: 1']
→ [2 AI tóm tắt + trích lỗi theo rubric: 2']
→ [3 AI check trích dẫn/đạo văn: 1']
→ [4 Giảng viên đọc bản tóm tắt + đối chiếu phần nghi vấn: 15']  <-- human boundary
→ [5 Giảng viên viết nhận xét + chốt điểm: 9']

Fallback: AI tóm tắt sai ý/bỏ sót → giảng viên đọc lại phần gốc tương ứng.
```

## Problem Card #3 — Lọc và xếp hạng CV ứng viên

**Problem 1 câu:**
Mỗi đợt tuyển dụng, nhà tuyển dụng mất khoảng 8-10 giờ đọc và lọc 200 CV cho 1 vị trí, trong đó bước đọc chi tiết để so sánh kinh nghiệm/kỹ năng tốn nhất và dễ bỏ sót ứng viên phù hợp.

**Actor:**
Nhà tuyển dụng/HR chịu trách nhiệm sàng lọc CV và chọn ứng viên vào vòng phỏng vấn.

**Thời điểm / bối cảnh:**
Ngay sau khi đóng tin tuyển dụng, khi CV đổ về dồn dập trong vài ngày và cần chọn ra danh sách phỏng vấn gấp để không trễ tiến độ tuyển dụng.

**Current workflow:**

```text
1. Tải toàn bộ CV về từ các kênh (email, LinkedIn, job site)
2. Mở từng CV, đọc thông tin ứng viên
3. Ghi chú kỹ năng, kinh nghiệm, học vấn vào bảng theo dõi
4. So sánh với JD (job description) và tiêu chí tuyển
5. Xếp hạng/gắn nhãn ứng viên (phù hợp, cân nhắc, loại)
6. Chọn danh sách gửi cho quản lý duyệt
7. Lên lịch phỏng vấn cho ứng viên được chọn
```

**Bottleneck:**
Bước 2 và 3 — đọc từng CV và ghi chú tay chiếm khoảng 3-5 phút/CV, nhân với 200 CV thành nhiều giờ liên tục, dễ mất tập trung và đánh giá không nhất quán giữa CV đọc đầu và CV đọc cuối.

**Impact:**
8-10 giờ/vị trí/người tuyển dụng. Với nhiều vị trí tuyển cùng lúc, HR có thể quá tải, dẫn đến chậm phản hồi ứng viên hoặc bỏ sót ứng viên tốt do đọc lướt ở cuối danh sách.

**Success metric:**
Giảm thời gian lọc CV xuống dưới 2 giờ/vị trí, tăng tỉ lệ ứng viên vào vòng phỏng vấn thực sự phù hợp (đo qua tỉ lệ pass vòng phỏng vấn đầu).

**Non-AI alternative:**
Dùng bộ lọc từ khóa (keyword filter) trên ATS hoặc nhờ thêm người hỗ trợ đọc CV, nhưng vẫn tốn nhân lực và dễ lọc sai vì từ khóa cứng không hiểu ngữ cảnh.

**AI hypothesis:**
AI đọc CV, trích xuất kỹ năng/kinh nghiệm, đối chiếu với JD và xếp hạng mức độ phù hợp kèm giải thích lý do; nhà tuyển dụng review danh sách đã xếp hạng thay vì đọc từ đầu.

**Quick gut:**
Workflow.

### Draft current workflow

```text
CURRENT STATE — 480 phút (200 CV)

[1 Tải CV về: 15']
→ [2 Đọc từng CV: 200']  <-- bottleneck
→ [3 Ghi chú vào bảng: 150']  <-- bottleneck
→ [4 So sánh với JD: 60']
→ [5 Xếp hạng/gắn nhãn: 40']
→ [6 Gửi quản lý duyệt: 10']
→ [7 Lên lịch phỏng vấn: 5']
```

### Draft future workflow

```text
FUTURE STATE — 130 phút (200 CV)

[1 Upload toàn bộ CV: 10']
→ [2 AI trích xuất + đối chiếu JD: 5']
→ [3 AI xếp hạng kèm giải thích: 2']
→ [4 HR review top ứng viên (ưu tiên nhóm cao điểm): 90']  <-- human boundary
→ [5 HR gửi quản lý duyệt: 15']
→ [6 Lên lịch phỏng vấn: 8']

Fallback: AI xếp hạng sai/thiên vị nghi ngờ → HR đọc lại CV gốc trước khi loại.
```