# 3.1.2 Đặc tả ca sử dụng

**Hệ thống** Ecopark Bicycle Parking

**Nguồn đối chiếu** Tài liệu Thành viên 1 tại commit `62dbda6`. Mã FR và UC theo repo. Các BR và câu trả lời trong bảng Q vẫn có trạng thái `Open`.

Các luồng có ghi “nếu được duyệt” phụ thuộc [quy tắc còn mở](open-business-rules.md). Tra cứu mã FR và tên actor ở [danh mục](use-case-catalog.md), tên và chuyển trạng thái ở [bảng thuật ngữ](use-case-glossary.md). “Hệ thống báo” là phản hồi cho người đang thao tác.

## UC001 · Đăng ký tài khoản

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tạo tài khoản khách hàng để sử dụng dịch vụ. |
| Phạm vi | Tài khoản khách hàng của Ecopark Bicycle Parking. |
| Actor chính / phụ | Khách hàng chưa có tài khoản / — |
| Mô tả ngắn | Khách cung cấp thông tin đăng ký và nhận kết quả tạo tài khoản. |
| Tiền điều kiện | Chức năng đăng ký tài khoản khách hàng được mở. |
| Kích hoạt | Khách chọn đăng ký. |
| Quy tắc liên quan | BR-04, Q-02, Q-03. NFR-05. |
| FR liên quan | FR-01, FR-03 |
| Dữ liệu vào | SĐT theo ghi chú Q-02, họ tên và mật khẩu theo phương án BR-04. Phạm vi CCCD và trường khác chờ Q-02–Q-03. |
| Dữ liệu ra | Xác nhận tạo tài khoản hoặc lỗi theo trường/định danh. |

**Luồng chính**

1. Khách hàng mở chức năng đăng ký.
2. Hệ thống hiển thị các thông tin cần cung cấp.
3. Khách hàng nhập thông tin và gửi đăng ký.
4. Hệ thống kiểm tra trường bắt buộc, định dạng và các định danh cần duy nhất.
5. Hệ thống tạo tài khoản khách hàng và hiển thị kết quả.

**Luồng thay thế**

- **A1 · Khách sửa dữ liệu sau phản hồi ở bước 4.** Khách nhập lại trường bị lỗi và gửi lại ở bước 3.

**Luồng ngoại lệ**

- **E1 · Thiếu trường hoặc dữ liệu sai ở bước 4.** Hệ thống nêu trường cần sửa và giữ dữ liệu biểu mẫu cần thiết để sửa. Tài khoản chưa được tạo.
- **E2 · Trùng định danh ở bước 4 hoặc phát sinh trùng khi lưu ở bước 5.** Hệ thống từ chối đăng ký và hiển thị thông báo phù hợp. Tài khoản đã tồn tại giữ nguyên.

**Hậu điều kiện** Thành công tạo một tài khoản khách hàng theo Q-02. Thất bại giữ nguyên tập tài khoản.

## UC002 · Đăng nhập

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Truy cập các chức năng được cấp theo vai trò. |
| Phạm vi | Xác thực và mở phiên truy cập hệ thống. |
| Actor chính / phụ | Khách hàng, Nhân viên bãi xe, Quản trị viên / — |
| Mô tả ngắn | Người dùng cung cấp thông tin xác thực để truy cập chức năng theo quyền. |
| Tiền điều kiện | Người dùng có thông tin của một tài khoản và đang ở điểm truy cập đăng nhập. |
| Kích hoạt | Người dùng yêu cầu đăng nhập. |
| Quy tắc liên quan | Q-11 về quyền theo vai trò. FR-01 bao gồm đăng xuất. |
| FR liên quan | FR-01 |
| Dữ liệu vào | Định danh đăng nhập và thông tin xác thực. |
| Dữ liệu ra | Phiên truy cập theo quyền hoặc thông báo từ chối. |

**Luồng chính**

1. Người dùng gửi thông tin đăng nhập.
2. Hệ thống xác thực thông tin và kiểm tra trạng thái cho phép đăng nhập.
3. Hệ thống mở phiên truy cập và hiển thị các chức năng người dùng được phép sử dụng.

**Luồng thay thế**

- **A1 · Người dùng nhập lại sau lỗi xác thực.** Người dùng sửa thông tin và quay lại bước 1.

- **A2 · Người dùng muốn kết thúc phiên sau bước 3.** Người dùng chọn đăng xuất. Hệ thống kết thúc phiên hiện tại và yêu cầu xác thực lại khi truy cập chức năng cần đăng nhập.

**Luồng ngoại lệ**

- **E1 · Thiếu hoặc sai thông tin xác thực ở bước 2.** Hệ thống báo đăng nhập không thành công và không mở phiên.
- **E2 · Tài khoản bị khóa hoặc không đủ điều kiện ở bước 2.** Hệ thống hiển thị phản hồi theo Q-02 và không mở phiên.

**Hậu điều kiện** Thành công mở phiên với quyền được cấp. Đăng xuất thành công làm phiên hiện tại hết hiệu lực. Thất bại không cấp quyền truy cập mới.

## UC003 · Cập nhật hồ sơ

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xem hồ sơ của mình và cập nhật thông tin được phép. |
| Phạm vi | Hồ sơ thông tin tài khoản khách hàng. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Khách xem hồ sơ và có thể lưu thay đổi theo quyền. |
| Tiền điều kiện | Khách hàng đã đăng nhập. |
| Kích hoạt | Khách mở hồ sơ cá nhân. |
| Quy tắc liên quan | BR-04, Q-02, Q-03. NFR-02. |
| FR liên quan | FR-02, FR-03 |
| Dữ liệu vào | Các giá trị hồ sơ muốn sửa, nếu có. |
| Dữ liệu ra | Hồ sơ hiện tại, xác nhận cập nhật hoặc lỗi. |

**Luồng chính**

1. Khách hàng yêu cầu xem hồ sơ của mình.
2. Hệ thống xác định quyền, hiển thị thông tin được xem và đánh dấu trường có thể sửa.
3. Khách hàng sửa các trường được phép và gửi cập nhật.
4. Hệ thống kiểm tra quyền đối với từng trường và kiểm tra dữ liệu.
5. Hệ thống lưu thay đổi và hiển thị hồ sơ đã cập nhật.

**Luồng thay thế**

- **A1 · Chỉ xem hồ sơ ở bước 2.** Khách kết thúc sau khi xem. Hệ thống giữ nguyên hồ sơ.

**Luồng ngoại lệ**

- **E1 · Trường không được phép xem hoặc sửa ở bước 2 hoặc 4.** Hệ thống từ chối thao tác ngoài phạm vi và giữ nguyên hồ sơ.
- **E2 · Dữ liệu sai hoặc định danh trùng ở bước 4 hoặc 5.** Hệ thống nêu phần cần sửa. Hồ sơ trước đó vẫn có hiệu lực.

**Hậu điều kiện** Thành công trả hồ sơ đúng phạm vi hoặc lưu thay đổi hợp lệ. Thất bại giữ nguyên hồ sơ.

## UC004 · Khai báo hồ sơ cư dân

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Nộp thông tin để được xét tư cách cư dân. |
| Phạm vi | Tiếp nhận hồ sơ cư dân. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Khách gửi minh chứng. Kết quả xác minh được xử lý trong UC015. |
| Tiền điều kiện | Khách đã đăng nhập. |
| Kích hoạt | Khách chọn gửi hồ sơ cư dân. |
| Quy tắc liên quan | BR-11, Q-01, Q-03, Q-08. |
| FR liên quan | FR-24 |
| Dữ liệu vào | Thông tin và minh chứng theo phạm vi được duyệt. |
| Dữ liệu ra | Tham chiếu hồ sơ và tình trạng. |

**Luồng chính**

1. Khách hàng gửi thông tin và minh chứng theo yêu cầu.
2. Hệ thống kiểm tra dữ liệu và điều kiện tiếp nhận.
3. Hệ thống lưu hồ sơ **Chờ xét duyệt** và xác nhận đã nhận.

**Luồng thay thế**

- **A1 · Nộp lại hoặc bổ sung sau quyết định, nếu Q-08 cho phép.** Khách gửi lại ở bước 1. Hệ thống áp dụng quy tắc xác định hồ sơ có hiệu lực.

**Luồng ngoại lệ**

- **E1 · Thiếu minh chứng, dữ liệu sai hoặc không đủ điều kiện ở bước 2.** Hệ thống nêu nội dung cần xử lý và giữ nguyên hồ sơ đã có.

**Hậu điều kiện** Thành công ghi nhận hồ sơ **Chờ xét duyệt**. Thất bại giữ nguyên tình trạng. Ưu đãi được xét trong UC012 sau kết quả UC015.

## UC005 · Tra cứu bãi xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xem bãi và tìm bãi gần theo vị trí. |
| Phạm vi | Danh sách bãi và tìm kiếm theo khoảng cách. |
| Actor chính / phụ | Khách hàng. Nhân viên bãi xe, Quản trị viên khi xem danh sách / — |
| Mô tả ngắn | Hệ thống cung cấp danh sách bãi và hỗ trợ tìm bãi gần theo phương án vị trí được duyệt. |
| Tiền điều kiện | Người dùng được quyền tra cứu. |
| Kích hoạt | Người dùng mở danh sách bãi. |
| Quy tắc liên quan | BR-13, Q-10, Q-11, NFR-06. |
| FR liên quan | FR-04, FR-05 |
| Dữ liệu vào | Vị trí tham chiếu khi tìm gần, tiêu chí nếu có. |
| Dữ liệu ra | Tên, địa chỉ/vị trí, số xe Sẵn sàng theo bãi và thứ tự gần khi tìm theo vị trí. |

**Luồng chính**

1. Người dùng mở danh sách bãi.
2. Hệ thống hiển thị bãi trong phạm vi truy cập, cùng tên, địa chỉ hoặc vị trí và số xe **Sẵn sàng**.
3. Khách hàng chọn tìm bãi gần và cung cấp vị trí theo cơ chế Q-10.
4. Hệ thống kiểm tra vị trí, xếp bãi theo khoảng cách áp dụng và hiển thị kết quả.

**Luồng thay thế**

- **A1 · Người dùng chỉ xem danh sách ở bước 2.** Người dùng có thể chọn bãi để tra cứu xe phù hợp theo quyền.
- **A2 · Từ chối quyền vị trí hoặc GPS không khả dụng ở bước 3.** Hệ thống dùng phương án Q-10 được duyệt. BR-13 đề xuất chọn khu vực hoặc giữ danh sách chưa xếp khoảng cách.
- **A3 · Không có bãi phù hợp ở bước 4.** Hệ thống hiển thị kết quả rỗng.

**Luồng ngoại lệ**

- **E1 · Thiếu vị trí hợp lệ và không có nguồn thay thế ở bước 3–4.** Hệ thống báo chưa thể tìm bãi gần. Danh sách bãi thông thường vẫn dùng được theo quyền.

**Hậu điều kiện** Thành công trả danh sách bãi hoặc kết quả theo vị trí. Thất bại trả lý do. Dữ liệu bãi và xe giữ nguyên.

## UC006 · Tra cứu xe khả dụng

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tìm xe có thể chọn để gửi yêu cầu thuê. |
| Phạm vi | Danh sách xe tại bãi và các bộ lọc đã duyệt. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Khách tìm xe, hệ thống trả kết quả khả dụng tại thời điểm tra cứu. |
| Tiền điều kiện | Khách có quyền tra cứu theo Q-11. |
| Kích hoạt | Khách chọn một bãi hoặc mở chức năng tìm xe. |
| Quy tắc liên quan | BR-02, Q-16, Q-20. NFR-03, NFR-06. |
| FR liên quan | FR-06 |
| Dữ liệu vào | Bãi và các tiêu chí được duyệt. Ghi chú Q-16 không áp dụng phân loại xe. |
| Dữ liệu ra | Danh sách xe khả dụng hoặc phản hồi không có kết quả/không hợp lệ. |

**Luồng chính**

1. Khách hàng chọn bãi và các tiêu chí áp dụng.
2. Hệ thống kiểm tra bãi và điều kiện lọc, lấy danh sách xe phù hợp ở trạng thái **Sẵn sàng**.
3. Hệ thống hiển thị kết quả tại thời điểm tra cứu. Khách chọn xe để bắt đầu UC007.

**Luồng thay thế**

- **A1 · Không có xe phù hợp ở bước 2.** Hệ thống hiển thị danh sách rỗng. Khách có thể đổi tiêu chí và quay lại bước 1.

**Luồng ngoại lệ**

- **E1 · Bãi không còn được phép tra cứu hoặc tiêu chí không hợp lệ ở bước 2.** Hệ thống báo cần chọn lại. Trạng thái xe giữ nguyên.
- **E2 · Xe mất khả dụng sau bước 3.** Khi khách tiếp tục gửi yêu cầu, hệ thống kiểm tra lại trong UC007 và từ chối chọn xe đã mất khả dụng.

**Hậu điều kiện** Thành công trả kết quả đúng thời điểm tra cứu. Thất bại thông báo lý do. Tra cứu chưa tạo yêu cầu hoặc giữ xe.

## UC007 · Gửi yêu cầu thuê

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Đề nghị thuê xe và nhận xác nhận giữ xe theo phương án Q-04. |
| Phạm vi | Từ chọn bãi, xe và thời lượng tới ghi nhận yêu cầu. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Tiếp nhận yêu cầu chờ bàn giao. Ghi chú Q-04 đề xuất giữ xe 10 phút từ lúc yêu cầu và giới hạn một yêu cầu chờ hoặc lượt thuê đang hoạt động. |
| Tiền điều kiện | Khách đã đăng nhập. |
| Kích hoạt | Khách gửi yêu cầu cho xe đã chọn. |
| Quy tắc liên quan | BR-02, BR-07–BR-09, Q-04–Q-06, Q-20, NFR-03–NFR-05. |
| FR liên quan | FR-07 |
| Dữ liệu vào | Bãi nhận, xe, thời lượng chọn và dữ liệu xác nhận cọc nếu Q-05 yêu cầu. |
| Dữ liệu ra | Mã yêu cầu, tình trạng giữ xe, thời hạn nếu áp dụng. |

**Luồng chính**

1. Khách hàng chọn bãi, xe và thời lượng dự kiến.
2. Khách hàng gửi yêu cầu, kèm dữ liệu cọc nếu chính sách đã duyệt yêu cầu ở bước này.
3. Hệ thống kiểm tra lựa chọn, số yêu cầu/lượt thuê còn mở, điều kiện cọc nếu có và xe vẫn **Sẵn sàng** tại bãi.
4. Hệ thống kiểm tra lại lúc lưu, đồng thời tạo yêu cầu **Chờ bàn giao** và chuyển xe **Đã đặt** theo phương án Q-04. Hệ thống hiển thị mã và thời hạn giữ xe.

**Luồng thay thế**

- **A1 · Khách đổi lựa chọn trước khi gửi ở bước 2.** Khách quay lại bước 1. Yêu cầu đặt trước theo khung giờ chỉ được đặc tả thêm khi Q-04 chốt chi tiết.
- **A2 · Yêu cầu chạm hạn giữ trước bàn giao.** Hệ thống áp dụng mốc Q-04. Nếu yêu cầu vẫn đang chờ và đã hết hạn, hệ thống ghi **Hết hạn** và giải phóng đúng phần giữ trong cùng lần cập nhật. Hệ thống ghi nhận kết quả cọc theo Q-05 nếu chính sách áp dụng.

**Luồng ngoại lệ**

- **E1 · Xe đã được giữ/thuê hoặc không còn ở bãi nhận tại bước 3–4.** Hệ thống yêu cầu chọn lại. Yêu cầu và xe của người đã giữ thành công giữ nguyên.
- **E2 · Dữ liệu thiếu/sai, có yêu cầu hoặc lượt thuê đang mở, hoặc điều kiện cọc không đạt ở bước 3.** Hệ thống hiển thị lý do và giữ dữ liệu nhập để khách xử lý.
- **E3 · Mất kết nối hoặc chưa rõ kết quả lưu ở bước 4.** Hệ thống hướng người dùng kiểm tra yêu cầu hiện có trước khi gửi lại. Thử lại tuân theo giới hạn Q-04.

**Hậu điều kiện** Thành công có một yêu cầu **Chờ bàn giao** và xe **Đã đặt** theo phương án giữ xe. Lượt thuê chỉ bắt đầu tại UC010. Thất bại đã xác định giữ nguyên trạng thái trước thao tác.

## UC008 · Hủy yêu cầu thuê

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Hủy yêu cầu của mình khi còn đủ điều kiện. |
| Phạm vi | Hủy yêu cầu chưa bàn giao, giải phóng phần giữ và xử lý tình trạng cọc theo chính sách. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Hệ thống kiểm tra điều kiện hủy và tách kết quả hủy khỏi việc xét hoàn cọc. |
| Tiền điều kiện | Khách đã đăng nhập. |
| Kích hoạt | Khách gửi thao tác hủy. |
| Quy tắc liên quan | BR-02, BR-07, BR-08, Q-04, Q-05, Q-20, NFR-03–NFR-04. |
| FR liên quan | FR-08 |
| Dữ liệu vào | Mã yêu cầu, thời điểm hủy và dữ liệu cần để xét cọc nếu được duyệt. |
| Dữ liệu ra | Tình trạng yêu cầu, kết quả giải phóng xe và thông tin cọc được phép hiển thị. |

**Luồng chính**

1. Khách hàng chọn yêu cầu của mình và gửi thao tác hủy.
2. Hệ thống kiểm tra chủ yêu cầu, hiệu lực và điều kiện hủy.
3. Hệ thống kiểm tra lại lúc lưu, chuyển yêu cầu sang **Đã hủy** và giải phóng phần giữ của yêu cầu.
4. Hệ thống hiển thị kết quả hủy và tình trạng xử lý cọc nếu áp dụng Q-05.

**Luồng thay thế**

- **A1 · Yêu cầu đã hủy khi kiểm tra ở bước 2.** Hệ thống hiển thị trạng thái hiện tại cho chủ yêu cầu. Phần giữ và kết quả cọc giữ nguyên.
- **A2 · Có cọc khi hủy ở bước 4.** Hệ thống đánh giá theo Q-05. Ghi chú nêu hủy trong 5 phút và lần thuê trước thành công để được xét hoàn trong 3 phút, còn mốc biên, lần thuê đầu và cách ghi nhận hoàn cần nhóm chốt.

**Luồng ngoại lệ**

- **E1 · Yêu cầu không thuộc quyền hoặc không tồn tại ở bước 2.** Hệ thống từ chối mà không tiết lộ dữ liệu ngoài quyền.
- **E2 · Yêu cầu hết hạn, đã bàn giao hoặc không thỏa điều kiện hủy ở bước 2–3.** Hệ thống từ chối hủy. Kết quả bàn giao/hết hạn đã ghi nhận giữ nguyên.

**Hậu điều kiện** Thành công yêu cầu **Đã hủy** và phần giữ tương ứng đã được giải phóng. Thất bại giữ nguyên kết quả hiện hành. Trạng thái cọc tuân theo Q-05.

## UC009 · Xem lịch sử thuê

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xem lịch sử và phiếu của mình. |
| Phạm vi | Lịch sử thuê của khách hàng. |
| Actor chính / phụ | Khách hàng / — |
| Mô tả ngắn | Khách chọn một lượt thuê thuộc tài khoản và có thể xem lại phiếu đã lập. |
| Tiền điều kiện | Khách đã đăng nhập. |
| Kích hoạt | Khách mở lịch sử thuê. |
| Quy tắc liên quan | FR-15, FR-16, NFR-02. |
| FR liên quan | FR-15, FR-16 |
| Dữ liệu vào | Lượt thuê đã chọn, tiêu chí nếu được duyệt. |
| Dữ liệu ra | Danh sách/chi tiết lượt thuê và phiếu được phép xem. |

**Luồng chính**

1. Khách hàng mở lịch sử thuê.
2. Hệ thống hiển thị các lượt thuê của tài khoản hiện tại.
3. Khách hàng chọn lượt thuê. Hệ thống xác minh quyền sở hữu, hiển thị chi tiết và phiếu nếu đã lập.

**Luồng thay thế**

- **A1 · Không có lượt thuê ở bước 2.** Hệ thống trả danh sách rỗng.
- **A2 · Lượt thuê chưa hoàn tất ở bước 3.** Hệ thống chỉ hiển thị thông tin lượt thuê và trạng thái hiện tại.

**Luồng ngoại lệ**

- **E1 · Lượt thuê không tồn tại hoặc thuộc khách khác ở bước 3.** Hệ thống từ chối và không trả chi tiết hay phiếu.

**Hậu điều kiện** Thành công trả dữ liệu của khách. Thất bại không tiết lộ dữ liệu ngoài quyền. Tra cứu chỉ đọc.

## UC010 · Bàn giao xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xác minh điều kiện và ghi nhận giao xe để bắt đầu lượt thuê. |
| Phạm vi | Danh sách yêu cầu tại bãi, xác minh và bàn giao. |
| Actor chính / phụ | Nhân viên bãi xe / Khách hàng |
| Mô tả ngắn | Nhân viên đối chiếu khách, yêu cầu và đúng xe đang giữ trước khi xác nhận giao. |
| Tiền điều kiện | Nhân viên đã đăng nhập. Khách đến nhận xe. |
| Kích hoạt | Nhân viên mở yêu cầu của khách. |
| Quy tắc liên quan | BR-02, BR-05–BR-08, BR-14, Q-03–Q-05, Q-11, Q-20, NFR-01, NFR-03–NFR-04. |
| FR liên quan | FR-09, FR-10 |
| Dữ liệu vào | Mã yêu cầu, xe, bãi, kết quả đối chiếu và cọc nếu áp dụng, xác nhận giao. |
| Dữ liệu ra | Mã lượt thuê, mốc và nhân viên giao, trạng thái hoặc lý do từ chối. |

**Luồng chính**

1. Nhân viên mở danh sách yêu cầu thuộc bãi được phân công và chọn yêu cầu của khách.
2. Hệ thống kiểm tra quyền, hiển thị yêu cầu, thông tin khách và nội dung đối chiếu được phép.
3. Khách xuất trình CCCD theo phương án Q-04. Nhân viên đối chiếu với thông tin được phép xem, kiểm tra xe đang được giữ đúng yêu cầu và xác nhận cọc nếu áp dụng.
4. Nhân viên chấp nhận và xác nhận giao xe.
5. Hệ thống kiểm tra lại quyền tại bãi, hiệu lực yêu cầu, xe **Đã đặt** cho đúng yêu cầu và điều kiện bắt buộc.
6. Hệ thống lưu đồng thời mốc và nhân viên giao, yêu cầu **Đã bàn giao**, xe **Đang thuê**, lượt thuê **Đang hoạt động**. Hệ thống hiển thị xác nhận.

**Luồng thay thế**

- **A1 · Nhân viên cần đổi xe ở bước 3, nếu Q-04 cho phép.** Nhân viên chọn xe thay thế. Hệ thống kiểm tra xe, bãi và quyền, rồi cập nhật phần giữ và bàn giao trong cùng lần hoàn tất.

**Luồng ngoại lệ**

- **E1 · Yêu cầu hết hạn, đã hủy, đã bàn giao hoặc nhân viên không có quyền ở bước 2 hoặc 5.** Hệ thống báo kết quả được phép xem. Hệ thống chưa tạo lượt thuê qua thao tác này.
- **E2 · CCCD thiếu/không khớp, điều kiện cọc chưa đạt hoặc điều kiện khác không đạt ở bước 3–5.** Nhân viên ghi lý do từ chối. Hệ thống không ghi bàn giao. Đóng yêu cầu và giải phóng xe chỉ thực hiện theo chính sách Q-04.
- **E3 · Xe không còn được giữ cho đúng yêu cầu hoặc đã được bàn giao qua thao tác khác ở bước 5–6.** Hệ thống báo xung đột, giữ nguyên kết quả đã ghi nhận.
- **E4 · Không xác nhận được kết quả lưu ở bước 6.** Hệ thống báo cần tra cứu lại trước khi thử. Dữ liệu chỉ phản ánh bàn giao đầy đủ hoặc trạng thái trước thao tác.

**Hậu điều kiện** Thành công có một lượt thuê **Đang hoạt động** cho xe giao. Khi xác định thất bại, không phát sinh lượt thuê mới và không đổi xe sang **Đang thuê** do lần thử đó.

## UC011 · Ghi nhận trả xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tiếp nhận xe trả, kết thúc lượt thuê và lập phiếu. |
| Phạm vi | Tra cứu lượt, ghi nhận bãi/mốc/tình trạng, gọi UC012, hoàn tất và lập phiếu. |
| Actor chính / phụ | Nhân viên bãi xe / Khách hàng |
| Mô tả ngắn | Nhân viên kiểm tra xe và bãi trả, xác nhận phí đã tính, sau đó hệ thống lưu cùng phiếu. |
| Tiền điều kiện | Nhân viên đã đăng nhập. Khách đưa xe đến bãi và cung cấp thông tin đối chiếu. |
| Kích hoạt | Nhân viên bắt đầu ghi nhận trả xe. |
| Quy tắc liên quan | BR-02, BR-08, BR-12, BR-14, BR-17, Q-05, Q-09, Q-11, Q-13, Q-15, Q-20, NFR-04–NFR-05. |
| FR liên quan | FR-11, FR-15 |
| Dữ liệu vào | Tham chiếu xe/lượt thuê, bãi trả, mốc trả, tình trạng xe và xác nhận. |
| Dữ liệu ra | Xác nhận hoàn tất, vị trí/trạng thái xe, phiếu thuê/trả theo FR-15. |

**Luồng chính**

1. Nhân viên tra cứu lượt thuê đang hoạt động của xe.
2. Hệ thống xác minh trạng thái lượt thuê, quyền xử lý tại bãi và tính hợp lệ của bãi trả.
3. Nhân viên đối chiếu xe và ghi nhận bãi trả, mốc trả, tình trạng xe.
4. Hệ thống kiểm tra dữ liệu, gọi UC012 và trình kết quả tính phí.
5. Nhân viên kiểm tra các khoản, ghi nhận xác nhận cần thiết theo Q-05 và xác nhận hoàn tất.
6. Hệ thống kiểm tra lại quyền, trạng thái, bãi, dữ liệu và xác nhận. Nếu khoản tiền đã đổi, hệ thống trình lại để xác nhận.
7. Hệ thống ghi nhận cùng lúc dữ liệu trả, kết quả phí, phiếu, lượt thuê **Đã hoàn tất** và trạng thái/vị trí xe tại bãi trả. Hệ thống hiển thị xác nhận và phiếu theo quyền.

**Luồng thay thế**

- **A1 · Khách trả tại bãi khác ở bước 2.** Theo ghi chú Q-09, bãi trả phải còn chỗ. Nếu được duyệt, hệ thống kiểm tra bãi trả đủ điều kiện và quyền của nhân viên, rồi dùng bãi trả thực tế ở bước 3 và 7.
- **A2 · Xe hư hỏng ở bước 3.** Nhân viên ghi tình trạng. Hệ thống áp dụng Q-15, Q-20 khi tính khoản phát sinh và xác định **Cần sửa chữa** khi hoàn tất.
- **A3 · Cần sửa dữ liệu ở bước 4–6.** Nhân viên quay lại bước 3. Hệ thống tính lại trước xác nhận.
- **A4 · Phiếu đã lưu nhưng hiển thị lỗi ở bước 7.** Hệ thống báo kết quả hoàn tất nếu xác định được. Khách có thể xem lại phiếu đã lập qua UC009.

**Luồng ngoại lệ**

- **E1 · Không có lượt đang hoạt động hoặc thiếu quyền ở bước 2 hoặc 6.** Hệ thống từ chối theo quyền, giữ nguyên kết quả đã lưu và không sinh phiếu mới.
- **E2 · Bãi không đủ điều kiện, hết chỗ theo Q-09, dữ liệu sai hoặc thiếu xác nhận ở bước 2–6.** Hệ thống báo nội dung cần xử lý, giữ dữ liệu biểu mẫu và chưa hoàn tất.
- **E3 · UC012 chưa tính được phí hoặc hệ thống không lưu được đầy đủ ở bước 4 hoặc 7.** Hệ thống báo lỗi và giữ dữ liệu nhập. Nếu chưa rõ kết quả lưu, nhân viên tra cứu lại trước khi xác nhận lần nữa.

**Hậu điều kiện** Thành công có một phiếu, lượt thuê **Đã hoàn tất**, xe cập nhật về bãi trả. Thất bại đã xác định trước khi lưu giữ lượt thuê **Đang hoạt động**, xe và phiếu giữ nguyên.

## UC012 · Tính phí lượt thuê

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tính chi phí lượt thuê để nhân viên xác nhận trong UC011. |
| Phạm vi | Tính thời lượng, giá thuê và khoản áp dụng trước khi lập phiếu. |
| Actor chính / phụ | Được gọi bởi UC011 / — |
| Mô tả ngắn | Hệ thống tính theo chính sách có hiệu lực và trả chi tiết khoản tiền cho luồng trả xe. |
| Tiền điều kiện | Có lượt thuê, dữ liệu trả hợp lệ và biểu phí áp dụng. |
| Kích hoạt | UC011 yêu cầu tính phí ở bước 4. |
| Quy tắc liên quan | BR-08–BR-11, BR-17, Q-05–Q-08, Q-15, NFR-09. |
| FR liên quan | FR-12, FR-13, FR-14 |
| Dữ liệu vào | Mốc giao/trả, lựa chọn thuê, biểu phí, hồ sơ cư dân, tình trạng xe và cọc nếu áp dụng. |
| Dữ liệu ra | Thời lượng thực tế, phí cơ bản, các khoản phụ thu/giảm giá, cọc riêng nếu có và số tiền cuối cùng. |

**Luồng chính**

1. Hệ thống xác định thời lượng từ mốc giao và trả được công nhận.
2. Hệ thống tính phí cơ bản theo biểu giá. Ghi chú Q-05 và Q-06 đề xuất tách phí xe và phí thời gian thực tế.
3. Hệ thống xác định các khoản phát sinh theo Q-07, Q-15 và xét trạng thái cư dân tại lúc tính theo FR-14.
4. Hệ thống tính các khoản và tổng tiền theo quy tắc áp dụng. Hệ thống trình bày cọc thành khoản riêng khi có và trả kết quả cho UC011.

**Luồng thay thế**

- **A1 · Thời lượng thực tế vượt thời lượng chọn ở bước 3.** Nếu giữ FR-13, hệ thống tính phụ thu theo ngưỡng và đơn vị được duyệt. Nếu duyệt ghi chú Q-07, kết quả không có phụ thu trả muộn.
- **A2 · Hồ sơ đã xác minh hoặc chưa xác minh ở bước 3.** Chỉ trạng thái **Đã xác minh** đủ điều kiện xét theo FR-14. Q-08 quyết định mức và khoản được giảm.
- **A3 · Xe hư hỏng khi trả ở bước 3.** Hệ thống chỉ tính khoản đã được chốt theo Q-15. Trường hợp mất xe và mức bồi thường nêu trong ghi chú cần chốt phạm vi riêng.

**Luồng ngoại lệ**

- **E1 · Mốc thời gian, biểu giá hoặc quy tắc bắt buộc không hợp lệ ở bước 1–4.** Hệ thống báo UC011 chưa thể tính phí và không trả số tiền để xác nhận.

**Hậu điều kiện** Thành công có bảng tính phục vụ xác nhận. Thất bại chưa có kết quả phí hợp lệ. UC011 chịu trách nhiệm hoàn tất lượt thuê và lập phiếu.

## UC013 · Tra cứu xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tìm xe và xem trạng thái, bãi hiện tại. |
| Phạm vi | Tra cứu dữ liệu đội xe. |
| Actor chính / phụ | Nhân viên bãi xe, Quản trị viên / — |
| Mô tả ngắn | Người dùng tìm xe theo mã, bãi và trạng thái trong phạm vi xem. |
| Tiền điều kiện | Người dùng đã đăng nhập. |
| Kích hoạt | Người dùng mở tra cứu xe. |
| Quy tắc liên quan | BR-01, BR-14, Q-11, Q-19, NFR-01, NFR-06. |
| FR liên quan | FR-17 |
| Dữ liệu vào | Mã xe, bãi, trạng thái hoặc tổ hợp được hỗ trợ. |
| Dữ liệu ra | Danh sách và thông tin trạng thái/bãi của xe trong phạm vi được xem. |

**Luồng chính**

1. Người dùng nhập tiêu chí tra cứu.
2. Hệ thống kiểm tra quyền xem và tiêu chí.
3. Hệ thống hiển thị các xe phù hợp, trạng thái và bãi hiện tại.

**Luồng thay thế**

- **A1 · Không có xe phù hợp ở bước 3.** Hệ thống hiển thị danh sách rỗng. Người dùng có thể đổi tiêu chí.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền hoặc tiêu chí không hợp lệ ở bước 2.** Hệ thống từ chối, không hiển thị dữ liệu ngoài phạm vi.

**Hậu điều kiện** Thành công trả dữ liệu được phép hoặc danh sách rỗng. Thất bại giữ dữ liệu xe nguyên vẹn.

## UC014 · Cập nhật trạng thái xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tra cứu và cập nhật trạng thái, vị trí xe trong phạm vi được cấp. |
| Phạm vi | Quản lý dữ liệu xe tại bãi, ngoài cập nhật do bàn giao và trả xe. |
| Actor chính / phụ | Nhân viên bãi xe, Quản trị viên theo quyền / — |
| Mô tả ngắn | Người quản lý chọn xe và thực hiện chuyển trạng thái/vị trí được phép. |
| Tiền điều kiện | Người dùng đã đăng nhập. |
| Kích hoạt | Người dùng mở chức năng quản lý xe. |
| Quy tắc liên quan | BR-01 đến BR-03, BR-14. Q-11, Q-17, Q-19, Q-20. NFR-01, NFR-04. |
| FR liên quan | FR-18 |
| Dữ liệu vào | Tham chiếu xe, bãi hoặc trạng thái dự kiến và thông tin cần ghi nhận theo quy tắc. |
| Dữ liệu ra | Chi tiết xe, kết quả cập nhật hoặc lỗi. |

**Luồng chính**

1. Người dùng tra cứu và chọn xe.
2. Hệ thống kiểm tra quyền và hiển thị dữ liệu xe.
3. Người dùng yêu cầu cập nhật vị trí hoặc trạng thái được phép.
4. Hệ thống kiểm tra quyền với xe/bãi liên quan, trạng thái hiện hành và tính hợp lệ của chuyển đổi, sau đó lưu trạng thái/vị trí và lịch sử thay đổi xe rồi hiển thị kết quả.

**Luồng thay thế**

- **A1 · Người dùng chỉ cần tra cứu ở bước 2.** Hệ thống hiển thị dữ liệu được phép xem và kết thúc.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền, xe không tồn tại hoặc bãi đích không hợp lệ ở bước 2 hoặc 4.** Hệ thống từ chối và giữ nguyên dữ liệu.
- **E2 · Chuyển đổi không hợp lệ hoặc trạng thái đã đổi ở bước 4.** Hệ thống báo cần kiểm tra lại. Cập nhật quản trị không được làm mất liên kết của xe với lượt thuê đang hoạt động.

**Hậu điều kiện** Thành công trả thông tin hoặc lưu thay đổi được phép, kèm lịch sử trạng thái/vị trí theo FR-18. Thất bại giữ nguyên dữ liệu hiện hành.

## UC015 · Xác minh hồ sơ cư dân

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xác định hồ sơ cư dân có đủ điều kiện xác minh. |
| Phạm vi | Xét hồ sơ chờ từ UC004. |
| Actor chính / phụ | Quản trị viên hoặc vai trò được Q-08 giao / — |
| Mô tả ngắn | Người có quyền đối chiếu minh chứng và ghi nhận kết quả. |
| Tiền điều kiện | Người xét đã đăng nhập. Có hồ sơ đang chờ để xử lý. |
| Kích hoạt | Người xét mở hồ sơ chờ. |
| Quy tắc liên quan | BR-11, Q-03, Q-08, NFR-01–NFR-02. |
| FR liên quan | FR-24 |
| Dữ liệu vào | Tham chiếu hồ sơ, minh chứng được phép xem, quyết định và lý do nếu từ chối. |
| Dữ liệu ra | Tình trạng và kết quả được phép hiển thị. |

**Luồng chính**

1. Người xét chọn hồ sơ.
2. Hệ thống kiểm tra quyền, tình trạng hồ sơ và hiển thị thông tin được phép xem.
3. Người xét đối chiếu minh chứng theo tiêu chí, chọn xác minh.
4. Hệ thống kiểm tra hồ sơ vẫn chờ, lưu **Đã xác minh** và hiển thị kết quả.

**Luồng thay thế**

- **A1 · Minh chứng không đạt ở bước 3.** Người xét ghi lý do. Hệ thống kiểm tra hồ sơ vẫn chờ, lưu **Bị từ chối** và hiển thị kết quả trong phạm vi quyền.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền, hồ sơ không tồn tại hoặc đã được xét ở bước 2 hoặc 4.** Hệ thống từ chối và giữ nguyên quyết định hiện hành.

**Hậu điều kiện** Thành công có quyết định hợp lệ. Thất bại giữ nguyên hồ sơ. UC012 sử dụng tình trạng xác minh để xét ưu đãi.

## UC016 · Quản lý bãi xe

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Duy trì thông tin bãi để phục vụ tra cứu và vận hành. |
| Phạm vi | Thêm, sửa và ngừng hoạt động bãi theo FR-19. |
| Actor chính / phụ | Quản trị viên / — |
| Mô tả ngắn | Quản trị viên chọn thao tác và hệ thống kiểm tra dữ liệu, liên kết với xe và lượt thuê. |
| Tiền điều kiện | Quản trị viên đã đăng nhập. |
| Kích hoạt | Quản trị viên mở quản lý bãi. |
| Quy tắc liên quan | BR-16, Q-11, Q-17, NFR-01. |
| FR liên quan | FR-19 |
| Dữ liệu vào | Thông tin bãi, thao tác và mã bãi nếu đã tồn tại. |
| Dữ liệu ra | Chi tiết bãi, kết quả quản trị hoặc lỗi. |

**Luồng chính**

1. Quản trị viên chọn bãi cần sửa.
2. Hệ thống kiểm tra quyền và hiển thị thông tin.
3. Quản trị viên nhập thay đổi và xác nhận.
4. Hệ thống kiểm tra dữ liệu và điều kiện liên quan, lưu và hiển thị kết quả.

**Luồng thay thế**

- **A1 · Thêm bãi ở bước 1.** Quản trị viên cung cấp thông tin bãi mới. Hệ thống kiểm tra và lưu bãi nếu hợp lệ.
- **A2 · Ngừng hoạt động bãi ở bước 1.** Quản trị viên xác nhận. Hệ thống kiểm tra xe, yêu cầu và lượt thuê liên quan theo quy tắc được duyệt rồi mới cập nhật tình trạng bãi.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền, dữ liệu sai hoặc bãi cần sửa không tồn tại ở bước 2 hoặc 4.** Hệ thống báo lỗi và không lưu.
- **E2 · Thao tác ngừng hoạt động vướng điều kiện hoặc yêu cầu xóa chưa được duyệt.** Hệ thống báo điều kiện cần xử lý, giữ nguyên bãi và các liên kết.

**Hậu điều kiện** Thành công lưu thao tác hợp lệ. Thất bại giữ nguyên bãi và liên kết nghiệp vụ. Việc xóa vật lý chờ Q-17.

## UC017 · Quản lý tài khoản

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Cấp và quản trị tài khoản trong phạm vi được giao. |
| Phạm vi | Cấp tài khoản nhân viên, phân công bãi và khóa/mở khóa tài khoản theo FR-20. |
| Actor chính / phụ | Quản trị viên / — |
| Mô tả ngắn | Quản trị viên thao tác trên tài khoản, hệ thống kiểm tra vai trò, bãi và dữ liệu trước khi lưu. |
| Tiền điều kiện | Quản trị viên đã đăng nhập. |
| Kích hoạt | Quản trị viên mở quản lý tài khoản. |
| Quy tắc liên quan | Q-02, Q-11, NFR-01–NFR-02. |
| FR liên quan | FR-20 |
| Dữ liệu vào | Tài khoản đích hoặc dữ liệu cấp tài khoản, bãi phân công, thao tác khóa/mở khóa nếu có. |
| Dữ liệu ra | Kết quả quản trị, vai trò/tình trạng và bãi được phép hiển thị. |

**Luồng chính**

1. Quản trị viên chọn cấp tài khoản nhân viên và nhập thông tin.
2. Hệ thống kiểm tra quyền, dữ liệu tài khoản và định danh duy nhất.
3. Quản trị viên chọn bãi phân công theo quy định và xác nhận.
4. Hệ thống kiểm tra bãi, tạo tài khoản và ghi nhận phân công hợp lệ.

**Luồng thay thế**

- **A1 · Đổi bãi cho nhân viên hiện có ở bước 1.** Quản trị viên chọn tài khoản và bãi. Hệ thống kiểm tra quyền, lưu phân công và hiển thị kết quả.
- **A2 · Khóa hoặc mở khóa ở bước 1.** Quản trị viên chọn tài khoản và xác nhận. Hệ thống kiểm tra phạm vi quản trị và cập nhật tình trạng.
- **A3 · Chỉ tra cứu ở bước 1.** Hệ thống hiển thị thông tin trong quyền và kết thúc.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền, định danh trùng hoặc bãi không hợp lệ ở bước 2–4.** Hệ thống báo phần cần xử lý và không lưu tài khoản hoặc phân công chưa hợp lệ.
- **E2 · Tài khoản không tồn tại hoặc trạng thái đã đổi khi xác nhận nhánh A1/A2.** Hệ thống yêu cầu kiểm tra lại, giữ kết quả hiện hành.

**Hậu điều kiện** Thành công trả dữ liệu hoặc ghi nhận thao tác được phép. Thất bại giữ nguyên dữ liệu tài khoản và phân công.

## UC018 · Xem thống kê

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xem số liệu vận hành theo kỳ và bãi. |
| Phạm vi | Thống kê trong phạm vi dữ liệu được phép. |
| Actor chính / phụ | Quản trị viên / — |
| Mô tả ngắn | Quản trị viên chọn tiêu chí, hệ thống tổng hợp và hiển thị kết quả. |
| Tiền điều kiện | Quản trị viên đã đăng nhập. |
| Kích hoạt | Quản trị viên mở thống kê. |
| Quy tắc liên quan | BR-15, Q-11, Q-18, NFR-01. |
| FR liên quan | FR-21 |
| Dữ liệu vào | Kỳ ngày/tuần/tháng, bãi và khoảng thời gian theo BR-15 và ghi chú Q-18. |
| Dữ liệu ra | Số lượt thuê, doanh thu, xe theo trạng thái, tỷ lệ trả muộn nếu được xác nhận. |

**Luồng chính**

1. Quản trị viên chọn kỳ, khoảng thời gian và bãi.
2. Hệ thống kiểm tra quyền, kỳ và tiêu chí.
3. Hệ thống tổng hợp chỉ số theo BR-15 trong phạm vi quyền và hiển thị cùng tiêu chí.

**Luồng thay thế**

- **A1 · Không có dữ liệu phù hợp ở bước 3.** Hệ thống hiển thị kết quả rỗng theo quy ước thống kê đã duyệt.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền hoặc khoảng thời gian không hợp lệ ở bước 2.** Hệ thống báo lỗi và không trả số liệu ngoài phạm vi.

**Hậu điều kiện** Thành công hiển thị số liệu trong phạm vi. Thất bại trả lỗi phù hợp. Dữ liệu nghiệp vụ nguồn giữ nguyên.

## UC019 · Xuất báo cáo

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Xuất kết quả thống kê đã xem nếu FR-22 được duyệt. |
| Phạm vi | Mở rộng UC018. Hiện ở trạng thái Pending scope. |
| Actor chính / phụ | Quản trị viên / — |
| Mô tả ngắn | Bản dự phòng mô tả tạo tệp theo kết quả thống kê. Q-13 có ghi chú “Không” cần xác nhận cách áp dụng. |
| Tiền điều kiện | UC018 có kết quả trong quyền và nhóm đã duyệt FR-22. |
| Kích hoạt | Quản trị viên chọn xuất. |
| Quy tắc liên quan | Q-13, Q-18. Phạm vi và định dạng chưa chốt. |
| FR liên quan | FR-22 |
| Dữ liệu vào | Tiêu chí thống kê và định dạng nếu được duyệt. |
| Dữ liệu ra | Tệp báo cáo hoặc lỗi. |

**Luồng chính**

1. Quản trị viên yêu cầu xuất kết quả đang xem.
2. Hệ thống kiểm tra quyền xuất và tiêu chí.
3. Hệ thống tạo tệp theo phạm vi dữ liệu, trả tệp cho quản trị viên.

**Luồng thay thế**

- **A1 · Kết quả hiện tại rỗng ở bước 3.** Hệ thống áp dụng quy tắc xuất dữ liệu rỗng đã duyệt tại Q-13.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền hoặc xuất thất bại ở bước 2–3.** Hệ thống báo lỗi và giữ kết quả UC018 trong phạm vi quyền.

**Hậu điều kiện** Thành công trả tệp hợp lệ trong quyền. Thất bại không trả tệp chưa tạo thành công.

## UC020 · Tra cứu nhật ký thay đổi

| Mục | Đặc tả |
|---|---|
| Mục tiêu | Tra cứu thay đổi quan trọng nếu FR-23 được duyệt. |
| Phạm vi | Nhật ký tổng quát của hệ thống. Hiện ở trạng thái Pending scope. |
| Actor chính / phụ | Quản trị viên / — |
| Mô tả ngắn | Bản dự phòng mô tả tìm và xem nhật ký trong quyền. |
| Tiền điều kiện | Đã đăng nhập và nhóm đã duyệt FR-23. |
| Kích hoạt | Quản trị viên mở tra cứu nhật ký. |
| Quy tắc liên quan | Q-14. Phạm vi sự kiện và quyền chưa chốt. |
| FR liên quan | FR-23 |
| Dữ liệu vào | Tiêu chí tra cứu theo phạm vi đã duyệt. |
| Dữ liệu ra | Người thực hiện, thời điểm, nội dung thay đổi được phép xem. |

**Luồng chính**

1. Quản trị viên gửi tiêu chí tra cứu.
2. Hệ thống kiểm tra quyền và tiêu chí.
3. Hệ thống hiển thị nhật ký phù hợp trong phạm vi quyền.

**Luồng thay thế**

- **A1 · Không có sự kiện phù hợp ở bước 3.** Hệ thống hiển thị danh sách rỗng.

**Luồng ngoại lệ**

- **E1 · Thiếu quyền hoặc tiêu chí không hợp lệ ở bước 2.** Hệ thống báo lỗi và không trả nhật ký ngoài quyền.

**Hậu điều kiện** Thành công trả dữ liệu trong phạm vi. Thất bại giữ nguyên nhật ký. Lịch sử trạng thái/vị trí xe vẫn được xử lý trong UC014 theo FR-18.

## Dữ liệu và sự kiện bàn giao cho Thành viên 3 và 4

| UC | Dữ liệu vào cần đối chiếu | Dữ liệu ra kiểm chứng được | Sự kiện và thay đổi |
|---|---|---|---|
| UC004, UC015 | Khách, minh chứng, quyền người xét, quyết định và lý do | Mã hồ sơ, tình trạng, kết quả trong quyền | Tiếp nhận → Chờ xét duyệt. Xét → Đã xác minh hoặc Bị từ chối. |
| UC007 | Khách, bãi nhận, xe, thời lượng, cọc nếu có | Mã yêu cầu, tình trạng và hạn giữ | Tiếp nhận → Chờ bàn giao và xe Đã đặt theo Q-04. |
| UC008 | Chủ yêu cầu, mã, thời điểm hủy, tình trạng cọc nếu có | Kết quả hủy và thông tin cọc được phép xem | Hủy hợp lệ → Đã hủy và giải phóng đúng phần giữ. Hết hạn là sự kiện khác theo Q-04. |
| UC010 | Mã yêu cầu, quyền tại bãi, xe, đối chiếu giấy tờ, xác nhận | Mã lượt thuê, mốc/nhân viên giao và trạng thái | Bàn giao → Đã bàn giao, Đang thuê, Đang hoạt động. |
| UC011 | Mã lượt, bãi trả, mốc trả, tình trạng xe, xác nhận | Xác nhận, bãi/trạng thái xe, phiếu theo FR-15 | Hoàn tất → Đã hoàn tất và một phiếu. Xe cập nhật theo bãi trả và tình trạng. |
| UC012 | Mốc giao/trả, thời lượng chọn, biểu phí, cư dân, tình trạng xe/cọc | Thời lượng, phí cơ bản, phụ thu, giảm giá, cọc riêng, tổng tiền | Trả kết quả tính về UC011 trước khi hoàn tất. |

Thành viên 3 xác nhận thành phần thiết kế, nơi giữ trạng thái và ranh giới ghi nhận nhất quán theo NFR-03–NFR-04. Thành viên 4 đối chiếu phản hồi và trạng thái sau mỗi thao tác theo ma trận. Dữ liệu và cách tính phụ thuộc quyết định nghiệp vụ được đánh dấu theo mã Q.
