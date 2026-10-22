# M1-07 — Quy tắc nghiệp vụ và câu hỏi cần xác nhận

**Phiên bản:** v0.1 — 2026-10-21
**Người phê duyệt:** Nhóm trưởng
**Người sử dụng:** Thành viên 2 (Use Case), 3 (Thiết kế), 4 (Kiểm thử)

> Nguồn duy nhất đã đọc là bản phân công công việc; đề bài chính thức và mã nguồn chưa được đối chiếu. Vì vậy **không có quy tắc nào ở trạng thái Confirmed**. Mỗi quy tắc dưới đây có *phương án đề xuất* để nhóm trưởng duyệt nhanh; khi được duyệt, đổi trạng thái và ghi người/ngày duyệt.

Trạng thái: `Open` (chờ quyết định) · `Confirmed` (đã chốt) · `Rejected` (bị loại).

## 1. Bảng quy tắc nghiệp vụ

| ID | Chủ đề | Phương án đề xuất | Ảnh hưởng | Câu hỏi | Trạng thái |
|---|---|---|---|---|---|
| BR-01 | Định danh xe | Mã xe duy nhất trên **toàn hệ thống** (không chỉ trong từng bãi), vì xe có thể được trả/điều chuyển sang bãi khác. | FR-17, FR-18, thiết kế CSDL | Q-19 | Open |
| BR-02 | Trạng thái xe | Tập trạng thái: *Sẵn sàng*, *Đã đặt* (có yêu cầu thuê chờ bàn giao), *Đang thuê*, *Cần sửa chữa*, *Ngừng sử dụng*. Chuyển hợp lệ: Sẵn sàng → Đã đặt (gửi yêu cầu); Đã đặt → Sẵn sàng (hủy/từ chối); Đã đặt → Đang thuê (bàn giao); Đang thuê → Sẵn sàng / Cần sửa chữa (trả xe); Sẵn sàng ↔ Cần sửa chữa (cập nhật thủ công); bất kỳ trạng thái nào trừ Đang thuê → Ngừng sử dụng. | FR-06, FR-07, FR-10, FR-11, FR-18, NFR-03 | Q-20 | Open |
| BR-03 | Khóa trạng thái khi đang thuê | Xe ở trạng thái *Đang thuê* chỉ được đổi trạng thái thông qua UC Ghi nhận trả xe. | FR-18, NFR-03 | Q-20 | Open |
| BR-04 | Đăng ký | Bắt buộc: họ tên, số điện thoại, mật khẩu; số điện thoại là duy nhất. Email, số giấy tờ tùy thân: chờ quyết định. | FR-01, FR-03 | Q-02 | Open |
| BR-05 | Dữ liệu cá nhân | Không lưu ảnh giấy tờ; nhân viên đối chiếu giấy tờ gốc tại bãi và chỉ ghi nhận "đã kiểm tra" cùng loại giấy tờ. | FR-09, NFR-02 | Q-03 | Open |
| BR-06 | Điều kiện bàn giao | Bàn giao khi: yêu cầu ở trạng thái chờ bàn giao, xe đúng bãi và ở trạng thái *Đã đặt*, khách hàng xuất trình giấy tờ tùy thân hợp lệ, (đặt cọc nếu BR-08 được duyệt). Từ chối nếu thiếu một điều kiện. | FR-09, FR-10 | Q-04 | Open |
| BR-07 | Số yêu cầu và hủy | Mỗi khách hàng có tối đa 1 yêu cầu thuê chờ bàn giao hoặc 1 lượt thuê đang hoạt động; được hủy yêu cầu bất kỳ lúc nào trước khi bàn giao, không mất phí. Yêu cầu không được bàn giao trong một khoảng thời gian X sẽ tự hết hạn (X chờ quyết định). | FR-07, FR-08 | Q-04 | Open |
| BR-08 | Đặt cọc và thanh toán | Thanh toán và đặt cọc bằng tiền mặt/chuyển khoản tại bãi; hệ thống chỉ **ghi nhận** số tiền và hình thức, không tích hợp cổng thanh toán. Hoàn cọc khi trả xe nếu xe không hư hỏng. | FR-09, FR-11, FR-15 | Q-05 | Open |
| BR-09 | Giá thuê | Khách hàng chọn **gói thời lượng** (ví dụ 1 giờ, 2 giờ, nửa ngày, 1 ngày) với giá cố định; biểu phí được quản trị viên cấu hình. | FR-07, FR-12, NFR-09 | Q-06 | Open |
| BR-10 | Trả muộn | Thời gian trễ = thời điểm trả − (thời điểm giao + thời lượng gói), làm tròn lên theo block (ví dụ 15 phút); phụ thu theo đơn giá mỗi block. Có thể có khoảng ân hạn. | FR-13 | Q-07 | Open |
| BR-11 | Ưu đãi cư dân | Chỉ áp dụng khi hồ sơ cư dân ở trạng thái *Đã xác minh* tại thời điểm tính phí; giảm theo tỷ lệ % trên phí thuê (có giảm phụ thu hay không: chờ quyết định). Người xác minh: quản trị viên. | FR-14, FR-24 | Q-08 | Open |
| BR-12 | Trả khác bãi | Cho phép trả xe tại **bất kỳ bãi đang hoạt động** nào; nhân viên của bãi nhận trả là người ghi nhận; vị trí xe cập nhật thành bãi nhận trả. | FR-11, FR-18 | Q-09 | Open |
| BR-13 | Vị trí người dùng | Dùng vị trí từ trình duyệt (khi người dùng cho phép); nếu không có, người dùng chọn khu vực thủ công hoặc xem danh sách bãi không sắp xếp theo khoảng cách. | FR-05 | Q-10 | Open |
| BR-14 | Phân quyền nhân viên | Nhân viên chỉ thao tác (bàn giao, cập nhật xe) trên bãi được phân công; được xem dữ liệu xe của toàn hệ thống. Ngoại lệ: nhận trả xe từ bãi khác theo BR-12. | FR-09, FR-17, FR-18, FR-20, NFR-01 | Q-11 | Open |
| BR-15 | Thống kê | Kỳ: ngày, tuần, tháng. Bộ lọc: bãi, khoảng thời gian. Chỉ số: số lượt thuê, doanh thu, số xe theo trạng thái, tỷ lệ trả muộn. | FR-21 | Q-18 | Open |
| BR-16 | Ngừng hoạt động bãi | Không xóa vật lý bãi đã có dữ liệu lượt thuê; chỉ chuyển sang *Ngừng hoạt động*. Không cho ngừng hoạt động khi bãi còn xe *Sẵn sàng/Đã đặt*. | FR-19 | Q-17 | Open |
| BR-17 | Hư hỏng xe khi trả | Nhân viên ghi nhận tình trạng; nếu hư hỏng, xe chuyển *Cần sửa chữa*. Việc thu phí bồi thường: chờ quyết định. | FR-11 | Q-15 | Open |

## 2. Danh sách câu hỏi chờ nhóm trưởng quyết định

| ID | Câu hỏi | Phương án đề xuất | Ảnh hưởng tới | Trạng thái | Người/ngày quyết định |
|---|---|---|---|---|---|
| Q-01 | Cư dân là actor riêng hay là loại hồ sơ của Khách hàng? | Loại hồ sơ của Khách hàng | Biểu đồ UC, đặc tả UC (TV2) | Open | |
| Q-02 | Trường bắt buộc khi đăng ký và quy tắc chống trùng (SĐT, email, số giấy tờ)? | BR-04 | FR-01, FR-03 | Open | |
| Q-03 | Lưu những dữ liệu cá nhân nào (số CCCD, ảnh giấy tờ)? | BR-05 — không lưu ảnh | NFR-02, thiết kế CSDL | Open | |
| Q-04 | Loại giấy tờ phải kiểm tra; điều kiện từ chối bàn giao; số yêu cầu đồng thời; thời hạn hủy/hết hạn yêu cầu; có đặt trước theo khung giờ không? | BR-06, BR-07; không có đặt trước | FR-07 → FR-10 | Open | |
| Q-05 | Có đặt cọc không? Mức cọc? Phương thức thanh toán? Điều kiện và thời điểm hoàn cọc? | BR-08 | FR-09, FR-11, FR-15, phạm vi tích hợp | Open | |
| Q-06 | Giá thuê theo gói cố định hay theo thời gian thực tế? Mức giá? | BR-09 — gói cố định | FR-12 | Open | |
| Q-07 | Cách làm tròn thời gian trễ, đơn giá phụ thu, có ân hạn không? | BR-10 | FR-13, test case biên | Open | |
| Q-08 | Điều kiện xác minh cư dân, ai xác minh, mức giảm, khoản phí nào được giảm? | BR-11 | FR-14, FR-24, UC015 | Open | |
| Q-09 | Có cho trả xe khác bãi không? Bãi nào được nhận? | BR-12 — mọi bãi đang hoạt động | FR-11, BR-14 | Open | |
| Q-10 | Cơ chế xác định vị trí người dùng; xử lý khi không có GPS? | BR-13 | FR-05 | Open | |
| Q-11 | Nhân viên thao tác theo bãi được phân công hay toàn hệ thống? Quản trị viên có làm được mọi việc của nhân viên không? | BR-14 | FR-17, FR-18, FR-20, NFR-01, actor | Open | |
| Q-12 | Triển khai web responsive hay web + mobile? | Web responsive | Chương 1 mục 1.4, NFR-08 | Open | |
| Q-13 | Xuất báo cáo (FR-22) có thuộc phạm vi cuối không? Định dạng file? In phiếu? | Có, xuất Excel/CSV — ưu tiên Thấp | FR-15, FR-22, UC019 | Open | |
| Q-14 | Nhật ký thay đổi (FR-23) có thuộc phạm vi không? | Chỉ giữ lịch sử trạng thái xe (trong FR-18); audit log tổng quát loại khỏi phạm vi | FR-23, UC020 | Open | |
| Q-15 | Có thu phí bồi thường khi xe hư hỏng/mất không? | Chỉ ghi nhận tình trạng, không tính phí | FR-11, FR-15 | Open | |
| Q-16 | Tiêu chí lọc xe (loại xe, xe trẻ em, xe điện…)? Hệ thống có phân loại xe không? | Lọc theo loại xe nếu có phân loại | FR-06 | Open | |
| Q-17 | Có cho xóa bãi xe không? | BR-16 — chỉ ngừng hoạt động | FR-19 | Open | |
| Q-18 | Kỳ thống kê, bộ lọc, chỉ số cần hiển thị? | BR-15 | FR-21 | Open | |
| Q-19 | Mã xe duy nhất toàn hệ thống hay trong từng bãi? | Toàn hệ thống | BR-01 | Open | |
| Q-20 | Danh sách trạng thái xe và các chuyển trạng thái hợp lệ? Có trạng thái "Đã đặt" không? | BR-02, BR-03 | FR-06 → FR-18, sơ đồ trạng thái (TV2/TV3) | Open | |

## 3. Quy tắc kiểm tra nhất quán

- Không có hai quy tắc mâu thuẫn ở trạng thái Confirmed (hiện chưa có quy tắc Confirmed).
- Phụ thuộc cần lưu ý khi duyệt: BR-12 (trả khác bãi) ↔ BR-14 (phân quyền theo bãi); BR-02 (trạng thái *Đã đặt*) ↔ BR-07 (hết hạn yêu cầu); BR-08 (đặt cọc) ↔ BR-06 (điều kiện bàn giao).
- Mỗi thay đổi về tính phí, quyền hạn, trạng thái xe hoặc luồng thuê/trả phải được thông báo cho nhóm trưởng và thành viên 2–4.
