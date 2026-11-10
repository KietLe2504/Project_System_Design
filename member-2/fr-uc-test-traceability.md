# Ma trận FR → UC → kịch bản kiểm thử

Mã FR từ [danh mục Thành viên 1](../member-1/functional-requirements.md). Mã UC từ [đặc tả](use-case-specifications.md). Các mục “Chờ” cần quyết định hoặc dữ liệu chuẩn trước khi chạy. Đây là kịch bản thiết kế kiểm thử.

| FR | UC | Mã | Nhánh | Thiết lập và thao tác | Kết quả mong đợi |
|---|---|---|---|---|---|
| FR-01, FR-03 | UC001 | TC001-01 | Chính | Dùng SĐT chưa tồn tại và dữ liệu đầy đủ, gửi đăng ký. | Tạo đúng một tài khoản khách. Chờ Q-02–Q-03 để chốt bộ trường. |
| FR-03 | UC001 | TC001-02 | E1/E2 | Lần lượt bỏ trống trường bắt buộc, nhập sai định dạng, dùng định danh đã có. | Báo nội dung cần xử lý, giữ dữ liệu nhập cần thiết, tài khoản cũ giữ nguyên. |
| FR-01 | UC002 | TC002-01 | Chính/A2 | Đăng nhập từng vai trò hợp lệ, đăng xuất rồi truy cập lại chức năng có bảo vệ. | Đúng quyền theo vai trò, phiên hết hiệu lực sau đăng xuất. |
| FR-01 | UC002 | TC002-02 | E1/E2 | Thử sai thông tin xác thực và thử tài khoản đã bị khóa. | Không cấp phiên mới. |
| FR-02, FR-03 | UC003 | TC003-01 | Chính/A1 | Xem hồ sơ của mình, sau đó sửa trường được phép bằng giá trị hợp lệ. | Xem đúng dữ liệu. Cập nhật hợp lệ hiển thị giá trị mới. Chờ Q-02 để chốt trường. |
| FR-02, FR-03 | UC003 | TC003-02 | E1/E2 | Gửi sửa trường bị khóa, định danh trùng và hồ sơ của khách khác. | Thao tác bị từ chối, giữ hồ sơ cũ và không lộ dữ liệu người khác. |
| FR-24 | UC004 | TC004-01 | Chính | Khách đăng nhập, gửi hồ sơ đủ minh chứng. | Có tham chiếu và trạng thái Chờ xét duyệt. Chờ Q-08 về minh chứng. |
| FR-24 | UC004 | TC004-02 | E1/A2 | Thử thiếu minh chứng, sau đó nộp lại theo điều kiện được chốt. | Lần thiếu không thay đổi hồ sơ. Hành vi nộp lại chờ Q-08. |
| FR-04 | UC005 | TC005-01 | Chính/A1 | Tạo bãi có xe Sẵn sàng, Đã đặt và Đang thuê. Mở danh sách bãi. | Có tên, địa chỉ/vị trí, số xe Sẵn sàng chính xác. |
| FR-05 | UC005 | TC005-02 | Chính | Chọn vị trí có hai bãi ở khoảng cách khác nhau. | Bãi gần hơn đứng trước theo tiêu chí được duyệt. Chờ Q-10. |
| FR-05 | UC005 | TC005-03 | A2/A3/E1 | Từ chối GPS, thử vị trí không hợp lệ và phạm vi không có bãi. | Phương án thay thế hoặc thông báo phù hợp, danh sách cơ bản dùng được, bộ lọc rỗng hiển thị rõ. Chờ Q-10. |
| FR-06 | UC006 | TC006-01 | Chính/A1 | Chọn bãi có nhiều trạng thái xe, sau đó chọn bãi không có xe Sẵn sàng. | Chỉ liệt kê xe Sẵn sàng ở đúng bãi. Bãi còn lại trả kết quả rỗng. |
| FR-06, FR-07 | UC006, UC007 | TC007-01 | UC006 E2, UC007 E1 | Hai khách cùng xem một xe, khách thứ nhất đặt trước, khách thứ hai gửi từ kết quả cũ. | Khách thứ hai được báo chọn xe khác. Giữ nguyên phần giữ hợp lệ của khách thứ nhất. |
| FR-07 | UC007 | TC007-02 | Chính | Khách chưa có yêu cầu/lượt đang mở, chọn xe Sẵn sàng và gửi dữ liệu hợp lệ. | Một yêu cầu Chờ bàn giao và xe Đã đặt, chưa tạo lượt thuê. Hạn giữ theo Q-04. |
| FR-07 | UC007 | TC007-03 | E1/E2 | Gửi đồng thời hai yêu cầu trên một xe, rồi thử gửi yêu cầu khi khách còn lượt đang hoạt động. | Tối đa một lần giữ trên xe. Giới hạn yêu cầu của khách theo Q-04. |
| FR-07 | UC007 | TC007-04 | E2/E3 | Thiếu dữ liệu hoặc làm gián đoạn phản hồi lưu, kiểm tra kết quả rồi thử lại. | Giữ dữ liệu nhập cần thiết. Một kết quả hợp lệ hoặc trạng thái trước thao tác, không nhân đôi yêu cầu. |
| FR-07 | UC007 | TC007-05 | A2 | Tạo yêu cầu có giữ xe, kiểm tra ngay trước, đúng và sau mốc 10 phút theo ghi chú Q-04. | Chờ Q-04–Q-05. Khi hết hạn, chỉ phần giữ tương ứng được giải phóng, không phát sinh lượt thuê, cọc xử lý theo chính sách. |
| FR-08 | UC008 | TC008-01 | Chính/A1 | Chủ yêu cầu hủy khi hợp lệ, lặp lại thao tác. | Yêu cầu Đã hủy, đúng phần giữ được giải phóng một lần. Điều kiện hủy chờ Q-04. |
| FR-08 | UC008 | TC008-02 | E1/E2 | Thử hủy yêu cầu người khác, đã hết hạn và đã bàn giao. | Từ chối, dữ liệu và quyền sử dụng xe giữ nguyên. |
| FR-08 | UC008 | TC008-03 | A2 | Hủy trước, đúng và sau mốc 5 phút. Thử có/không có lần thuê trước thành công. | Quyết định cọc độc lập với kết quả hủy. Chờ Q-05 để chốt mốc biên và cách xác nhận trong 3 phút. |
| FR-08, FR-10 | UC008, UC010 | TC010-01 | UC008 E2, UC010 E1/E3 | Cho thao tác hủy và bàn giao đồng thời, lặp lại với hết hạn và bàn giao. | Mỗi yêu cầu chỉ có một kết quả phù hợp với trạng thái đã ghi nhận. Không có lượt thuê từ yêu cầu đã hủy/hết hạn. Chờ Q-04 để chốt mốc. |
| FR-09, FR-10 | UC010 | TC010-02 | Chính | Nhân viên đúng bãi chọn yêu cầu còn hiệu lực, CCCD khớp, điều kiện cọc đạt nếu có, xác nhận giao. | Danh sách đúng phạm vi. Tạo một lượt, lưu mốc và nhân viên giao, xe Đang thuê, yêu cầu Đã bàn giao. |
| FR-09 | UC010 | TC010-03 | E1/E2 | Thử nhân viên khác bãi, CCCD thiếu/không khớp, cọc chưa đạt nếu được yêu cầu. | Từ chối, ghi lý do đúng phạm vi. Không bàn giao. Chờ Q-04–Q-05 về hậu quả của từ chối. |
| FR-10 | UC010 | TC010-04 | E3/E4 | Hai nhân viên xác nhận cùng xe hoặc mô phỏng lỗi lưu giữa chừng. | Tối đa một lượt hoạt động. Dữ liệu xe, yêu cầu và lượt nhất quán. Lỗi chưa rõ hướng dẫn tra cứu lại. |
| FR-09, FR-10 | UC010 | TC010-05 | A1 | Nhân viên chọn xe thay thế khi còn đủ điều kiện. | Chờ Q-04. Nếu cho phép, chỉ xe thực tế có lượt thuê, phần giữ cũ được xử lý đúng. |
| FR-11, FR-15 | UC011 | TC011-01 | Chính | Trả xe còn hoạt động, cùng bãi, tình trạng đạt và xác nhận đầy đủ. | Lưu mốc/bãi/tình trạng, kết thúc lượt, xe Sẵn sàng, một phiếu đủ dữ liệu FR-15. |
| FR-11 | UC011 | TC011-02 | A1/E2 | Trả ở bãi khác, thử bãi còn chỗ và bãi đầy hoặc nhân viên sai bãi. | Khi Q-09 được duyệt, chỉ bãi và quyền hợp lệ được nhận. Xe cập nhật về bãi thực tế khi hoàn tất. |
| FR-11, FR-15 | UC011 | TC011-03 | A2 | Trả xe có hư hỏng thuộc điều kiện sửa chữa. | Lượt hoàn tất, xe Cần sửa chữa, phiếu chỉ có khoản phát sinh theo Q-15 đã duyệt. |
| FR-11, FR-15 | UC011 | TC011-04 | E1/E2 | Thử lượt không tồn tại, đã hoàn tất, thiếu xác nhận và hai thao tác hoàn tất đồng thời. | Không có phiếu thứ hai. Lượt/xe chỉ đổi khi có lần hoàn tất hợp lệ. |
| FR-11, FR-15 | UC011 | TC011-05 | E3/A4 | Mô phỏng lỗi lưu giữa chừng và lỗi hiển thị sau khi đã lưu. | Lỗi lưu không để lại dữ liệu dở dang. Lỗi hiển thị giữ kết quả hoàn tất và một phiếu có thể xem lại. |
| FR-12 | UC012 | TC012-01 | Chính | Dùng mốc giao/trả và biểu phí đã chốt để đối chiếu bảng tính. | Kết quả khớp phí xe, phí thời gian, các khoản riêng và tổng tiền. Chờ Q-05–Q-06. |
| FR-13 | UC012 | TC012-02 | A1 | Đặt thời điểm trả ngay trước, đúng và ngay sau mốc trễ. | Chờ Q-07. Nếu giữ FR-13, áp dụng ngưỡng và làm tròn đã duyệt. Nếu bỏ, không tính phụ thu muộn và cập nhật truy vết. |
| FR-14 | UC012 | TC012-03 | A2 | So sánh cùng lượt mẫu với hồ sơ Đã xác minh, Chờ xét và Bị từ chối tại lúc tính. | Chỉ hồ sơ Đã xác minh được xét. Chờ Q-08 về tỷ lệ và khoản giảm. |
| FR-12 | UC012 | TC012-04 | E1/A3 | Dùng mốc trả trước mốc giao hoặc thiếu biểu phí, sau đó thử ca có hư hỏng hợp lệ. | Dữ liệu sai không trả tổng để xác nhận. Phí hư hỏng chờ Q-15. |
| FR-15, FR-16 | UC009 | TC009-01 | Chính/A1/A2 | Khách xem lượt hoàn tất, lượt đang hoạt động và tài khoản chưa có lượt. | Phiếu có ở lượt đã lập, lượt đang hoạt động hiện trạng thái, tài khoản mới có danh sách rỗng. |
| FR-16 | UC009 | TC009-02 | E1 | Khách A yêu cầu xem lượt/phiếu khách B. | Không trả dữ liệu của B. |
| FR-17 | UC013 | TC013-01 | Chính/A1 | Nhân viên và quản trị viên tìm theo mã, bãi, trạng thái và tiêu chí không khớp. | Hiển thị đúng xe, bãi, trạng thái hoặc danh sách rỗng trong phạm vi xem. Chờ Q-11. |
| FR-17 | UC013 | TC013-02 | E1 | Tài khoản khách yêu cầu chức năng tra cứu vận hành. | Từ chối, không hiển thị dữ liệu ngoài quyền. |
| FR-18 | UC014 | TC014-01 | Chính | Người có quyền đổi trạng thái hợp lệ, hoặc chuyển xe sang bãi hợp lệ. | Thay đổi và lịch sử xe được lưu. Chờ Q-20 về tập chuyển đổi. |
| FR-18 | UC014 | TC014-02 | E1/E2 | Nhân viên sai bãi thử đổi xe, người có quyền thử đổi xe đang thuê sang Sẵn sàng. | Từ chối, giữ liên kết lượt thuê và trạng thái xe. |
| FR-24 | UC015 | TC015-01 | Chính/A1 | Người có quyền xét hai hồ sơ chờ, một đạt và một chưa đạt. | Lần lượt Đã xác minh và Bị từ chối kèm lý do được phép xem. Chờ Q-08. |
| FR-24 | UC015 | TC015-02 | E1 | Người thiếu quyền hoặc hai người đồng thời gửi kết quả cho cùng hồ sơ. | Từ chối thao tác ngoài quyền, chỉ một quyết định hợp lệ cập nhật hồ sơ chờ. |
| FR-19 | UC016 | TC016-01 | Chính/A1/A2 | Quản trị viên thêm bãi, sửa thông tin, rồi ngừng hoạt động khi đủ điều kiện. | Bãi và thông tin cập nhật đúng. Chờ Q-17 để chốt điều kiện ngừng/xóa. |
| FR-19 | UC016 | TC016-02 | E1/E2 | Thử nhân viên sửa bãi và quản trị viên ngừng bãi khi còn điều kiện vướng. | Từ chối, giữ thông tin bãi và liên kết. |
| FR-20 | UC017 | TC017-01 | Chính/A1/A2 | Cấp tài khoản nhân viên, đổi bãi, khóa rồi mở khóa. | Tài khoản, phân công và quyền sử dụng phản ánh thao tác đã lưu. |
| FR-20 | UC017 | TC017-02 | E1/E2 | Thử định danh trùng, bãi không hợp lệ và vai trò không có quyền cấp tài khoản. | Không tạo tài khoản hoặc phân công sai. |
| FR-21 | UC018 | TC018-01 | Chính/A1 | Dùng dữ liệu biết trước theo hai bãi và các mốc ngày/tuần/tháng. Thử bộ lọc rỗng. | Chỉ số khớp dữ liệu trong kỳ/bãi, kết quả rỗng rõ ràng. Chờ Q-18 để chốt định nghĩa và biên kỳ. |
| FR-21 | UC018 | TC018-02 | E1 | Dùng khoảng thời gian ngược và người không có quyền. | Báo lỗi phù hợp, không lộ dữ liệu ngoài phạm vi. |
| FR-22 | UC019 | TC019-01 | Chính/E1 | Nếu phạm vi được duyệt, xuất một kết quả đã lọc và mô phỏng lỗi xuất. | Chờ Q-13. Tệp đúng phạm vi hoặc thông báo lỗi, giữ số liệu đang xem. |
| FR-23 | UC020 | TC020-01 | Chính/E1 | Nếu phạm vi được duyệt, quản trị viên và nhân viên cùng tìm một sự kiện quan trọng. | Chờ Q-14. Người có quyền xem đúng người/thời điểm/nội dung, nhân viên bị từ chối nếu không có quyền. |

## Kiểm tra chéo theo NFR

| NFR | Kịch bản khởi tạo |
|---|---|
| NFR-01, NFR-02 | TC002-01, TC003-02, TC009-02, TC010-03, TC013-02, TC014-02, TC015-02, TC017-02. Bổ sung kiểm tra cách lưu mật khẩu và trường CCCD sau khi Q-03 chốt. |
| NFR-03, NFR-04 | TC007-03, TC008-01, TC010-01, TC010-04, TC011-04, TC011-05, TC014-02. Đối chiếu cả phản hồi và dữ liệu sau lỗi/cạnh tranh. |
| NFR-05, NFR-07 | TC001-02, TC007-04, TC011-04, TC011-05. Kiểm tra dữ liệu nhập và thông báo trạng thái sau lỗi, chạy thử luồng với người dùng theo NFR. |
| NFR-06 | Đo tra cứu UC005, UC006 và UC013 theo tải và ngưỡng Thành viên 1 chốt. |
| NFR-08, NFR-09 | Chạy các luồng chính trên trình duyệt/kích thước đã duyệt. Đối chiếu khả năng cấu hình biểu phí sau khi có thiết kế. |
| NFR-10 | Chờ xác nhận phạm vi sao lưu/khôi phục. |
