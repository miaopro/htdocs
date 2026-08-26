---
title: "Battery Service Tool: Makita LXT thường"
description: "Hướng dẫn đọc dữ liệu, reset, mở khóa, khôi phục giao tiếp và ghi dữ liệu MSG cho pin Makita LXT thường (IC ngắn)."
tags: ["battery-service-tool", "makita-lxt"]
type: docs
weight: 1
---

Tài liệu này hướng dẫn xử lý pin **Makita LXT thường (IC ngắn, IC bé không phải loại IC dài to, F0513)** báo lỗi, bị khóa hoặc không nhận sạc bằng **Battery Service Tool**. Với bo mạch IC dài, xem [quy trình riêng cho F0513](../makita-lxt-f0513/).

> **Cảnh báo an toàn:** Pin lithium-ion có thể gây cháy, nổ khi đo kiểm và sửa chữa không đúng cách. Không thao tác với pack pin phồng, rò rỉ, biến dạng, quá nóng hoặc có cell hư hỏng rõ ràng. Luôn kiểm tra đúng cực kết nối, theo dõi nhiệt độ và không sạc pin khi không có người giám sát. Các chức năng phần mềm không thể sửa cell hoặc phần cứng bị hỏng.

> **Nguyên tắc bắt buộc:** Sau mỗi lần kết nối hoặc kết nối lại pin, phải chọn **Read Data** và chờ đọc thành công. Khi đó các nút chức năng như Quick Reset, Full Unlock, Charger Reconnect, Factory Reset, Write MSG, Set Cycles và Lock Test mới có thể thao tác.

## 1. Trước khi bắt đầu

1. Kết nối pin với Battery Service Tool bằng jack kết nối LXT đi kèm.
2. Chọn **Read Data** và chờ thiết bị đọc dữ liệu thành công.
3. Kiểm tra thông tin sơ bộ về trạng thái pin và phần cứng.
4. Nếu có vấn đề như lệch áp, đứt chân kết nối hoặc lỗi phần cứng khác, cần khắc phục trước khi thực hiện chức năng reset hoặc mở khóa.

## 2. Trình tự xử lý khuyến nghị

Thực hiện từ mức can thiệp thấp đến cao. Chỉ chuyển sang bước tiếp theo khi bước trước không khắc phục được lỗi.

| Thứ tự | Chức năng | Mục đích |
| ---: | --- | --- |
| 1 | **Read Data** | Đọc và ghi nhận trạng thái ban đầu |
| 2 | **Quick Reset** | Xóa lỗi ở mức ít can thiệp nhất |
| 3 | **Full Unlock** | Xóa trạng thái lỗi và mở khóa sâu hơn |
| 4 | **Charger Reconnect** | Khôi phục giao tiếp giữa pin và bộ sạc Makita |
| 5 | **Factory Reset** | Can thiệp sâu vào dữ liệu reset; ưu tiên **1. Min** |
| 6 | **Read MSG / Write MSG** | Sao chép dữ liệu tương thích từ một pin tốt |
| 7 | **Kiểm tra phần cứng** | Tìm lỗi cell, cảm biến, cầu chì, mối hàn và đường giao tiếp |

Sau mỗi lần tháo và kết nối lại pin với Battery Service Tool, phải chọn **Read Data** lần nữa trước khi chuyển sang chức năng tiếp theo.

## 3. Quick Reset

**Quick Reset** tương đương chức năng **Clear Errors** trên ứng dụng máy tính. Đây là lựa chọn nên thử đầu tiên vì thực hiện nhanh và ít ảnh hưởng đến dữ liệu đang lưu trong pin.

### Khi nào nên sử dụng?

- Pin mới xuất hiện lỗi hoặc đột nhiên không nhận sạc.
- Pin bị khóa tạm thời.
- Chưa xác định được chính xác nguyên nhân.
- Muốn thử phương án ít can thiệp trước khi dùng chức năng nâng cao.

### Cách thực hiện

1. Kết nối pin với thiết bị.
2. Chọn **Read Data** và chờ đọc thành công để các nút chức năng được kích hoạt.
3. Chọn **Reset Tools → Quick Reset**.
4. Chờ thiết bị thông báo hoàn tất.
5. Tháo pin, kết nối lại và thử bằng bộ sạc Makita.

Nếu lỗi vẫn còn, chuyển sang **Full Unlock**.

## 4. Full Unlock

**Full Unlock** xóa trạng thái lỗi và mở khóa pin ở mức sâu hơn Quick Reset.

### Khi nào nên sử dụng?

- Pin vẫn báo lỗi sau Quick Reset.
- Pin đang bị khóa và không hoạt động.
- Pin không nhận sạc trên bộ sạc Makita.
- Lỗi xuất hiện lại ngay sau Quick Reset.
- Quick Reset hoàn tất nhưng trạng thái pin không thay đổi.

### Cách thực hiện

1. Kết nối pin, chọn **Read Data** và chờ đọc thành công.
2. Chọn **Reset Tools → Full Unlock**.
3. Chờ thiết bị hoàn tất quá trình mở khóa.
4. Tháo pin, kết nối lại và thử bằng bộ sạc Makita.

Nếu thiết bị báo mở khóa thành công nhưng pin vẫn không giao tiếp hoặc không nhận sạc, tiếp tục với **Charger Reconnect**.

## 5. Charger Reconnect

Đường dẫn trên thiết bị: **Reset Tools → Advanced → Charger Reconnect**.

Chức năng này khôi phục trạng thái giao tiếp và nhận dạng giữa pin với bộ sạc Makita.

### Khi nào nên sử dụng?

- Pin đã mở khóa thành công nhưng vẫn không nhận sạc trên bộ sạc Makita.
- Pin sạc được bằng phương pháp khác nhưng không sạc được bằng bộ sạc Makita.
- Bộ sạc, ví dụ **DC18RC**, nháy đèn đỏ và xanh liên tục.
- Pin đã reset nhưng không hoàn tất quá trình nhận dạng với bộ sạc.
- Full Unlock thành công nhưng giao tiếp với bộ sạc vẫn chưa bình thường.

### Cách thực hiện

1. Kết nối pin, chọn **Read Data** và chờ đọc thành công.
2. Chọn **Reset Tools → Advanced → Charger Reconnect**.
3. Chờ thiết bị thông báo hoàn tất.
4. Tháo pin khỏi thiết bị và chờ vài giây.
5. Lắp pin vào bộ sạc Makita để kiểm tra.

### Nếu pin vẫn không nhận sạc

Không nên lặp lại thao tác reset quá nhiều lần. Ghi nhận trạng thái đèn báo và kiểm tra:

- Điện áp từng nhóm cell và độ lệch điện áp giữa các nhóm.
- Điểm tiếp xúc giữa bo mạch BMS và cell pin.
- Cầu chì và các linh kiện bảo vệ trên bo mạch.
- Mối hàn tại các đầu kết nối; kiểm tra nứt hoặc đứt ngầm.
- Cảm biến nhiệt độ.
- Đường tín hiệu giao tiếp với bộ sạc.
- Dây dẫn bên trong pack pin.
- Chân tiếp xúc bị oxy hóa, bẩn hoặc lỏng.
- Đường mạch hoặc linh kiện có dấu hiệu hư hỏng.

Nếu phần cứng đã được xác nhận an toàn và phù hợp, có thể tiếp tục với **Factory Reset**.

## 6. Factory Reset

Tên hiển thị trên thiết bị: **F.Reset**. Đây là chức năng can thiệp sâu hơn vào dữ liệu reset của pin và chỉ nên sử dụng sau khi Quick Reset, Full Unlock và Charger Reconnect không hiệu quả.

### Các chế độ

| Chế độ | Mô tả | Khuyến nghị |
| --- | --- | --- |
| **1. Min** | Reset ở mức tối thiểu | Luôn thử trước |
| **2. Std** | Áp dụng mẫu reset `0xC` | Chỉ dùng khi đã xác định mẫu phù hợp |
| **3. Max** | Áp dụng mẫu reset `0x9` | Chỉ dùng khi đã xác định mẫu phù hợp |

> **Cảnh báo:** Không chọn ngẫu nhiên **2. Std** hoặc **3. Max**. Dùng sai mẫu có thể làm dữ liệu không phù hợp, khiến pin hoạt động sai, không nhận sạc hoặc phát sinh lỗi khác. Nếu chưa xác định được mẫu reset, chỉ ưu tiên **1. Min**.

### Cách thực hiện

1. Kết nối pin, chọn **Read Data** và chờ đọc thành công.
2. Chọn **Reset Tools → Advanced**.
3. Chọn **F.Reset → 1. Min**, **2. Std** hoặc **3. Max** theo đúng loại bo mạch.
4. Chờ thiết bị báo hoàn tất.
5. Tháo pin, chờ vài giây rồi thử bằng bộ sạc Makita.

## 7. Read MSG / Write MSG

**Write MSG** ghi dữ liệu MSG từ một viên pin đang hoạt động bình thường sang viên pin cần sửa. Đây là phương án can thiệp sâu, chỉ dùng khi các chức năng reset thông thường không khắc phục được lỗi.

### Điều kiện tương thích

Pin nguồn và pin đích nên có:

- Cùng model.
- Cùng loại bo mạch.
- Cùng cấu hình cell.
- Cùng phiên bản phần cứng.
- Cấu trúc dữ liệu MSG tương thích.

### Bước 1 – Đọc dữ liệu từ pin tốt

1. Kết nối viên pin đang hoạt động tốt.
2. Chọn **Read Data** và chờ đọc thành công.
3. Chọn **Read MSG**.
4. Chờ thiết bị đọc và lưu dữ liệu MSG thành công.
5. Tháo viên pin tốt khỏi thiết bị.

### Bước 2 – Ghi dữ liệu sang pin cần sửa

1. Kết nối viên pin bị lỗi.
2. Chọn **Read Data** và chờ đọc thành công.
3. Chọn **Write MSG**.
4. Chờ thiết bị ghi dữ liệu thành công.
5. Tháo pin, kết nối lại rồi chọn **Read Data** để kiểm tra.
6. Thử pin trên bộ sạc Makita.

> **Cảnh báo:** Không ghi dữ liệu MSG của model khác sang pin cần sửa nếu chưa xác định chắc chắn tính tương thích.

## 8. Các chức năng khác

### Set Cycles

**Set Cycles** thay đổi giá trị số chu kỳ sạc/xả được lưu trong pin.

1. Kết nối pin, chọn **Read Data** và chờ đọc thành công.
2. Dùng nút mũi tên trái/phải tại mục **Set Cycles** để chọn giá trị.
3. Nhấn **Set Cycles** để ghi.
4. Chờ thiết bị thông báo hoàn tất.
5. Chọn **Read Data** lần nữa để xác nhận giá trị mới.

Việc thay đổi Cycles chỉ sửa dữ liệu được lưu, không phục hồi dung lượng thực tế hoặc tình trạng vật lý của cell.

### Lock Test

**Lock Test** đưa pin vào trạng thái khóa/lỗi được lựa chọn để kiểm tra, thử nghiệm hoặc chẩn đoán.

1. Kết nối pin, chọn **Read Data** và chờ đọc thành công.
2. Dùng nút mũi tên trái/phải tại mục **Lock** để chọn trạng thái.
3. Kiểm tra kỹ lựa chọn rồi nhấn **Lock: …**.
4. Chờ thiết bị thông báo hoàn tất.
5. Chọn **Read Data** lần nữa để kiểm tra trạng thái pin.

> **Cảnh báo:** Lock Test chỉ phục vụ thử nghiệm. Không sử dụng trên pin đang hoạt động bình thường nếu không có mục đích kiểm tra cụ thể.

## 9. Quy trình nhanh

```text
Read Data
   ↓
Quick Reset
   ↓ nếu chưa khắc phục
Read Data
   ↓
Full Unlock
   ↓ nếu đã mở khóa nhưng vẫn không nhận sạc
Read Data
   ↓
Charger Reconnect
   ↓ nếu vẫn chưa khắc phục
Read Data
   ↓
Factory Reset — ưu tiên 1. Min
   ↓ nếu có pin nguồn và dữ liệu tương thích
Kết nối pin tốt → Read Data → Read MSG
   ↓ kết nối pin cần sửa
Read Data → Write MSG
   ↓
Kiểm tra phần cứng
```

## Nguyên tắc cần nhớ

- Sau mỗi lần kết nối hoặc kết nối lại pin, luôn **Read Data** và chờ đọc thành công; các nút chức năng chỉ có thể thao tác sau bước này.
- Ghi lại trạng thái pin trước khi reset hoặc mở khóa.
- Bắt đầu từ chức năng ít can thiệp nhất.
- Không dùng Factory Reset **Std** hoặc **Max** nếu chưa xác định đúng mẫu dữ liệu.
- Không dùng Write MSG giữa các model pin không tương thích.
- Sau mỗi bước, tháo pin, kết nối lại và kiểm tra bằng bộ sạc Makita (có thể dùng lock check để kiểm tra trạng thái link).
- Nếu thao tác phần mềm báo thành công nhưng pin vẫn không hoạt động, chuyển sang kiểm tra phần cứng thay vì tiếp tục reset nhiều lần.
