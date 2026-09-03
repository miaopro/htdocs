---
title: "Battery Service Tool: Cập nhật firmware qua Wi-Fi OTA"
description: "Hướng dẫn kết nối Wi-Fi, kiểm tra phiên bản và cập nhật firmware OTA cho Battery Service Tool."
tags: ["battery-service-tool", "firmware", "ota", "wifi"]
type: docs
weight: 5
---

Battery Service Tool hỗ trợ cập nhật firmware qua Wi-Fi OTA (Over-the-Air), không cần kết nối thiết bị với máy tính. Thiết bị sẽ tự kiểm tra phiên bản mới, tải firmware từ máy chủ và khởi động lại sau khi cập nhật thành công.

> **Cảnh báo:** Tuyệt đối không tắt nguồn, rút cáp nguồn hoặc khởi động lại Battery Service Tool trong khi thiết bị đang tải và ghi firmware. Mất nguồn ở giai đoạn này có thể làm quá trình cập nhật thất bại.

## Chuẩn bị trước khi cập nhật

Hãy bảo đảm:

- Battery Service Tool được cấp nguồn ổn định.
- Có mạng Wi-Fi **2.4 GHz** đang kết nối Internet.
- Biết chính xác tên và mật khẩu Wi-Fi.
- Có điện thoại để cấu hình Wi-Fi nếu thiết bị chưa lưu mạng.

## Quy trình nhanh

```text
Khởi động Battery Service Tool
   ↓
Service Mode
   ↓
Kết nối Wi-Fi 2.4 GHz
   ↓
Kiểm tra phiên bản
   ↓
Start update
   ↓
Chờ cập nhật 100% và thiết bị tự khởi động lại
   ↓
Kiểm tra phiên bản mới
```

## Bước 1: Vào chế độ cập nhật

1. Khởi động Battery Service Tool và chờ màn hình chính xuất hiện.
2. Nhấn **Service Mode**.
3. Tại màn hình **Software Information**, kiểm tra các thông tin:

   - Phiên bản firmware hiện tại.
   - Thông tin kích hoạt.
   - Trạng thái kết nối Wi-Fi.
   - Phiên bản firmware mới nhất.

Khi vào Service Mode, thiết bị sẽ tạm dừng các chức năng giao tiếp với pin và bắt đầu kết nối Wi-Fi.

## Bước 2: Kết nối Wi-Fi

### Thiết bị đã lưu Wi-Fi

Battery Service Tool sẽ tự động kết nối lại mạng đã lưu. Chờ đến khi màn hình hiển thị:

```text
WiFi: Online <tên Wi-Fi>
```

Sau khi kết nối Internet, thiết bị sẽ tự động kiểm tra phiên bản firmware mới.

### Thiết bị chưa cấu hình hoặc không kết nối được Wi-Fi

Khi màn hình hiển thị:

```text
Setup: MeV-BST
```

hãy thực hiện các bước sau trên điện thoại:

1. Mở **Cài đặt Wi-Fi**.
2. Kết nối với mạng **MeV-BST**. Mạng cấu hình này không có mật khẩu.
3. Nếu điện thoại cảnh báo mạng không có Internet, chọn tiếp tục duy trì kết nối.
4. Chờ trang cấu hình Wi-Fi tự động mở. Nếu trang không xuất hiện, mở trình duyệt và truy cập `http://192.168.4.1`.
5. Nhấn **Configure WiFi**.
6. Chọn mạng Wi-Fi 2.4 GHz cần sử dụng.
7. Nhập đúng mật khẩu Wi-Fi.
8. Nhấn **Save/Connect** và chờ thiết bị kết nối.
9. Xác nhận màn hình Battery Service Tool hiển thị:

   ```text
   WiFi: Online <tên Wi-Fi>
   ```

> **Lưu ý:** Điểm phát `MeV-BST` chỉ hoạt động trong khoảng **5 phút**. Nếu hết thời gian, nhấn **Exit Update Mode**, chờ thiết bị khởi động lại rồi vào **Service Mode** lần nữa.

## Bước 3: Kiểm tra phiên bản firmware

Sau khi kết nối Internet, Battery Service Tool tự lấy thông tin phiên bản từ máy chủ.

Nếu thiết bị đang dùng phiên bản mới nhất, màn hình hiển thị:

```text
Latest Version: ...
Status: Up to date
```

Trong trường hợp này, nút cập nhật không được kích hoạt và bạn không cần thực hiện thêm thao tác nào.

Nếu có firmware mới, màn hình hiển thị:

```text
Latest Version: ...
Status: Update available
```

Nút **Start update** sẽ được kích hoạt.

> Trong lần kết nối đầu tiên, thiết bị có thể tự khởi động lại để đồng bộ thông tin kích hoạt. Sau khi máy khởi động xong, hãy vào lại **Service Mode** để tiếp tục kiểm tra phiên bản.

## Bước 4: Tiến hành cập nhật

1. Nhấn **Start update**.
2. Chờ thiết bị kết nối máy chủ, tải và ghi firmware. Màn hình sẽ lần lượt hiển thị các trạng thái tương tự:

   ```text
   Connecting to server...
   Requesting firmware...
   Writing firmware...
   Updating firmware...
   Progress: xx%
   ```

3. Giữ nguyên nguồn điện và kết nối Wi-Fi cho đến khi quá trình hoàn tất.

Trong lúc cập nhật:

- Không tắt nguồn hoặc rút cáp nguồn.
- Không khởi động lại thiết bị.
- Không ngắt hoặc thay đổi mạng Wi-Fi.
- Không thao tác với các nút khác.

Các nút **Start update** và **Exit Update Mode** sẽ bị khóa trong khi firmware đang được tải và ghi. Đây là hoạt động bình thường của thiết bị.

## Bước 5: Hoàn tất và kiểm tra

Khi cập nhật thành công, màn hình hiển thị:

```text
Update successful!
Rebooting...
```

Thiết bị sẽ tự khởi động lại sau khoảng 1,5 giây. Sau khi màn hình chính xuất hiện:

1. Kiểm tra số phiên bản firmware hiển thị trên thiết bị.
2. Vào lại **Service Mode**.
3. Xác nhận màn hình hiển thị:

   ```text
   Status: Up to date
   ```

Firmware của Battery Service Tool đã được cập nhật thành công khi phiên bản mới hiển thị đúng và trạng thái là **Up to date**.

## Xử lý sự cố

| Hiện tượng | Cách xử lý |
| --- | --- |
| Không thấy mạng `MeV-BST` | Nhấn **Exit Update Mode**, chờ thiết bị khởi động lại rồi vào **Service Mode** lần nữa. |
| Trang cấu hình Wi-Fi không tự mở | Giữ điện thoại kết nối với `MeV-BST`, mở trình duyệt và truy cập `http://192.168.4.1`. |
| Hiển thị `Not found` | Kiểm tra router đang bật và bảo đảm mạng được chọn là Wi-Fi 2.4 GHz. |
| Hiển thị `Failed` | Kiểm tra và nhập lại đúng mật khẩu Wi-Fi. |
| Dừng ở `Checking...` | Kiểm tra kết nối Internet. Nếu vẫn không tiếp tục, thoát Update Mode rồi thực hiện lại. |
| Xuất hiện lỗi HTTP, download hoặc write | Giữ nguyên nguồn cấp, kiểm tra Internet rồi nhấn **Start update** để thử lại khi nút được mở. |
| Phần trăm cập nhật đang hiển thị nhưng chưa hoàn tất | Tiếp tục chờ và tuyệt đối không tắt nguồn thiết bị. |

