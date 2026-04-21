# Đề xuất cải thiện UX/UI cho FoodApps Dashboard

## 1) Nhận định nhanh từ hiện trạng

Dashboard hiện có nền tảng kỹ thuật tốt (dark theme đồng bộ, nhiều khối thông tin, hệ thống KPI/charts khá đầy đủ), nhưng trải nghiệm vẫn bị "nặng thông tin" do:

- Mật độ card/section cao, khó quét nhanh để ra quyết định trong 10–20 giây đầu.
- Chưa có luồng đọc ưu tiên (What happened → Why → What to do next).
- Nhiều thành phần có style khác nhau nhưng thiếu “design grammar” nhất quán về khoảng cách, trạng thái và ngữ nghĩa màu.
- Thiếu lớp tóm tắt hành động cho người quản lý (Executive summary + CTA rõ ràng).

## 2) Vấn đề UX/UI chính và hướng sửa

## A. Information architecture (quan trọng nhất)

### Vấn đề
- Người dùng phải tự tổng hợp từ nhiều khối (KPI, trend, top stores, risk, action items...) nên cognitive load cao.

### Đề xuất
1. **Thiết kế lại trang theo 3 tầng quyết định**:
   - **Tầng 1: Executive snapshot** (4–6 KPI chủ lực + cảnh báo đỏ + xu hướng tuần).
   - **Tầng 2: Driver analysis** (theo kênh, khu vực, khung giờ, sản phẩm).
   - **Tầng 3: Action center** (danh sách việc + ưu tiên + deadline + owner).
2. **Giảm số card hiển thị mặc định**, dùng “Show more” hoặc tab để mở sâu.
3. **Giữ một narrative nhất quán** ở đầu mỗi section: “Kết luận 1 dòng” + “chi tiết ở dưới”.

## B. Visual hierarchy & readability

### Vấn đề
- Nhiều tiêu đề/caption có kích cỡ nhỏ, tương phản thấp; vùng biểu đồ và text insight đôi lúc cạnh tranh thị giác.

### Đề xuất
1. Chuẩn hóa type scale:
   - H1 (page) 24/700, H2 (section) 18/700, Label 12/600, Body 13–14/400.
2. Nâng tương phản chữ phụ (text-muted) để đạt gần WCAG AA trên nền tối.
3. Mỗi card chỉ nên có **1 điểm nhấn chính** (số lớn hoặc chart chính), các chỉ số phụ đưa xuống secondary row.
4. Tăng khoảng trắng dọc giữa các section lớn để tạo “nhịp thở” khi đọc.

## C. Semantics màu và trạng thái

### Vấn đề
- Một số thành phần dùng màu theo cảm tính; người dùng khó phân biệt mức ưu tiên chỉ bằng glance.

### Đề xuất
1. Chuẩn hóa semantic color tokens:
   - Success = xanh lá, Warning = vàng/cam, Risk = đỏ, Neutral = xám.
2. Không dùng màu đơn lẻ để truyền nghĩa; thêm icon/label (ví dụ: ↑ Tăng tốt, ↓ Giảm rủi ro).
3. Thêm legend nhỏ cố định ở khu vực KPI đầu trang.

## D. Filter UX

### Vấn đề
- Bộ lọc hiện hữu nhưng chưa phản hồi đủ rõ về trạng thái “đang lọc cái gì” và “ảnh hưởng đến dữ liệu nào”.

### Đề xuất
1. Thêm **filter chips** ngay dưới filter bar (ví dụ: “Khu vực: HCM”, “Kênh: GrabFood”).
2. Có nút **Clear all** rõ ràng và xác nhận phạm vi reset.
3. Hiển thị dòng mô tả ngắn: “Đang hiển thị dữ liệu từ dd/mm đến dd/mm cho X cửa hàng”.

## E. Actionability (đi từ insight → hành động)

### Vấn đề
- Có risk alerts và action items nhưng chưa ràng buộc trực tiếp với KPI suy giảm.

### Đề xuất
1. Mỗi risk alert có CTA cụ thể: “Tạo task”, “Giao owner”, “Đặt deadline”.
2. Thêm cột **Impact ước tính** (doanh thu có thể cứu được nếu xử lý).
3. Ưu tiên mặc định theo ma trận: **Mức ảnh hưởng × Mức khẩn cấp**.

## F. Table & exploration

### Vấn đề
- Bảng dữ liệu lớn nhưng cần hỗ trợ scan/so sánh tốt hơn.

### Đề xuất
1. Cố định cột quan trọng (Store, Revenue) khi cuộn ngang.
2. Thêm row state (good/warn/risk) bằng indicator nhẹ ở mép trái.
3. Cho phép “pin store” để theo dõi top 5 cửa hàng quan trọng.

## G. Mobile & responsive

### Vấn đề
- Nhiều grid 3–4 cột dễ vỡ bố cục trên tablet/mobile.

### Đề xuất
1. Mobile-first breakpoints:
   - ≥1280: full analytics layout.
   - 768–1279: 2 cột.
   - <768: 1 cột, ưu tiên KPI + alert + action.
2. Sidebar thu gọn thành bottom nav hoặc drawer.

## 3) Lộ trình triển khai đề xuất

## Giai đoạn 1 (1–2 tuần) — Quick wins
- Chuẩn hóa typography + spacing + màu semantic.
- Bổ sung filter chips + trạng thái bộ lọc.
- Viết lại tiêu đề section theo dạng “Kết luận nhanh”.

## Giai đoạn 2 (2–4 tuần) — Trải nghiệm quyết định
- Tái cấu trúc layout thành 3 tầng (Snapshot → Driver → Action).
- Liên kết risk alert với action item có owner/deadline.
- Tối ưu bảng (sticky columns, highlight risk row).

## Giai đoạn 3 (4–6 tuần) — Nâng cao
- Cá nhân hóa dashboard theo vai trò (Owner/CEO/TA).
- Benchmark theo tuần/tháng và anomaly detection đơn giản.
- A/B test bố cục dashboard và đo time-to-insight.

## 4) KPI để đo hiệu quả cải tiến UX/UI

Đề xuất theo dõi thêm các chỉ số sau sau khi rollout:

- **Time to first insight**: thời gian để user xác định vấn đề chính đầu ngày.
- **Task conversion rate**: % alert được chuyển thành task có owner.
- **Filter success rate**: % phiên lọc thành công (không reset nhiều lần).
- **Executive satisfaction score**: điểm hài lòng nội bộ theo tuần/tháng.

## 5) Gợi ý ưu tiên nếu chỉ làm 3 việc ngay

1. Tái cấu trúc “fold đầu tiên” thành **Executive snapshot + 3 cảnh báo quan trọng nhất**.
2. Thêm **filter chips + clear all + trạng thái dữ liệu đang xem**.
3. Biến risk thành action rõ ràng: owner + deadline + impact.

---

Nếu bạn muốn, mình có thể tiếp tục làm bước kế tiếp: **đưa ra wireframe low-fidelity (desktop + mobile)** và map trực tiếp vào các section hiện tại trong `index.html` để đội dev triển khai nhanh.
