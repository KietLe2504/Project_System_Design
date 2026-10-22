# Phân công công việc --- Thành viên 1

## Dự án: Ecopark Bicycle Parking

**Vai trò:** Phân tích nghiệp vụ và yêu cầu hệ thống\
**Phạm vi chính:** Chương 1, Chương 2 (tùy chọn nhưng nên có bản gọn),
và phần tổng quan yêu cầu trong Chương 3.\
**Mục tiêu:** Tạo một nền tảng phân tích rõ ràng để thành viên phụ trách
Use Case, Thiết kế và Kiểm thử có thể tiếp tục mà không phải tự đoán
nghiệp vụ.

------------------------------------------------------------------------

## 1. Tổng quan nhiệm vụ

Thành viên 1 chịu trách nhiệm mô tả **vấn đề cần giải quyết, phạm vi hệ
thống, các bên liên quan, quy trình nghiệp vụ và danh mục yêu cầu**.
Thành viên này không chịu trách nhiệm chính cho đặc tả chi tiết từng Use
Case hoặc thiết kế UML ở Chương 4; các phần đó được bàn giao cho thành
viên phụ trách Use Case và thành viên thiết kế.

### Các đầu ra bắt buộc

1.  Nội dung Chương 1 --- Đặt vấn đề.
2.  Nội dung Chương 2 --- Phân tích nghiệp vụ (có thể rút gọn vì hướng
    dẫn ghi *Optional*).
3.  Danh mục yêu cầu chức năng (FR) có mã định danh.
4.  Danh mục yêu cầu phi chức năng (NFR) có mã định danh.
5.  Sơ đồ phân rã chức năng / biểu đồ gói ở mức tổng quan.
6.  Biểu đồ Use Case tổng quan, gồm tác nhân và nhóm chức năng; **không
    thay thế** các bản đặc tả Use Case chi tiết của thành viên 2.
7.  Bảng truy vết yêu cầu ban đầu, dùng để đối chiếu với Use Case, thiết
    kế và kiểm thử.
8.  Danh sách các quy tắc nghiệp vụ đã xác nhận và các câu hỏi còn chờ
    nhóm trưởng quyết định.

------------------------------------------------------------------------

## 2. Tài liệu đầu vào

Trước khi viết, thành viên 1 cần đọc và đối chiếu:

-   `group-project-guideline.docx`: cấu trúc báo cáo môn Phân tích Thiết
    kế Hệ thống.
-   Đề bài / mô tả bài toán Ecopark Bicycle Parking do nhóm nhận được.
-   README hoặc tài liệu mô tả phiên bản hệ thống hiện tại (nếu nhóm
    dùng mã nguồn có sẵn).
-   Các quyết định phạm vi và quy tắc nghiệp vụ đã được nhóm trưởng xác
    nhận.
-   Trao đổi với thành viên 2 để thống nhất tên tác nhân, tên chức năng
    và mã Use Case.

**Lưu ý:** Nếu tài liệu đầu vào không nêu rõ một quy tắc, không tự coi
giả định là yêu cầu chính thức. Ghi nó vào danh sách câu hỏi cần nhóm
trưởng xác nhận.

------------------------------------------------------------------------

## 3. Công việc chi tiết theo mã nhiệm vụ

## M1-01 --- Đọc đề bài và xác định phạm vi hệ thống

**Mục tiêu:** Viết được một mô tả thống nhất về hệ thống sẽ xây dựng và
những gì không thuộc phạm vi.

### Các bước thực hiện

-   [ ] Đọc toàn bộ đề bài và hướng dẫn báo cáo.
-   [ ] Tóm tắt bài toán hiện tại: người dùng cần thuê xe ở các bãi
    trong Ecopark; nhân viên xử lý giao/nhận xe; quản trị viên theo dõi
    đội xe và hoạt động.
-   [ ] Xác định mục tiêu hệ thống: hỗ trợ tìm bãi/xe, tạo yêu cầu thuê,
    kiểm tra điều kiện giao xe, ghi nhận trả xe, tính phí và quản lý dữ
    liệu vận hành.
-   [ ] Liệt kê nhóm người dùng chính: khách hàng, cư dân Ecopark, nhân
    viên bãi xe, quản trị viên/điều hành.
-   [ ] Viết rõ các chức năng nằm trong phạm vi và ngoài phạm vi.
-   [ ] Đánh dấu các quy tắc còn cần xác nhận, ví dụ: xử lý tiền đặt
    cọc, phương thức thanh toán, phạm vi dữ liệu cá nhân được lưu và
    việc triển khai trên web hay cả web/mobile.

### Đầu ra

-   `scope.md` hoặc mục "Phạm vi hệ thống" trong báo cáo.
-   Bảng *In scope / Out of scope / Pending decision*.

### Tiêu chí nghiệm thu

-   Phạm vi mô tả được ít nhất bốn nhóm người dùng chính.
-   Không mâu thuẫn với đề bài và quyết định đã chốt của nhóm.
-   Phân biệt rõ chức năng đã xác nhận với giả định/chức năng dự kiến.
-   Các phần ngoài phạm vi không được viết như thể hệ thống chắc chắn sẽ
    triển khai.

------------------------------------------------------------------------

## M1-02 --- Viết Chương 1: Đặt vấn đề

Theo hướng dẫn, Chương 1 cần giới thiệu ngữ cảnh, hiện trạng và nhu cầu
xây dựng hệ thống; mô tả sơ bộ yêu cầu chức năng và giải pháp.

### 1.1. Bối cảnh và hiện trạng

Viết 2--4 đoạn ngắn trả lời:

-   Hoạt động thuê xe đạp tại nhiều bãi cần quản lý những thông tin gì?
-   Vì sao cần biết xe nào đang rảnh, đang được thuê, hoặc cần sửa chữa?
-   Những khó khăn có thể phát sinh khi tra cứu xe, bàn giao, nhận trả,
    tính phụ thu và tổng hợp số liệu bằng quy trình thủ công hoặc dữ
    liệu phân tán?
-   Vì sao cần một hệ thống dùng chung để đồng bộ thông tin giữa khách
    hàng, nhân viên và bộ phận điều hành?

Chỉ nêu vấn đề hợp lý theo bài toán; không khẳng định một tổ chức cụ thể
đang gặp sự cố thực tế nếu đề bài không cung cấp bằng chứng.

### 1.2. Mục tiêu hệ thống

Nêu mục tiêu theo góc nhìn nghiệp vụ, chẳng hạn:

-   Hỗ trợ khách hàng tìm bãi và xe có thể thuê.
-   Hỗ trợ nhân viên xác minh điều kiện và thực hiện giao/nhận xe.
-   Tính phí thuê và phụ thu theo quy tắc đã thống nhất.
-   Quản lý trạng thái, vị trí và lịch sử sử dụng của xe.
-   Cung cấp thống kê cho quản trị viên/điều hành.
-   Áp dụng ưu đãi cư dân khi đáp ứng điều kiện xác minh.

### 1.3. Mô tả sơ bộ chức năng

Tóm tắt theo nhóm, chưa đi vào từng bước Use Case:

1.  Tài khoản và hồ sơ khách hàng.
2.  Tra cứu bãi xe, vị trí và xe còn khả dụng.
3.  Tạo/hủy yêu cầu thuê.
4.  Xác minh và bàn giao xe.
5.  Tiếp nhận trả xe, tính phí, phụ thu và xuất phiếu thuê/trả.
6.  Quản lý bãi, xe, trạng thái xe và tài khoản.
7.  Thống kê, lịch sử, nhật ký và xuất báo cáo.
8.  Xác minh thông tin cư dân và áp dụng ưu đãi.

Chỉ giữ các nhóm thực sự nằm trong phạm vi đã chốt.

### 1.4. Giải pháp sơ bộ

Mô tả ở mức khái quát: một hệ thống phần mềm có giao diện cho khách hàng
và giao diện vận hành cho nhân viên/quản trị; dữ liệu bãi, xe, lượt
thuê, tài khoản và phí được quản lý tập trung. Nếu nhóm quyết định chỉ
làm web responsive, hãy dùng đúng cách gọi đó; không mô tả đồng thời một
ứng dụng mobile riêng nếu chưa được thống nhất.

### 1.5. Cấu trúc báo cáo

Tóm tắt một câu cho mỗi chương từ Chương 1 đến Chương 7 theo hướng dẫn
môn học.

### Đầu ra

-   Bản thảo Chương 1 hoàn chỉnh.
-   Nếu có hình minh họa bối cảnh, ghi rõ nguồn; ưu tiên sơ đồ do nhóm
    tự vẽ nếu phù hợp.

### Tiêu chí nghiệm thu

-   Đủ ba ý hướng dẫn yêu cầu: bối cảnh/nhu cầu, chức năng sơ bộ, giải
    pháp sơ bộ.
-   Văn phong báo cáo, rõ ràng, không viết như quảng cáo sản phẩm.
-   Không đưa chi tiết thiết kế lớp, cơ sở dữ liệu hoặc thuật toán vào
    Chương 1.
-   Các chức năng nêu ở đây phải xuất hiện nhất quán trong danh mục yêu
    cầu ở Chương 3.

------------------------------------------------------------------------

## M1-03 --- Viết Chương 2: Phân tích nghiệp vụ (Optional)

Chương 2 được hướng dẫn ghi là tùy chọn. Nên làm bản ngắn nhưng có giá
trị, tránh dành quá nhiều thời gian nếu nhóm đang thiếu thời gian hoàn
thiện Use Case và thiết kế.

### 2.1. Cơ cấu tổ chức

Mô tả các vai trò nghiệp vụ và trách nhiệm của họ:

  -----------------------------------------------------------------------
  Vai trò                             Trách nhiệm nghiệp vụ
  ----------------------------------- -----------------------------------
  Khách hàng                          Tạo/quản lý tài khoản, tìm xe, gửi
                                      yêu cầu thuê, theo dõi lượt thuê và
                                      lịch sử

  Cư dân Ecopark                      Thực hiện các thao tác như khách
                                      hàng; được xem xét ưu đãi khi hồ sơ
                                      cư dân được xác minh

  Nhân viên bãi xe                    Xử lý yêu cầu thuộc phạm vi bãi
                                      được phân công; kiểm tra giấy
                                      tờ/điều kiện, giao xe và tiếp nhận
                                      xe trả

  Quản trị viên/Điều hành             Quản lý bãi, xe, tài khoản và dữ
                                      liệu vận hành; xem thống kê, nhật
                                      ký và báo cáo
  -----------------------------------------------------------------------

Điều chỉnh tên vai trò theo đề bài và thiết kế thực tế. Nếu hệ thống
không phân biệt "khách hàng" và "cư dân" thành hai tác nhân độc lập, hãy
ghi rõ cư dân là một loại hồ sơ/nhóm quyền lợi của khách hàng, không tự
tạo tác nhân riêng một cách máy móc.

### 2.2. Quy trình nghiệp vụ

Vẽ sơ đồ hoạt động hoặc lưu đồ nghiệp vụ ở mức dễ đọc. Tối thiểu nên mô
tả:

**Quy trình A --- Thuê xe** 1. Khách hàng đăng nhập hoặc đăng ký. 2. Tra
cứu bãi và xe có thể thuê. 3. Chọn xe/thời lượng và gửi yêu cầu. 4. Nhân
viên kiểm tra yêu cầu và thông tin giấy tờ. 5. Kiểm tra điều kiện giao
xe, bao gồm đặt cọc và giấy tờ theo quy định đã chốt. 6. Giao xe và cập
nhật trạng thái xe/lượt thuê.

**Quy trình B --- Trả xe** 1. Khách hàng đưa xe đến bãi trả được chấp
nhận. 2. Nhân viên kiểm tra xe và ghi nhận tình trạng. 3. Hệ thống xác
định thời lượng thuê và tính phí/phụ thu. 4. Kiểm tra điều kiện ưu đãi
cư dân. 5. Xuất phiếu, cập nhật lịch sử và trạng thái/vị trí xe.

**Quy trình C --- Quản lý đội xe** 1. Nhân viên hoặc quản trị viên tra
cứu xe. 2. Cập nhật trạng thái/vị trí hoặc ghi nhận xe cần sửa chữa. 3.
Hệ thống lưu lịch sử thay đổi. 4. Quản trị viên tra cứu thống kê/báo
cáo.

Không đưa vào sơ đồ những bước chưa được nhóm xác nhận. Có thể dùng
swimlane để phân biệt Khách hàng / Nhân viên / Hệ thống / Quản trị viên.

### 2.3. Các lớp lĩnh vực (đối tượng nghiệp vụ)

Liệt kê và mô tả ngắn các khái niệm nghiệp vụ, không cần thiết kế thuộc
tính/phương thức như biểu đồ lớp phần mềm.

  -----------------------------------------------------------------------
  Đối tượng nghiệp vụ                 Ý nghĩa
  ----------------------------------- -----------------------------------
  Khách hàng                          Người sử dụng dịch vụ thuê xe

  Hồ sơ cư dân                        Thông tin dùng để xét điều kiện ưu
                                      đãi cư dân

  Bãi xe                              Địa điểm chứa và quản lý xe

  Xe đạp                              Tài sản có mã định danh duy nhất,
                                      trạng thái và vị trí hiện tại

  Yêu cầu thuê                        Yêu cầu thuê được gửi trước khi
                                      nhân viên bàn giao xe

  Lượt thuê                           Ghi nhận một phiên thuê từ lúc giao
                                      xe đến lúc trả xe

  Phiếu thuê/trả                      Chứng từ/thông tin tổng kết lượt
                                      thuê và khoản phí

  Nhân viên                           Người xử lý giao/nhận xe tại bãi

  Nhật ký trạng thái xe               Lịch sử thay đổi trạng thái/vị trí
                                      xe

  Báo cáo thống kê                    Dữ liệu tổng hợp theo kỳ và tiêu
                                      chí quản lý
  -----------------------------------------------------------------------

Danh sách trên là đề xuất ban đầu; cần thống nhất tên gọi với thành viên
thiết kế. Không yêu cầu các khái niệm nghiệp vụ phải tương ứng một-một
với bảng cơ sở dữ liệu hoặc lớp phần mềm.

### Đầu ra

-   Mục 2.1 mô tả vai trò/cơ cấu nghiệp vụ.
-   Ít nhất 2--3 sơ đồ quy trình nghiệp vụ.
-   Bảng mô tả đối tượng nghiệp vụ.

### Tiêu chí nghiệm thu

-   Sơ đồ có điểm bắt đầu/kết thúc và thể hiện được các nhánh điều kiện
    quan trọng.
-   Tên vai trò và tên đối tượng nhất quán với Chương 3.
-   Sơ đồ thể hiện nghiệp vụ, không biến thành sơ đồ trình tự API hoặc
    sơ đồ lớp.
-   Nếu cần rút gọn, giữ quy trình thuê, trả xe và quản lý xe trước.

------------------------------------------------------------------------

## M1-04 --- Lập danh mục yêu cầu chức năng (FR)

### Nguyên tắc

-   Mỗi yêu cầu có mã duy nhất, ví dụ `FR-01`, `FR-02`.
-   Mỗi yêu cầu nên diễn đạt một khả năng hoặc kết quả có thể kiểm tra.
-   Dùng cách viết "Hệ thống phải..." để câu yêu cầu rõ ràng.
-   Không gộp nhiều chức năng độc lập vào một yêu cầu quá dài.
-   Không mô tả chi tiết luồng chính/luồng ngoại lệ của Use Case tại
    đây; phần đó do thành viên 2 phụ trách.

### Danh mục khởi tạo để nhóm rà soát

  -----------------------------------------------------------------------
  Mã                      Nhóm                    Yêu cầu chức năng dự
                                                  kiến
  ----------------------- ----------------------- -----------------------
  FR-01                   Tài khoản               Hệ thống cho phép khách
                                                  hàng đăng ký và đăng
                                                  nhập

  FR-02                   Hồ sơ                   Hệ thống cho phép khách
                                                  hàng xem/cập nhật thông
                                                  tin hồ sơ trong phạm vi
                                                  được phép

  FR-03                   Hồ sơ                   Hệ thống kiểm tra các
                                                  thông tin định danh bắt
                                                  buộc theo quy tắc đã
                                                  chốt

  FR-04                   Bãi xe                  Hệ thống hiển thị danh
                                                  sách bãi xe và thông
                                                  tin vị trí

  FR-05                   Tra cứu                 Hệ thống cho phép tìm
                                                  bãi gần người dùng theo
                                                  cơ chế vị trí đã thống
                                                  nhất

  FR-06                   Tra cứu                 Hệ thống hiển thị xe có
                                                  thể thuê tại bãi và cho
                                                  phép lọc theo tiêu chí
                                                  được hỗ trợ

  FR-07                   Yêu cầu thuê            Hệ thống cho phép khách
                                                  hàng chọn xe/thời lượng
                                                  và gửi yêu cầu thuê

  FR-08                   Yêu cầu thuê            Hệ thống cho phép hủy
                                                  yêu cầu khi yêu cầu
                                                  chưa được hoàn tất theo
                                                  quy tắc nghiệp vụ

  FR-09                   Giao xe                 Hệ thống hỗ trợ nhân
                                                  viên kiểm tra yêu cầu,
                                                  giấy tờ và điều kiện
                                                  bàn giao

  FR-10                   Giao xe                 Hệ thống ghi nhận thông
                                                  tin bàn giao và cập
                                                  nhật trạng thái xe/lượt
                                                  thuê

  FR-11                   Trả xe                  Hệ thống hỗ trợ nhân
                                                  viên ghi nhận bãi trả
                                                  và tình trạng xe

  FR-12                   Tính phí                Hệ thống tính phí thuê
                                                  theo biểu phí và thời
                                                  lượng được xác nhận

  FR-13                   Tính phí                Hệ thống tính phụ thu
                                                  trả muộn theo quy tắc
                                                  đã chốt

  FR-14                   Ưu đãi                  Hệ thống áp dụng ưu đãi
                                                  cư dân khi hồ sơ đáp
                                                  ứng điều kiện xác minh

  FR-15                   Phiếu                   Hệ thống tạo và hiển
                                                  thị thông tin phiếu
                                                  thuê/trả sau khi hoàn
                                                  tất

  FR-16                   Lịch sử                 Hệ thống lưu và cho
                                                  phép tra cứu lịch sử
                                                  thuê của khách hàng

  FR-17                   Quản lý xe              Hệ thống cho phép người
                                                  có quyền quản lý tra
                                                  cứu xe và trạng thái/vị
                                                  trí hiện tại

  FR-18                   Quản lý xe              Hệ thống cho phép cập
                                                  nhật trạng thái xe theo
                                                  quyền hạn

  FR-19                   Quản lý bãi             Hệ thống cho phép quản
                                                  trị viên quản lý thông
                                                  tin bãi xe

  FR-20                   Quản lý tài khoản       Hệ thống cho phép quản
                                                  trị viên thực hiện các
                                                  thao tác quản lý tài
                                                  khoản trong phạm vi
                                                  được phép

  FR-21                   Thống kê                Hệ thống cung cấp thống
                                                  kê theo kỳ và tiêu chí
                                                  được xác nhận

  FR-22                   Báo cáo                 Hệ thống hỗ trợ xuất
                                                  báo cáo nếu chức năng
                                                  này thuộc phạm vi cuối
                                                  cùng

  FR-23                   Nhật ký                 Hệ thống lưu nhật ký
                                                  các thay đổi quan trọng
                                                  nếu chức năng audit
                                                  được đưa vào phạm vi
  -----------------------------------------------------------------------

**Quan trọng:** Bảng trên là danh mục khởi tạo để phân tích, không phải
danh sách yêu cầu đã được phê duyệt. Thành viên 1 phải đối chiếu đề bài,
mã nguồn/tài liệu hiện có và quyết định của nhóm trưởng để sửa, gộp hoặc
loại bỏ yêu cầu không thuộc phạm vi.

### Đầu ra

-   Bảng FR chính thức với các cột tối thiểu: `ID`, `Tên yêu cầu`,
    `Mô tả`, `Tác nhân liên quan`, `Mức ưu tiên`, `Nguồn/ghi chú`.
-   Biểu đồ phân rã chức năng hoặc biểu đồ gói ở mức tổng quan.
-   Biểu đồ Use Case tổng quan.

### Tiêu chí nghiệm thu

-   Mã FR không trùng lặp và được dùng thống nhất trong báo cáo.
-   Mỗi FR có thể kiểm chứng bằng một hoặc nhiều Use Case/test case.
-   Không có yêu cầu mâu thuẫn với quy tắc nghiệp vụ đã được xác nhận.
-   Biểu đồ tổng quan dễ đọc, không nhồi toàn bộ bước xử lý vào một
    hình.
-   Bàn giao danh sách FR cho thành viên 2 để ánh xạ sang Use Case.

------------------------------------------------------------------------

## M1-05 --- Lập danh mục yêu cầu phi chức năng (NFR)

NFR mô tả chất lượng hoặc ràng buộc của hệ thống, không phải chức năng
nghiệp vụ.

### Các nhóm cần xem xét

  -----------------------------------------------------------------------
  Mã gợi ý                Nhóm                    Nội dung cần xác định
  ----------------------- ----------------------- -----------------------
  NFR-01                  Bảo mật                 Thông tin tài khoản và
                                                  dữ liệu định danh phải
                                                  được bảo vệ; quyền truy
                                                  cập phải phù hợp với
                                                  vai trò

  NFR-02                  Quyền riêng tư          Chỉ thu thập/lưu thông
                                                  tin cá nhân cần thiết
                                                  cho nghiệp vụ và giới
                                                  hạn người được xem

  NFR-03                  Toàn vẹn dữ liệu        Một xe không được đồng
                                                  thời được bàn giao cho
                                                  nhiều lượt thuê đang
                                                  hoạt động

  NFR-04                  Tính nhất quán          Trạng thái xe, lượt
                                                  thuê và bãi/vị trí hiện
                                                  tại phải được cập nhật
                                                  nhất quán

  NFR-05                  Khả dụng                Hệ thống cần hiển thị
                                                  lỗi và cho phép người
                                                  dùng tiếp tục hoặc thử
                                                  lại trong các trường
                                                  hợp lỗi phù hợp

  NFR-06                  Hiệu năng               Xác định mục tiêu phản
                                                  hồi cho các thao tác
                                                  tra cứu thường dùng;
                                                  chỉ ghi số đo cụ thể
                                                  nếu nhóm có căn cứ

  NFR-07                  Dễ sử dụng              Các bước tìm xe, gửi
                                                  yêu cầu, bàn giao và
                                                  trả xe phải có thông
                                                  báo trạng thái/lỗi rõ
                                                  ràng

  NFR-08                  Tương thích             Xác định các trình
                                                  duyệt, kích thước màn
                                                  hình hoặc thiết bị cần
                                                  hỗ trợ

  NFR-09                  Khả năng bảo trì        Cấu trúc hệ thống và
                                                  tài liệu phải đủ rõ để
                                                  thành viên khác có thể
                                                  tiếp tục phát triển

  NFR-10                  Sao lưu/khôi phục       Xác định yêu cầu lưu
                                                  trữ và khôi phục dữ
                                                  liệu nếu thuộc phạm vi
                                                  triển khai
  -----------------------------------------------------------------------

Không tự đặt các cam kết như "phản hồi dưới 1 giây", "99,99% uptime"
hoặc "mã hóa theo chuẩn X" nếu nhóm chưa kiểm chứng hoặc chưa được yêu
cầu. Nếu cần tiêu chí định lượng, hãy đề xuất để nhóm trưởng duyệt và
ghi rõ cách đo.

### Đầu ra

Bảng NFR có các cột: `ID`, `Thuộc tính chất lượng`, `Yêu cầu`,
`Cách kiểm tra/đánh giá`, `Trạng thái xác nhận`.

### Tiêu chí nghiệm thu

-   NFR không chỉ là các câu chung chung như "hệ thống thân thiện" hoặc
    "hệ thống nhanh".
-   Mỗi NFR có cách đánh giá phù hợp; với NFR chưa có ngưỡng số, phải
    ghi rõ cần thống nhất.
-   Không nhầm NFR với chức năng, ví dụ "quản lý xe" là chức năng; "chỉ
    nhân viên được phân quyền mới được cập nhật xe" có khía cạnh bảo
    mật/phân quyền.

------------------------------------------------------------------------

## M1-06 --- Xây dựng sơ đồ tổng quan chức năng và Use Case

### Sơ đồ phân rã chức năng / biểu đồ gói

Gợi ý nhóm chức năng cấp cao:

-   Quản lý tài khoản và hồ sơ.
-   Tra cứu bãi và xe.
-   Quản lý yêu cầu thuê.
-   Bàn giao xe.
-   Trả xe và tính phí.
-   Quản lý đội xe/bãi xe.
-   Thống kê và báo cáo.

Điều chỉnh tên nhóm theo phạm vi cuối cùng. Biểu đồ phải cho thấy cấu
trúc chức năng, không mô tả thứ tự thời gian.

### Biểu đồ Use Case tổng quan

Tác nhân có thể gồm:

-   Khách hàng.
-   Nhân viên bãi xe.
-   Quản trị viên/Điều hành.
-   Dịch vụ bên ngoài (chỉ khi thực sự có tương tác ngoài hệ thống và
    nhóm quyết định thể hiện).

Cư dân có thể được mô hình hóa là khách hàng có trạng thái xác minh cư
dân thay vì một actor riêng; cần trao đổi với thành viên 2 để chọn cách
nhất quán.

### Cách phối hợp với thành viên 2

-   Chia sẻ danh mục FR, tác nhân và thuật ngữ ngay khi có bản nháp đầu
    tiên.
-   Thống nhất mã Use Case (ví dụ `UC001`, `UC002`) với thành viên 2.
-   Thành viên 1 chỉ chịu trách nhiệm **biểu đồ tổng quan**; thành viên
    2 chịu trách nhiệm **đặc tả từng Use Case**, gồm tiền điều kiện, hậu
    điều kiện, luồng chính, luồng thay thế/ngoại lệ và quy tắc liên
    quan.
-   Khi thành viên 2 đề xuất Use Case mới, cập nhật lại FR nếu chức năng
    đó chưa được phản ánh.

### Đầu ra

-   Một sơ đồ phân rã chức năng/biểu đồ gói.
-   Một biểu đồ Use Case tổng quan.
-   Danh mục ánh xạ sơ bộ `FR → UC`.

### Tiêu chí nghiệm thu

-   Tất cả chức năng quan trọng trong bảng FR được phản ánh trên sơ đồ
    tổng quan.
-   Mọi actor đều có vai trò rõ ràng.
-   Tên Use Case dùng động từ + đối tượng, ví dụ "Tra cứu xe", "Gửi yêu
    cầu thuê", "Ghi nhận trả xe".
-   Sơ đồ và danh mục FR không mâu thuẫn với đặc tả Use Case của thành
    viên 2.

------------------------------------------------------------------------

## M1-07 --- Lập bảng quy tắc nghiệp vụ và câu hỏi cần xác nhận

Tạo bảng riêng để phân biệt quy tắc đã chốt với nội dung còn mở.

### Quy tắc cần rà soát

  -----------------------------------------------------------------------
  Chủ đề                              Nội dung cần xác nhận
  ----------------------------------- -----------------------------------
  Định danh xe                        Mã xe có duy nhất trên toàn hệ
                                      thống hay chỉ trong từng bãi?

  Trạng thái xe                       Danh sách trạng thái hợp lệ và các
                                      chuyển trạng thái được phép

  Đăng ký                             Trường hồ sơ bắt buộc và quy tắc
                                      chống trùng thông tin

  Bàn giao                            Loại giấy tờ phải kiểm tra; tiền
                                      đặt cọc; điều kiện từ chối bàn giao

  Giá thuê                            Các gói giá có phải mức cố định hay
                                      tính theo thời gian thực tế?

  Trả muộn                            Cách làm tròn thời gian trễ và cách
                                      tính phụ thu

  Ưu đãi cư dân                       Điều kiện xác minh; mức giảm; khoản
                                      phí nào được giảm

  Hoàn cọc                            Thời điểm và điều kiện hoàn cọc,
                                      nếu nghiệp vụ có quy định

  Trả khác bãi                        Bãi nào được phép nhận trả và quyền
                                      xử lý của nhân viên

  Vị trí                              Dùng GPS, nhập vị trí thủ công hay
                                      cơ chế khác; xử lý khi không có GPS

  Thống kê                            Các kỳ thống kê, bộ lọc và chỉ số
                                      cần hiển thị

  Phân quyền                          Nhân viên được thao tác ở bãi được
                                      phân công hay trên toàn hệ thống?
  -----------------------------------------------------------------------

Nếu tài liệu hoặc mã nguồn hiện tại đã mô tả rõ một quy tắc, hãy ghi
nguồn và đề nghị nhóm trưởng xác nhận đó là quy tắc dùng cho báo cáo.
Không tự suy ra quy tắc chỉ từ giao diện.

### Đầu ra

-   `business-rules.md` hoặc bảng quy tắc nghiệp vụ trong tài liệu nhóm.
-   Danh sách quyết định cần nhóm trưởng phê duyệt, có trạng thái
    `Open / Confirmed / Rejected`.

### Tiêu chí nghiệm thu

-   Mỗi quy tắc quan trọng có trạng thái rõ ràng.
-   Không có hai quy tắc mâu thuẫn cùng được coi là đã xác nhận.
-   Thành viên 2, 3 và 4 có thể dùng bảng này để viết Use Case, thiết kế
    và kiểm thử.

------------------------------------------------------------------------

## M1-08 --- Xây dựng bảng truy vết yêu cầu

Tạo bảng để theo dõi yêu cầu từ mô tả nghiệp vụ đến Use Case và kiểm
thử.

  -----------------------------------------------------------------------
  FR ID       Yêu cầu     UC liên     Thành phần  Test case   Trạng thái
                          quan        thiết kế                
  ----------- ----------- ----------- ----------- ----------- -----------
  FR-05       Tra cứu bãi Chờ thành   Chờ thành   Chờ thành   Draft
              gần người   viên 2 ánh  viên 3      viên 4      
              dùng        xạ                                  

  FR-12       Tính phí    Chờ thành   Chờ thành   Chờ thành   Draft
              thuê        viên 2 ánh  viên 3      viên 4      
                          xạ                                  

  FR-14       Áp dụng ưu  Chờ thành   Chờ thành   Chờ thành   Draft
              đãi cư dân  viên 2 ánh  viên 3      viên 4      
                          xạ                                  
  -----------------------------------------------------------------------

Đây là ví dụ cấu trúc, không phải ánh xạ đã được xác nhận. Sau khi nhận
tài liệu từ các thành viên khác, cập nhật bảng để chỉ ra: - Yêu cầu chưa
có Use Case. - Use Case không truy về yêu cầu nào. - Yêu cầu chưa có
thiết kế hoặc kiểm thử tương ứng. - Các mục chưa hoàn tất hoặc còn tranh
luận.

### Đầu ra

-   `requirements-traceability.xlsx`, bảng Markdown hoặc bảng trong báo
    cáo.
-   Bản cập nhật cuối trước khi nhóm nộp bài.

### Tiêu chí nghiệm thu

-   Mọi FR đã duyệt đều có ít nhất một UC liên quan hoặc lý do giải
    thích.
-   Các yêu cầu quan trọng có cách kiểm thử/đánh giá tương ứng.
-   Không đánh dấu hoàn thành khi thành viên phụ trách chưa bàn giao
    bằng chứng.

------------------------------------------------------------------------

## 4. Những việc thành viên 1 không chịu trách nhiệm chính

Để tránh trùng lặp công việc, thành viên 1 **không** là người chịu trách
nhiệm chính cho:

-   Đặc tả chi tiết tất cả Use Case: thành viên 2.
-   Biểu đồ trình tự, hoạt động hoặc máy trạng thái ở mức thiết kế chi
    tiết: phối hợp thành viên 2/3 theo phân công.
-   Kiến trúc logic/triển khai, biểu đồ lớp thiết kế, ERD và thiết kế cơ
    sở dữ liệu: thành viên 3.
-   Cài đặt chức năng, cấu trúc mã nguồn, môi trường triển khai, test
    case thực thi và đánh giá kết quả: thành viên 4.
-   Quyết định cuối cùng về phạm vi hoặc quy tắc còn tranh luận: nhóm
    trưởng phê duyệt.

Thành viên 1 vẫn cần **rà soát tính nhất quán** của các phần trên với
yêu cầu đã viết, nhưng không thay thế trách nhiệm của người phụ trách
chính.

------------------------------------------------------------------------

## 5. Kế hoạch bàn giao và phối hợp

  -----------------------------------------------------------------------
  Mốc               Việc cần bàn giao Người nhận        Điều kiện bàn
                                                        giao
  ----------------- ----------------- ----------------- -----------------
  Mốc 1             Phạm vi, actor,   Nhóm trưởng và cả Có phân biệt nội
                    danh sách quy tắc nhóm              dung đã chốt/chưa
                    còn mở                              chốt

  Mốc 2             Bản nháp Chương 1 Nhóm trưởng       Đủ cấu trúc,
                    và Chương 2                         thuật ngữ nhất
                                                        quán

  Mốc 3             Bảng FR/NFR bản   Thành viên 2      Có mã ID, tác
                    nháp và Use Case                    nhân và mô tả rõ
                    tổng quan                           

  Mốc 4             Quy tắc nghiệp vụ Thành viên 2, 3,  Các quy tắc quan
                    đã duyệt          4                 trọng có trạng
                                                        thái xác nhận

  Mốc 5             Bảng truy vết cập Nhóm trưởng và cả Có liên kết tới
                    nhật              nhóm              UC, thiết kế và
                                                        test case khi đã
                                                        có

  Mốc cuối          Chương 1--3 đã rà Nhóm trưởng       Không còn lỗi mâu
                    soát                                thuẫn hoặc thuật
                                                        ngữ
  -----------------------------------------------------------------------

Thời hạn cụ thể do nhóm trưởng đặt theo lịch chung. Nếu có thay đổi phạm
vi, thành viên 1 cập nhật FR/NFR và thông báo cho các thành viên liên
quan, không chỉ sửa riêng phần báo cáo của mình.

------------------------------------------------------------------------

## 6. Danh sách kiểm tra trước khi gửi nhóm trưởng

### Chương 1

-   [ ] Có bối cảnh và vấn đề cụ thể.
-   [ ] Nêu mục tiêu hệ thống.
-   [ ] Tóm tắt các nhóm chức năng.
-   [ ] Mô tả giải pháp sơ bộ.
-   [ ] Giới thiệu cấu trúc báo cáo.
-   [ ] Không đưa chi tiết thiết kế quá sớm.

### Chương 2

-   [ ] Có mô tả các vai trò nghiệp vụ.
-   [ ] Có quy trình thuê xe.
-   [ ] Có quy trình trả xe.
-   [ ] Có quy trình quản lý xe/bãi ở mức phù hợp.
-   [ ] Có bảng đối tượng nghiệp vụ.
-   [ ] Tên vai trò/đối tượng nhất quán với Chương 3.

### Chương 3 --- Phần thành viên 1 phụ trách

-   [ ] FR có mã duy nhất và mô tả kiểm chứng được.
-   [ ] NFR có cách đánh giá hoặc ghi chú cần xác nhận.
-   [ ] Có sơ đồ phân rã chức năng/biểu đồ gói.
-   [ ] Có biểu đồ Use Case tổng quan.
-   [ ] Đã bàn giao FR và actor cho thành viên 2.
-   [ ] Đã tạo bảng truy vết ban đầu.

### Phối hợp

-   [ ] Các quy tắc chưa rõ đã được ghi thành câu hỏi cụ thể.
-   [ ] Không tự chốt các quy tắc quan trọng ngoài thẩm quyền.
-   [ ] Tài liệu đã gửi đúng định dạng và đúng thư mục chung.
-   [ ] Có ghi phiên bản/ngày cập nhật để tránh dùng nhầm bản cũ.

------------------------------------------------------------------------

## 7. Cấu trúc thư mục đề xuất

``` text
member-1/
├── chapter-1-introduction.md
├── chapter-2-business-analysis.md
├── functional-requirements.md
├── non-functional-requirements.md
├── business-rules.md
├── function-decomposition.md
├── use-case-overview.md
└── requirements-traceability.md
```

Nếu nhóm viết báo cáo trực tiếp trong một file chung, vẫn nên giữ các
file nháp riêng trong quá trình làm việc và chuyển nội dung đã được
duyệt vào báo cáo chính.

------------------------------------------------------------------------

## 8. Quy ước chất lượng tài liệu

-   Dùng thống nhất một ngôn ngữ cho tên actor, Use Case và mã yêu cầu;
    có thể viết tiếng Việt và giữ thuật ngữ tiếng Anh trong ngoặc ở lần
    xuất hiện đầu tiên.
-   Không thay đổi mã FR sau khi các thành viên khác đã tham chiếu nếu
    không thông báo.
-   Mọi sơ đồ phải có tên, chú thích cần thiết và được nhắc đến trong
    phần thuyết minh.
-   Không dùng ảnh chụp sơ đồ mờ hoặc sơ đồ không thể đọc được khi đưa
    vào báo cáo.
-   Phân biệt rõ **yêu cầu đã xác nhận**, **đề xuất**, và **câu hỏi đang
    chờ quyết định**.
-   Mỗi thay đổi nghiệp vụ ảnh hưởng đến tính phí, quyền hạn, trạng thái
    xe hoặc luồng thuê/trả phải được thông báo cho nhóm trưởng và các
    thành viên 2--4.
-   Nội dung báo cáo phải phản ánh hệ thống nhóm thực sự phân tích/xây
    dựng, không mô tả tính năng không tồn tại như một kết quả đã hoàn
    thành.

------------------------------------------------------------------------

## 9. Tiêu chuẩn hoàn thành công việc của thành viên 1

Công việc được coi là hoàn thành khi:

1.  Chương 1 đáp ứng đủ các ý trong hướng dẫn môn học.
2.  Chương 2 có bản nghiệp vụ ngắn gọn, hoặc nhóm trưởng đã đồng ý lược
    bỏ do đây là chương tùy chọn.
3.  Danh mục FR/NFR được nhóm trưởng duyệt.
4.  Sơ đồ chức năng và Use Case tổng quan nhất quán với danh mục yêu
    cầu.
5.  Quy tắc nghiệp vụ quan trọng đã được xác nhận hoặc được ghi rõ là
    chưa quyết định.
6.  Thành viên 2 nhận được FR, actor và thuật ngữ để viết đặc tả Use
    Case.
7.  Có bảng truy vết để nhóm dùng khi tích hợp thiết kế và kiểm thử.
8.  Nhóm trưởng có thể đọc tài liệu và kiểm tra tiến độ mà không phải
    hỏi lại các nội dung nền tảng.

**Ưu tiên nếu thiếu thời gian:** Hoàn thành phạm vi + Chương 1 +
FR/NFR + Use Case tổng quan trước; tiếp theo làm bảng quy tắc nghiệp vụ
và bàn giao cho thành viên 2; cuối cùng hoàn thiện Chương 2 và bảng truy
vết. Không nên dành quá nhiều thời gian cho Chương 2 tùy chọn trong khi
yêu cầu chức năng chưa rõ.
