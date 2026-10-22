# CHƯƠNG 2. PHÂN TÍCH NGHIỆP VỤ

**Phiên bản:** v0.1 — 2026-10-21 · **Trạng thái:** Draft (bản gọn — chương tùy chọn)

## 2.1. Cơ cấu tổ chức (vai trò nghiệp vụ)

| Vai trò | Trách nhiệm nghiệp vụ |
|---|---|
| Khách hàng (Customer) | Tạo/quản lý tài khoản, tra cứu bãi và xe, gửi/hủy yêu cầu thuê, theo dõi lượt thuê đang diễn ra và lịch sử thuê |
| Cư dân Ecopark (Resident) | Là **khách hàng có hồ sơ cư dân**; thực hiện mọi thao tác như khách hàng; được xét ưu đãi khi hồ sơ cư dân được xác minh |
| Nhân viên bãi xe (Parking Staff) | Xử lý yêu cầu thuê thuộc bãi được phân công; kiểm tra giấy tờ/điều kiện; giao xe; tiếp nhận xe trả và ghi nhận tình trạng xe; cập nhật trạng thái xe |
| Quản trị viên / Điều hành (Administrator) | Quản lý bãi, xe, tài khoản và dữ liệu vận hành; xem thống kê (và báo cáo, nhật ký nếu được đưa vào phạm vi) |

**Ghi chú mô hình hóa [Đề xuất]:** "Cư dân" không được tạo thành tác nhân độc lập; đây là một *loại hồ sơ / nhóm quyền lợi* của Khách hàng (thuộc tính "trạng thái xác minh cư dân"). Lý do: cư dân không có thao tác nghiệp vụ riêng khác khách hàng, chỉ khác ở cách tính phí. Chờ thống nhất với thành viên 2 (Q-01).

Người xác minh hồ sơ cư dân (nhân viên hay quản trị viên) chưa được xác định (Q-08).

## 2.2. Quy trình nghiệp vụ

Các sơ đồ dưới đây là lưu đồ nghiệp vụ dạng swimlane, mỗi làn tương ứng một vai trò. Các bước/nhánh có ký hiệu **(\*)** phụ thuộc quy tắc chưa chốt, được giữ ở dạng điều kiện tổng quát và sẽ chỉnh khi nhóm trưởng xác nhận.

### Hình 2.1. Quy trình A — Thuê xe

```mermaid
flowchart TB
  subgraph KH["Khách hàng"]
    A0([Bắt đầu]) --> A1{Đã có tài khoản?}
    A1 -- Chưa --> A2[Đăng ký tài khoản]
    A1 -- Có --> A3[Đăng nhập]
    A2 --> A3
    A3 --> A4[Tra cứu bãi và xe có thể thuê]
    A4 --> A5{Có xe phù hợp?}
    A5 -- Không --> A6([Kết thúc: không thuê])
    A5 -- Có --> A7[Chọn xe, thời lượng và gửi yêu cầu thuê]
  end
  subgraph HT["Hệ thống"]
    S1[Ghi nhận yêu cầu thuê<br/>trạng thái: Chờ bàn giao]
    S2[Cập nhật xe: Đang thuê<br/>Tạo lượt thuê, ghi thời điểm giao]
    S3[Cập nhật yêu cầu: Bị từ chối]
  end
  subgraph NV["Nhân viên bãi xe"]
    N1[Kiểm tra yêu cầu và thông tin giấy tờ]
    N2{Giấy tờ và điều kiện bàn giao hợp lệ? *}
    N3[Thu đặt cọc nếu quy định yêu cầu *]
    N4[Kiểm tra tình trạng xe và giao xe]
    N5[Thông báo lý do từ chối]
  end
  A7 --> S1 --> N1 --> N2
  N2 -- Hợp lệ --> N3 --> N4 --> S2 --> E1([Kết thúc: xe đã giao])
  N2 -- Không hợp lệ --> N5 --> S3 --> E2([Kết thúc: không giao xe])
```

Thuyết minh: Hình 2.1 mô tả từ khi khách hàng truy cập hệ thống tới khi xe được giao. Hai nhánh quan trọng là (1) không có xe phù hợp và (2) không đủ điều kiện bàn giao. Loại giấy tờ, việc thu đặt cọc và điều kiện từ chối chưa chốt (Q-04, Q-05). Khách hàng có thể hủy yêu cầu khi yêu cầu còn ở trạng thái *Chờ bàn giao* (FR-08) — nhánh này không vẽ để giữ sơ đồ dễ đọc.

### Hình 2.2. Quy trình B — Trả xe

```mermaid
flowchart TB
  subgraph KH["Khách hàng"]
    B0([Bắt đầu]) --> B1[Đưa xe đến bãi trả được chấp nhận *]
  end
  subgraph NV["Nhân viên bãi xe"]
    B2[Tìm lượt thuê đang hoạt động của xe]
    B3[Kiểm tra xe, ghi nhận tình trạng]
    B4[Thu tiền và hoàn cọc nếu có *]
  end
  subgraph HT["Hệ thống"]
    B5[Xác định thời lượng thuê thực tế]
    B6[Tính phí thuê theo biểu phí]
    B7{Trả muộn?}
    B8[Tính phụ thu trả muộn *]
    B9{Khách hàng là cư dân<br/>đã được xác minh?}
    B10[Áp dụng ưu đãi cư dân *]
    B11[Tạo phiếu thuê/trả]
    B12{Xe cần sửa chữa?}
    B13[Xe: Cần sửa chữa]
    B14[Xe: Sẵn sàng tại bãi nhận trả]
    B15[Kết thúc lượt thuê, lưu lịch sử]
  end
  B1 --> B2 --> B3 --> B5 --> B6 --> B7
  B7 -- Có --> B8 --> B9
  B7 -- Không --> B9
  B9 -- Có --> B10 --> B11
  B9 -- Không --> B11
  B11 --> B4 --> B12
  B12 -- Có --> B13 --> B15
  B12 -- Không --> B14 --> B15
  B15 --> B16([Kết thúc])
```

Thuyết minh: Hệ thống xác định thời lượng thuê từ thời điểm giao và thời điểm trả do nhân viên ghi nhận, sau đó tính phí, phụ thu và ưu đãi. Vị trí hiện tại của xe được cập nhật thành bãi nhận trả. Các quy tắc tính phụ thu, ưu đãi, hoàn cọc và việc trả khác bãi chưa chốt (Q-05 → Q-09). Có thể cần thêm phí bồi thường hư hỏng — chưa được đề cập trong đề bài nên không đưa vào sơ đồ (Q-15).

### Hình 2.3. Quy trình C — Quản lý đội xe

```mermaid
flowchart TB
  subgraph NVQT["Nhân viên bãi xe / Quản trị viên"]
    C0([Bắt đầu]) --> C1[Tra cứu xe theo mã, bãi hoặc trạng thái]
    C1 --> C2{Loại cập nhật}
    C2 -- Trạng thái --> C3[Chọn trạng thái mới, ví dụ Cần sửa chữa / Sẵn sàng]
    C2 -- Vị trí --> C4[Chọn bãi mới của xe]
  end
  subgraph HT["Hệ thống"]
    C5{Người dùng có quyền<br/>và chuyển trạng thái hợp lệ? *}
    C6[Cập nhật xe]
    C7[Lưu lịch sử thay đổi trạng thái/vị trí]
    C8[Báo lỗi, giữ nguyên dữ liệu]
  end
  subgraph QT["Quản trị viên"]
    C9[Tra cứu thống kê theo kỳ]
  end
  C3 --> C5
  C4 --> C5
  C5 -- Có --> C6 --> C7 --> C10([Kết thúc])
  C5 -- Không --> C8 --> C10
  C7 -.-> C9
```

Thuyết minh: Quy trình áp dụng khi cần ghi nhận xe hỏng, xe đã sửa xong hoặc điều chuyển xe giữa các bãi. Xe đang trong một lượt thuê không được chuyển sang trạng thái khác ngoài luồng trả xe (đề xuất BR-03, chờ xác nhận). Phạm vi bãi mà nhân viên được thao tác chưa chốt (Q-11). Dữ liệu lịch sử là đầu vào cho thống kê của quản trị viên.

## 2.3. Các lớp lĩnh vực (đối tượng nghiệp vụ)

Danh sách là đề xuất ban đầu, cần thống nhất tên với thành viên 3. Các đối tượng không nhất thiết tương ứng một-một với bảng CSDL hoặc lớp phần mềm.

| Đối tượng nghiệp vụ | Ý nghĩa |
|---|---|
| Khách hàng | Người sử dụng dịch vụ thuê xe, có tài khoản trong hệ thống |
| Hồ sơ cư dân | Thông tin dùng để xét điều kiện ưu đãi cư dân, gắn với một khách hàng, có trạng thái xác minh |
| Bãi xe | Địa điểm chứa và quản lý xe, có vị trí xác định |
| Xe đạp | Tài sản có mã định danh duy nhất, trạng thái và bãi hiện tại |
| Yêu cầu thuê | Yêu cầu do khách hàng gửi trước khi nhân viên bàn giao xe |
| Lượt thuê | Một phiên thuê từ lúc giao xe đến lúc trả xe |
| Biểu phí | Mức giá thuê, quy tắc phụ thu và ưu đãi đang áp dụng |
| Phiếu thuê/trả | Thông tin tổng kết lượt thuê và các khoản phí |
| Nhân viên | Người xử lý giao/nhận xe tại bãi được phân công |
| Quản trị viên | Người quản lý dữ liệu vận hành và xem thống kê |
| Nhật ký trạng thái xe | Lịch sử thay đổi trạng thái/vị trí xe |
| Báo cáo thống kê | Dữ liệu tổng hợp theo kỳ và tiêu chí quản lý |

Quan hệ nghiệp vụ chính (mức khái niệm):

- Một **Khách hàng** có thể có tối đa một **Hồ sơ cư dân**.
- Một **Khách hàng** gửi nhiều **Yêu cầu thuê**; một **Yêu cầu thuê** được bàn giao sẽ sinh ra một **Lượt thuê**.
- Một **Lượt thuê** gắn với một **Xe đạp**, một bãi giao, một bãi trả và một **Phiếu thuê/trả**.
- Một **Bãi xe** chứa nhiều **Xe đạp**; một **Nhân viên** được phân công cho một hoặc nhiều bãi (Q-11).
- Một **Xe đạp** có nhiều bản ghi **Nhật ký trạng thái xe**.
