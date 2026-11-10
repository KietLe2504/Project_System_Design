# Ecopark Bicycle Parking · Thành viên 2

Bộ tài liệu dự thảo cho Chương 3.1.2 và phần sơ đồ trình tự của Chương 4.3. Mã FR và UC theo tài liệu Thành viên 1 tại commit `62dbda6`. Các quy tắc nghiệp vụ và phương án mới trong cột phản hồi vẫn có trạng thái `Open`. [Yêu cầu chức năng](../member-1/functional-requirements.md) · [Sơ đồ tổng quan](../member-1/use-case-overview.md) · [Quy tắc nghiệp vụ](../member-1/business-rules.md)

| Tài liệu | Nội dung |
|---|---|
| [Danh mục ca sử dụng](use-case-catalog.md) | 20 mã UC theo sơ đồ tổng quan, gồm UC019–UC020 chờ phạm vi |
| [Đặc tả ca sử dụng](use-case-specifications.md) | Luồng, nhánh lỗi và dữ liệu bàn giao cho Thành viên 3 |
| [Thuật ngữ và trạng thái](use-case-glossary.md) | Từ vựng, chuyển trạng thái xe, yêu cầu, lượt thuê và hồ sơ cư dân |
| [Ma trận FR → UC → kiểm thử](fr-uc-test-traceability.md) | Kịch bản và kết quả mong đợi để Thành viên 4 cụ thể hóa |
| [Quy tắc cần xác nhận](open-business-rules.md) | Đối chiếu FR/BR với ghi chú mới và các điểm cần nhóm chốt |

## Sơ đồ hoạt động

| Quy trình | Bản xem | Tệp nguồn |
|---|---|---|
| Gửi yêu cầu, hủy và bàn giao xe | [SVG](activity-diagrams/rental-handover.svg) | [PlantUML](activity-diagrams/rental-handover.puml) |
| Ghi nhận trả xe, tính phí và lập phiếu | [SVG](activity-diagrams/return-payment.svg) | [PlantUML](activity-diagrams/return-payment.puml) |
| Khai báo và xác minh cư dân | [SVG](activity-diagrams/resident-verification.svg) | [PlantUML](activity-diagrams/resident-verification.puml) |

## Sơ đồ trình tự dự thảo

| Ca sử dụng | Bản xem | Tệp nguồn |
|---|---|---|
| UC007 · Gửi yêu cầu thuê | [SVG](sequence-diagrams/rental-request-design.svg) | [PlantUML](sequence-diagrams/rental-request-design.puml) |
| UC010 · Bàn giao xe | [SVG](sequence-diagrams/rental-handover-design.svg) | [PlantUML](sequence-diagrams/rental-handover-design.puml) |
| UC011–UC012 · Ghi nhận trả xe và tính phí | [SVG](sequence-diagrams/return-payment-design.svg) | [PlantUML](sequence-diagrams/return-payment-design.puml) |

Lifeline hiện dùng vai trò thiết kế logic. Thành viên 3 xác nhận ánh xạ sang kiến trúc và biểu đồ lớp trước khi ghép vào Chương 4.3.

Nhóm trưởng chốt các câu hỏi theo mã Q của Thành viên 1. Sau khi chốt, cập nhật đồng thời FR/BR, nhánh UC, sơ đồ và ca kiểm thử liên quan. Các kịch bản phụ thuộc chính sách được đánh dấu trong ma trận.
