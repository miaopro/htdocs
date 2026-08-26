---
title: "Battery Service Tool: Makita XGT"
description: "Quy trình Read Data và Full Unlock để xóa lỗi, mở khóa pin Makita XGT."
tags: ["battery-service-tool", "makita-xgt"]
type: docs
weight: 3
---

Pin **Makita XGT** chỉ sử dụng chức năng **Full Unlock**. Loại này không hiển thị Err Code và không có bước phân tích mã lỗi.

> **Lưu ý an toàn:** Không tiếp tục sử dụng hoặc sạc nếu pin phồng, rò rỉ, có mùi lạ hoặc nóng bất thường. Full Unlock chỉ xóa lỗi và mở khóa; chức năng này không khắc phục cell hoặc phần cứng bị hỏng.

> **Nguyên tắc bắt buộc:** Sau mỗi lần kết nối hoặc kết nối lại pin, phải chọn **Read Data** và chờ đọc thành công. Khi đó nút Full Unlock mới có thể thao tác.

## Quy trình Full Unlock

1. Kết nối pin Makita XGT với Battery Service Tool bằng jack phù hợp.
2. Chọn **Read Data** và chờ thiết bị đọc dữ liệu thành công.
3. Kiểm tra thiết bị đã nhận đúng loại pin Makita XGT. Sau bước Read Data, nút Full Unlock mới có thể thao tác.
4. Chọn **Reset Tools → Full Unlock**.
5. Chờ thiết bị thông báo quá trình hoàn tất. Không tháo pin trong khi thiết bị đang xử lý.
6. Tháo pin khỏi Battery Service Tool và chờ vài giây.
7. Kết nối lại pin với thiết bị.
8. Chọn **Read Data** lần nữa để kiểm tra trạng thái sau mở khóa.
9. Tháo pin và thử bằng bộ sạc Makita XGT phù hợp.

Nếu Read Data không thành công, nút Full Unlock sẽ chưa thể thao tác. Hãy kiểm tra lại jack kết nối, chân tiếp xúc và loại pin trước khi thử lại.

## Quy trình nhanh

```text
Kết nối pin Makita XGT
   ↓
Read Data
   ↓
Full Unlock
   ↓
Tháo pin và chờ vài giây
   ↓
Kết nối lại → Read Data
   ↓
Kiểm tra bằng bộ sạc Makita XGT
```
