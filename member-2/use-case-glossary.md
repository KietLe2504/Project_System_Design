# Thuật ngữ và trạng thái

| Thuật ngữ | Cách dùng |
|---|---|
| Khách hàng | Người dùng dịch vụ. Cư dân là thuộc tính hồ sơ của khách, theo phương án Q-01 và FR-24. |
| Nhân viên bãi xe | Người xử lý bàn giao, trả xe và vận hành trong phạm vi bãi được phân công theo Q-11. |
| Quản trị viên | Người quản trị tài khoản, xe, bãi và số liệu. Quyền xét cư dân theo Q-08. |
| Yêu cầu thuê | Đề nghị thuê trước bàn giao. Có bãi nhận, xe, lựa chọn thuê và thời hạn giữ nếu áp dụng. |
| Lượt thuê | Bản ghi việc sử dụng xe thực tế từ mốc bàn giao tới khi hoàn tất trả xe. |
| Bãi nhận / bãi trả | Nơi giao xe / nơi tiếp nhận xe trả. Điều kiện trả khác bãi theo Q-09. |
| Phí xe / phí thời gian | Hai cấu phần giá theo ghi chú Q-05 và Q-06. Biểu phí, đơn vị thời gian và cách làm tròn cần chốt. |
| Phí thuê cơ bản | Tổng cấu phần thuê áp dụng theo biểu phí được duyệt. |
| Phụ thu / giảm giá | Các khoản phát sinh / ưu đãi theo quy tắc áp dụng. FR-13 và ghi chú Q-07 còn mâu thuẫn về phụ thu muộn. |
| Đặt cọc | Khoản cần theo dõi riêng. Điều kiện thu/hoàn và ảnh hưởng tới số tiền cuối cùng theo Q-05. |
| Phiếu thuê/trả | Chứng từ FR-15 của lượt đã hoàn tất, có xe, khách, mốc giao/trả, bãi giao/trả và các khoản tiền. |

## Xe đạp

Các chuyển trạng thái dưới đây dựa trên BR-02, BR-03 và ghi chú Q-04, Q-20, còn chờ duyệt.

| Trạng thái | Ý nghĩa | Chuyển trạng thái |
|---|---|---|
| Sẵn sàng | Xe có thể nhận yêu cầu thuê. | Sang **Đã đặt** khi UC007 giữ xe. Sang **Cần sửa chữa** qua UC014 nếu hợp lệ. |
| Đã đặt | Xe đang được giữ cho một yêu cầu chờ bàn giao. | Sang **Đang thuê** khi UC010 bàn giao. Về **Sẵn sàng** khi yêu cầu giữ xe được hủy hoặc hết hạn. Khi từ chối, giải phóng nếu chính sách đóng yêu cầu được duyệt. |
| Đang thuê | Xe gắn với một lượt thuê đang hoạt động. | Sang **Sẵn sàng** hoặc **Cần sửa chữa** qua UC011 khi trả xe. |
| Cần sửa chữa | Xe cần xử lý kỹ thuật và bị loại khỏi kết quả xe sẵn sàng. | Về **Sẵn sàng** qua UC014 nếu đáp ứng điều kiện kỹ thuật. |
| Ngừng sử dụng | Xe không còn phục vụ theo phương án BR-02. | Chuyển vào trạng thái này qua UC014 nếu được duyệt và xe không có lượt thuê hoặc yêu cầu giữ đang hiệu lực. Điều kiện đưa xe trở lại cần chốt tại Q-20. |

## Yêu cầu thuê và lượt thuê

| Đối tượng | Trạng thái | Sự kiện |
|---|---|---|
| Yêu cầu | Chờ bàn giao | UC007 tiếp nhận và giữ xe theo phương án Q-04. |
| Yêu cầu | Đã hủy | UC008 ghi nhận hủy hợp lệ, giải phóng đúng xe đang giữ cho yêu cầu. |
| Yêu cầu | Hết hạn | Điều kiện hết hạn Q-04 xảy ra. Hệ thống giải phóng phần giữ tương ứng. |
| Yêu cầu | Bị từ chối | Nhân viên ghi lý do. Trạng thái này áp dụng nếu Q-04 chốt đóng yêu cầu khi từ chối. |
| Yêu cầu | Đã bàn giao | UC010 hoàn tất bàn giao. Yêu cầu giữ trạng thái này sau khi lượt thuê kết thúc. |
| Lượt thuê | Đang hoạt động | UC010 ghi nhận xe đã được giao. |
| Lượt thuê | Đã hoàn tất | UC011 lưu dữ liệu trả, kết quả phí và phiếu cùng lần hoàn tất. |

Theo NFR-03 và NFR-04, một xe có tối đa một lượt thuê đang hoạt động. Hủy, hết hạn và bàn giao phải kiểm tra lại cùng trạng thái hiện hành để chỉ một kết quả được ghi nhận. Mỗi lần hoàn tất trả xe tạo tối đa một phiếu.

## Hồ sơ cư dân

| Trạng thái | Sự kiện |
|---|---|
| Chờ xét duyệt | UC004 tiếp nhận hồ sơ hợp lệ. |
| Đã xác minh | UC015 lưu quyết định đạt. FR-14 xét ưu đãi theo trạng thái lúc tính phí. |
| Bị từ chối | UC015 lưu kết quả chưa đạt kèm lý do được phép hiển thị. |

Chính sách nộp lại hoặc thay thế hồ sơ đang có hiệu lực phụ thuộc Q-08. Trạng thái cọc hoặc thanh toán cần xác định sau khi nhóm chốt Q-05.
