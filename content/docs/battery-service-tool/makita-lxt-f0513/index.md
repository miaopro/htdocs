---
title: "Battery Service Tool: Makita LXT IC dài – F0513"
description: "Quy trình dùng Quick Reset để lấy mã Err Code, phân tích nguyên nhân và dùng Full Unlock để xóa lỗi, mở khóa pin Makita LXT F0513."
tags: ["battery-service-tool", "makita-lxt", "f0513"]
type: docs
weight: 2
---

Quy trình xử lý pin **Makita LXT IC dài – F0513** gồm hai bước: lấy mã lỗi để xác định nguyên nhân, sau đó xóa lỗi và mở khóa pin.

> **Lưu ý an toàn:** Không tiếp tục sử dụng hoặc sạc nếu pin phồng, rò rỉ, có mùi lạ hoặc nóng bất thường. Nếu kết quả phân tích cho thấy lỗi cell hoặc phần cứng, cần kiểm tra và khắc phục nguyên nhân để tránh pin bị khóa lại.

> **Nguyên tắc bắt buộc:** Sau mỗi lần kết nối hoặc kết nối lại pin, phải chọn **Read Data** và chờ đọc thành công. Khi đó các nút Quick Reset và Full Unlock mới có thể thao tác.

## Bước 1 – Quick Reset và phân tích Err Code

1. Kết nối pin Makita LXT F0513 với Battery Service Tool.
2. Chọn **Read Data** và chờ thiết bị đọc dữ liệu thành công. Sau bước này, nút Quick Reset mới có thể thao tác.
3. Chọn **Reset Tools → Quick Reset**.
4. Sau khi thực hiện, màn hình thiết bị sẽ hiển thị mã **Err Code**.
5. Ghi lại chính xác mã Err Code đang hiển thị.
6. Mở [trang phân tích mã Err Code F0513](/f0513.html).
7. Nhập mã Err Code và chọn **Xem hướng xử lý**.
8. Đọc kết quả để xác định nguyên nhân khiến pin bị khóa.

## Bước 2 – Full Unlock

1. Quay lại Battery Service Tool.
2. Chọn **Read Data** và chờ thiết bị đọc dữ liệu thành công. Sau bước này, nút Full Unlock mới có thể thao tác.
3. Chọn **Reset Tools → Full Unlock**.
4. Chờ thiết bị thông báo hoàn tất.
5. Tháo pin khỏi thiết bị và chờ vài giây.
6. Kết nối lại pin, chọn **Read Data** và kiểm tra trạng thái.
7. Thử pin bằng bộ sạc Makita phù hợp.

**Full Unlock** hoàn tất quá trình xóa lỗi và mở khóa pin.

## Quy trình nhanh

```text
Read Data
   ↓
Quick Reset
   ↓
Lấy mã Err Code trên màn hình
   ↓
Nhập mã vào trang phân tích F0513
   ↓
Xác định nguyên nhân gây khóa
   ↓
Read Data
   ↓
Full Unlock
   ↓
Xóa lỗi và mở khóa hoàn tất
```
