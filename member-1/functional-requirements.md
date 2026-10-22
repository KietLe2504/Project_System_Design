# M1-04 — Danh mục yêu cầu chức năng (FR)

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft — chờ nhóm trưởng duyệt
**Bàn giao cho:** Thành viên 2 (ánh xạ sang Use Case)

## Quy ước

- Mức ưu tiên: **Cao** = bắt buộc cho luồng thuê/trả cốt lõi; **Trung bình** = cần cho vận hành đầy đủ; **Thấp** = có thể lược bỏ nếu thiếu thời gian.
- Trạng thái: tất cả FR đang ở **Draft**. FR-22, FR-23 ở **Pending scope** (chưa quyết định đưa vào phạm vi).
- Nguồn "PC" = bản phân công thành viên 1 (`member_1_task_specification.md`), danh mục khởi tạo §M1-04.
- FR-24 là yêu cầu **bổ sung** so với danh mục khởi tạo, để phản ánh nhóm chức năng "Xác minh thông tin cư dân" ở §1.3 bản phân công.

## Danh mục FR

| ID | Tên yêu cầu | Mô tả | Tác nhân liên quan | Mức ưu tiên | Nguồn / ghi chú |
|---|---|---|---|---|---|
| FR-01 | Đăng ký và đăng nhập | Hệ thống phải cho phép khách hàng đăng ký tài khoản mới, đăng nhập và đăng xuất; nhân viên và quản trị viên đăng nhập bằng tài khoản được cấp. | Khách hàng, Nhân viên, Quản trị viên | Cao | PC. Trường bắt buộc khi đăng ký: Q-02 |
| FR-02 | Xem/cập nhật hồ sơ | Hệ thống phải cho phép khách hàng xem và cập nhật thông tin hồ sơ cá nhân trong phạm vi các trường được phép sửa. | Khách hàng | Trung bình | PC. Trường được sửa: Q-02 |
| FR-03 | Kiểm tra thông tin định danh | Hệ thống phải kiểm tra các thông tin định danh bắt buộc (đủ trường, đúng định dạng, không trùng) khi đăng ký và cập nhật hồ sơ, và báo lỗi cụ thể khi không hợp lệ. | Khách hàng | Cao | PC. Quy tắc chống trùng: BR-04 / Q-02 |
| FR-04 | Xem danh sách bãi xe | Hệ thống phải hiển thị danh sách bãi xe kèm tên, địa chỉ/vị trí và số xe đang sẵn sàng tại mỗi bãi. | Khách hàng, Nhân viên, Quản trị viên | Cao | PC |
| FR-05 | Tìm bãi gần người dùng | Hệ thống phải cho phép tìm và sắp xếp các bãi xe theo khoảng cách tới vị trí của người dùng theo cơ chế vị trí đã thống nhất. | Khách hàng | Trung bình | PC. Cơ chế vị trí: Q-10 |
| FR-06 | Xem và lọc xe khả dụng | Hệ thống phải hiển thị các xe ở trạng thái sẵn sàng tại một bãi và cho phép lọc theo các tiêu chí được hỗ trợ. | Khách hàng | Cao | PC. Tiêu chí lọc (loại xe…): Q-16 |
| FR-07 | Gửi yêu cầu thuê | Hệ thống phải cho phép khách hàng đã đăng nhập chọn xe, chọn thời lượng/gói thuê và gửi yêu cầu thuê. | Khách hàng | Cao | PC. Giới hạn số yêu cầu đồng thời: Q-04 |
| FR-08 | Hủy yêu cầu thuê | Hệ thống phải cho phép khách hàng hủy yêu cầu thuê khi yêu cầu chưa được bàn giao xe. | Khách hàng | Trung bình | PC. Điều kiện/thời hạn hủy: Q-04 |
| FR-09 | Kiểm tra điều kiện bàn giao | Hệ thống phải hiển thị cho nhân viên danh sách yêu cầu thuê thuộc bãi được phân công cùng thông tin khách hàng, giấy tờ và các điều kiện bàn giao cần kiểm tra; cho phép nhân viên chấp nhận hoặc từ chối kèm lý do. | Nhân viên | Cao | PC. Loại giấy tờ, đặt cọc: Q-04, Q-05 |
| FR-10 | Ghi nhận bàn giao xe | Hệ thống phải ghi nhận thời điểm giao xe, nhân viên giao, tạo lượt thuê và chuyển trạng thái xe sang "Đang thuê". | Nhân viên | Cao | PC. Liên quan NFR-03, NFR-04 |
| FR-11 | Ghi nhận trả xe | Hệ thống phải cho phép nhân viên tìm lượt thuê đang hoạt động của xe, ghi nhận bãi trả, thời điểm trả và tình trạng xe khi trả. | Nhân viên | Cao | PC. Trả khác bãi: Q-09 |
| FR-12 | Tính phí thuê | Hệ thống phải tính phí thuê dựa trên biểu phí và thời lượng thuê được xác nhận. | Hệ thống (kích hoạt bởi Nhân viên) | Cao | PC. Cách tính giá: Q-06 |
| FR-13 | Tính phụ thu trả muộn | Hệ thống phải tính phụ thu khi thời điểm trả vượt quá thời lượng đã chọn, theo quy tắc đã chốt. | Hệ thống (kích hoạt bởi Nhân viên) | Cao | PC. Làm tròn/mức phụ thu: Q-07 |
| FR-14 | Áp dụng ưu đãi cư dân | Hệ thống phải tự động áp dụng ưu đãi cư dân vào các khoản phí được quy định khi khách hàng có hồ sơ cư dân ở trạng thái đã xác minh tại thời điểm tính phí. | Hệ thống | Trung bình | PC. Mức giảm, khoản được giảm: Q-08 |
| FR-15 | Tạo phiếu thuê/trả | Hệ thống phải tạo và hiển thị phiếu thuê/trả gồm thông tin xe, khách hàng, thời điểm giao/trả, bãi giao/trả, phí thuê, phụ thu, ưu đãi và tổng tiền sau khi lượt thuê hoàn tất. | Nhân viên, Khách hàng | Cao | PC. In/xuất file: Q-13 |
| FR-16 | Lịch sử thuê | Hệ thống phải lưu và cho phép khách hàng tra cứu lịch sử các lượt thuê và phiếu thuê/trả của chính mình. | Khách hàng | Trung bình | PC |
| FR-17 | Tra cứu xe | Hệ thống phải cho phép nhân viên và quản trị viên tra cứu xe theo mã xe, bãi và trạng thái, xem trạng thái và bãi hiện tại. | Nhân viên, Quản trị viên | Cao | PC. Phạm vi bãi của nhân viên: Q-11 |
| FR-18 | Cập nhật trạng thái/vị trí xe | Hệ thống phải cho phép người có quyền cập nhật trạng thái xe (ví dụ cần sửa chữa, sẵn sàng) và bãi hiện tại của xe, chỉ theo các chuyển trạng thái hợp lệ. | Nhân viên, Quản trị viên | Cao | PC. Danh sách trạng thái: BR-02 |
| FR-19 | Quản lý bãi xe | Hệ thống phải cho phép quản trị viên thêm, sửa thông tin và ngừng hoạt động bãi xe. | Quản trị viên | Trung bình | PC. Xóa bãi còn xe: Q-17 |
| FR-20 | Quản lý tài khoản | Hệ thống phải cho phép quản trị viên tạo tài khoản nhân viên, phân công bãi, khóa/mở khóa tài khoản trong phạm vi được phép. | Quản trị viên | Trung bình | PC. Quyền chi tiết: Q-11 |
| FR-21 | Thống kê | Hệ thống phải cung cấp thống kê theo kỳ (ví dụ ngày/tháng) và theo bãi cho các chỉ số được xác nhận. | Quản trị viên | Trung bình | PC. Kỳ, chỉ số: Q-18 |
| FR-22 | Xuất báo cáo | Hệ thống phải cho phép xuất kết quả thống kê ra file. | Quản trị viên | Thấp | **Pending scope** — Q-13 |
| FR-23 | Nhật ký thay đổi | Hệ thống phải lưu nhật ký các thay đổi quan trọng (người thực hiện, thời điểm, nội dung) và cho phép quản trị viên tra cứu. | Quản trị viên | Thấp | **Pending scope** — Q-14. Lịch sử trạng thái xe đã thuộc FR-18 |
| FR-24 | Xác minh hồ sơ cư dân | Hệ thống phải cho phép khách hàng khai báo thông tin cư dân và cho phép người có thẩm quyền xác minh hoặc từ chối hồ sơ cư dân. | Khách hàng, (Nhân viên/Quản trị viên) | Trung bình | **Bổ sung** từ §1.3 PC. Người xác minh: Q-08 |

## Ghi chú cho thành viên 2

- FR-12, FR-13, FR-14 là hành vi của hệ thống bên trong luồng "Ghi nhận trả xe"; đề xuất mô hình hóa bằng `<<include>>` thay vì UC độc lập do actor kích hoạt (xem [use-case-overview.md](use-case-overview.md)).
- FR-01 gộp đăng ký/đăng nhập theo danh mục khởi tạo; có thể tách thành 2 UC.
- Không mô tả luồng chính/ngoại lệ tại đây — thuộc đặc tả UC của thành viên 2.
