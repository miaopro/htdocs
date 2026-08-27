---
title: "Battery Service Tool: HiKOKI"
description: "Quy trình Read Data, Full Unlock và bảng tra cứu mã lỗi pin HiKOKI."
tags: ["battery-service-tool", "hikoki"]
type: docs
weight: 4
---

Pin **HiKOKI** chỉ sử dụng chức năng **Full Unlock**. Loại này không hiển thị mã lỗi chi tiết; sau khi **Read Data**, màn hình chỉ hiển thị hai cờ trạng thái **Err** (lỗi) và **Fuse** (cầu chì).

> **Lưu ý an toàn:** Không tiếp tục sử dụng hoặc sạc nếu pin phồng, rò rỉ, có mùi lạ hoặc nóng bất thường. Full Unlock chỉ xóa lỗi và mở khóa; chức năng này không khắc phục cell hoặc phần cứng bị hỏng.

> **Nguyên tắc bắt buộc:** Sau mỗi lần kết nối hoặc kết nối lại pin, phải chọn **Read Data** và chờ đọc thành công. Khi đó nút Full Unlock mới có thể thao tác.

## Quy trình Full Unlock

1. Kết nối pin HiKOKI với Battery Service Tool bằng jack phù hợp.
2. Chọn **Read Data** và chờ thiết bị đọc dữ liệu thành công.
3. Kiểm tra thiết bị đã nhận đúng loại pin HiKOKI. Sau bước Read Data, nút Full Unlock mới có thể thao tác.
4. Chọn **Reset Tools → Full Unlock**.
5. Chờ thiết bị thông báo quá trình hoàn tất. Không tháo pin trong khi thiết bị đang xử lý.
6. Tháo pin khỏi Battery Service Tool và chờ vài giây.
7. Kết nối lại pin với thiết bị.
8. Chọn **Read Data** lần nữa để kiểm tra trạng thái sau mở khóa.
9. Tháo pin và thử bằng bộ sạc HiKOKI phù hợp.

Nếu Read Data không thành công, nút Full Unlock sẽ chưa thể thao tác. Hãy kiểm tra lại jack kết nối, chân tiếp xúc và loại pin trước khi thử lại.

## Quy trình nhanh

```text
Kết nối pin HiKOKI
   ↓
Read Data
   ↓
Full Unlock
   ↓
Tháo pin và chờ vài giây
   ↓
Kết nối lại → Read Data
   ↓
Kiểm tra bằng bộ sạc HiKOKI
```

## Cách đọc trạng thái lỗi và cầu chì

Trong đó, **Y** nghĩa là trạng thái đang được ghi nhận, còn **N** nghĩa là không ghi nhận trạng thái đó.

| Trạng thái hiển thị | Ý nghĩa |
| --- | --- |
| `Err:Y Fuse:N` | Pin đang ghi nhận lỗi, nhưng cầu chì chưa kích hoạt. |
| `Err:N Fuse:Y` | Không ghi nhận cờ lỗi, nhưng cầu chì đã kích hoạt. |
| `Err:Y Fuse:Y` | Pin vừa ghi nhận lỗi vừa kích hoạt cầu chì; pin đang bị khóa. |
| `Err:N Fuse:N` | Không ghi nhận lỗi, cầu chì chưa kích hoạt; pin không bị khóa. |

## Danh mục bảng mã lỗi

Bảng dưới đây dùng để tra cứu và đối chiếu mã lỗi HiKOKI. Cột **Fatal** cho biết lỗi có được xếp vào nhóm nghiêm trọng hay không; **No\*** là lỗi không được đánh dấu Fatal nhưng vẫn cần đặc biệt thận trọng vì liên quan đến tình trạng xả quá sâu nghiêm trọng.

| Code | Standardized name | Diễn giải tiếng Việt | Nhóm | Đối tượng | Fatal |
| --- | --- | --- | --- | --- | --- |
| `0x01` | Upper Side Over-Charge | Quá sạc phía Upper | Over-Charge | Upper | No |
| `0x02` | Lower Side Cell 1 Over-Charge | Cell 1 phía Lower quá sạc | Over-Charge | Lower C1 | No |
| `0x03` | Lower Side Cell 2 Over-Charge | Cell 2 phía Lower quá sạc | Over-Charge | Lower C2 | No |
| `0x04` | Lower Side Cell 3 Over-Charge | Cell 3 phía Lower quá sạc | Over-Charge | Lower C3 | No |
| `0x05` | Lower Side Cell 4 Over-Charge | Cell 4 phía Lower quá sạc | Over-Charge | Lower C4 | No |
| `0x06` | Lower Side Cell 5 Over-Charge | Cell 5 phía Lower quá sạc | Over-Charge | Lower C5 | No |
| `0x08` | Over-Charge 2 | Quá sạc 2 | Over-Charge | Pack | **Yes** |
| `0x09` | Over-Charge 2 without Over-Charge 1 | Quá sạc 2 nhưng không có Over-Charge 1 | Over-Charge | Pack | **Yes** |
| `0x0B` | Upper Side High Temperature During Charge | Phía Upper quá nhiệt khi sạc | Temperature | Upper | No |
| `0x0C` | Lower Side High Temperature During Charge | Phía Lower quá nhiệt khi sạc | Temperature | Lower | No |
| `0x0E` | Partial Charge - Upper C Bank | Hạn chế sạc Upper C Bank | Charge Control | Upper | No |
| `0x0F` | Partial Charge - Lower C Bank | Hạn chế sạc Lower C Bank | Charge Control | Lower | No |
| `0x10` | Partial Charge - Upper (-) Bank | Hạn chế sạc Upper (-) Bank | Charge Control | Upper | No |
| `0x11` | Partial Charge - Lower (-) Bank | Hạn chế sạc Lower (-) Bank | Charge Control | Lower | No |
| `0x13` | Charge Over-Current | Quá dòng khi sạc | Current | Pack | No |
| `0x15` | Upper Side Abnormal Cell | Cell/phía Upper bất thường | Cell | Upper | No |
| `0x16` | Lower Side Cell 1 Abnormal | Cell 1 phía Lower bất thường | Cell | Lower C1 | No |
| `0x17` | Lower Side Cell 2 Abnormal | Cell 2 phía Lower bất thường | Cell | Lower C2 | No |
| `0x18` | Lower Side Cell 3 Abnormal | Cell 3 phía Lower bất thường | Cell | Lower C3 | No |
| `0x19` | Lower Side Cell 4 Abnormal | Cell 4 phía Lower bất thường | Cell | Lower C4 | No |
| `0x1A` | Lower Side Cell 5 Abnormal | Cell 5 phía Lower bất thường | Cell | Lower C5 | No |
| `0x1C` | Upper Side Over-Discharge 1 | Phía Upper xả quá mức 1 | Over-Discharge | Upper | No |
| `0x1D` | Lower Side Cell 1 Over-Discharge 1 | Cell 1 phía Lower xả quá mức 1 | Over-Discharge | Lower C1 | No |
| `0x1E` | Lower Side Cell 2 Over-Discharge 1 | Cell 2 phía Lower xả quá mức 1 | Over-Discharge | Lower C2 | No |
| `0x1F` | Lower Side Cell 3 Over-Discharge 1 | Cell 3 phía Lower xả quá mức 1 | Over-Discharge | Lower C3 | No |
| `0x20` | Lower Side Cell 4 Over-Discharge 1 | Cell 4 phía Lower xả quá mức 1 | Over-Discharge | Lower C4 | No |
| `0x21` | Lower Side Cell 5 Over-Discharge 1 | Cell 5 phía Lower xả quá mức 1 | Over-Discharge | Lower C5 | No |
| `0x22` | Upper Side Over-Discharge 2 | Phía Upper xả quá mức 2 | Over-Discharge | Upper | No |
| `0x23` | Lower Side Cell 1 Over-Discharge 2 | Cell 1 phía Lower xả quá mức 2 | Over-Discharge | Lower C1 | No |
| `0x24` | Lower Side Cell 2 Over-Discharge 2 | Cell 2 phía Lower xả quá mức 2 | Over-Discharge | Lower C2 | No |
| `0x25` | Lower Side Cell 3 Over-Discharge 2 | Cell 3 phía Lower xả quá mức 2 | Over-Discharge | Lower C3 | No |
| `0x26` | Lower Side Cell 4 Over-Discharge 2 | Cell 4 phía Lower xả quá mức 2 | Over-Discharge | Lower C4 | No |
| `0x27` | Lower Side Cell 5 Over-Discharge 2 | Cell 5 phía Lower xả quá mức 2 | Over-Discharge | Lower C5 | No |
| `0x28` | Over-Discharge 3 | Xả quá mức 3 | Over-Discharge | Pack | No |
| `0x29` | Over-Discharge 4 | Xả quá mức 4 | Over-Discharge | Pack | No |
| `0x2A` | Over-Discharge 5 | Xả quá mức 5 | Over-Discharge | Pack | No |
| `0x2B` | Over-Discharge 6 | Xả quá mức 6 | Over-Discharge | Pack | No |
| `0x33` | Upper Side High Temperature During Discharge | Phía Upper quá nhiệt khi xả | Temperature | Upper | No |
| `0x34` | Lower Side High Temperature During Discharge | Phía Lower quá nhiệt khi xả | Temperature | Lower | No |
| `0x35` | Upper Side Temperature 60°C Event | Sự kiện nhiệt độ Upper đạt 60°C | Temperature History | Upper | No |
| `0x36` | Upper Side Temperature 65°C Event | Sự kiện nhiệt độ Upper đạt 65°C | Temperature History | Upper | No |
| `0x37` | Upper Side Temperature 70°C Event | Sự kiện nhiệt độ Upper đạt 70°C | Temperature History | Upper | No |
| `0x38` | Upper Side Temperature 75°C Event | Sự kiện nhiệt độ Upper đạt 75°C | Temperature History | Upper | No |
| `0x39` | Lower Side Temperature 60°C Event | Sự kiện nhiệt độ Lower đạt 60°C | Temperature History | Lower | No |
| `0x3A` | Lower Side Temperature 65°C Event | Sự kiện nhiệt độ Lower đạt 65°C | Temperature History | Lower | No |
| `0x3B` | Lower Side Temperature 70°C Event | Sự kiện nhiệt độ Lower đạt 70°C | Temperature History | Lower | No |
| `0x3C` | Lower Side Temperature 75°C Event | Sự kiện nhiệt độ Lower đạt 75°C | Temperature History | Lower | No |
| `0x43` | Upper Bank Thermistor Open | Hở cảm biến nhiệt Upper Bank | Sensor | Upper | No |
| `0x44` | Lower Bank Thermistor Open | Hở cảm biến nhiệt Lower Bank | Sensor | Lower | No |
| `0x45` | Upper Bank Thermistor Short | Chập cảm biến nhiệt Upper Bank | Sensor | Upper | No |
| `0x46` | Lower Bank Thermistor Short | Chập cảm biến nhiệt Lower Bank | Sensor | Lower | No |
| `0x48` | Current Detection Error | Lỗi phát hiện/đo dòng | Detection | Current Sense | No |
| `0x49` | Cell Voltage Detection Error | Lỗi phát hiện/đo điện áp cell | Detection | Cell Sense | No |
| `0x4A` | VIN12 Voltage Detection Error | Lỗi phát hiện điện áp VIN12 | Detection | VIN12 | No |
| `0x4B` | Thermistor Resistance Detection Error | Lỗi phát hiện điện trở nhiệt | Detection | Thermistor | No |
| `0x4C` | Upper Bank Voltage Detection Error | Lỗi phát hiện điện áp Upper Bank | Detection | Upper | No |
| `0x4E` | Bank Voltage Imbalance - Lower > Upper | Điện áp Lower lớn hơn Upper bất thường | Balance | Bank | No |
| `0x4F` | Bank Voltage Imbalance - Lower < Upper | Điện áp Lower thấp hơn Upper bất thường | Balance | Bank | No |
| `0x50` | Severe Balance Error | Mất cân bằng nghiêm trọng | Balance | Pack | No |
| `0x52` | Temperature Imbalance - Lower > Upper | Nhiệt độ Lower cao hơn Upper bất thường | Temperature Balance | Bank | No |
| `0x53` | Temperature Imbalance - Lower < Upper | Nhiệt độ Lower thấp hơn Upper bất thường | Temperature Balance | Bank | No |
| `0x55` | Cell Imbalance | Cell mất cân bằng | Balance | Cells | No |
| `0x59` | Abnormally High Temperature | Nhiệt độ cao bất thường | Temperature | Pack | No |
| `0x5A` | Extreme Over-Discharge | Xả quá sâu nghiêm trọng | Over-Discharge | Pack | No\* |
| `0x65` | Upper Side Over-Charge 1 | Phía Upper quá sạc 1 | Over-Charge | Upper | No |
| `0x66` | Lower Side Cell 1 Over-Charge 1 | Cell 1 phía Lower quá sạc 1 | Over-Charge | Lower C1 | No |
| `0x67` | Lower Side Cell 2 Over-Charge 1 | Cell 2 phía Lower quá sạc 1 | Over-Charge | Lower C2 | No |
| `0x68` | Lower Side Cell 3 Over-Charge 1 | Cell 3 phía Lower quá sạc 1 | Over-Charge | Lower C3 | No |
| `0x69` | Lower Side Cell 4 Over-Charge 1 | Cell 4 phía Lower quá sạc 1 | Over-Charge | Lower C4 | No |
| `0x6A` | Lower Side Cell 5 Over-Charge 1 | Cell 5 phía Lower quá sạc 1 | Over-Charge | Lower C5 | No |
| `0x6C` | Over-Charge 2 | Quá sạc 2 | Over-Charge | Pack | **Yes** |
| `0x6D` | Over-Charge 2 without Over-Charge 1 | Quá sạc 2 nhưng không có Over-Charge 1 | Over-Charge | Pack | **Yes** |
| `0x80` | Upper Side Over-Discharge 1 | Phía Upper xả quá mức 1 | Over-Discharge | Upper | No |
| `0x81` | Lower Side Cell 1 Over-Discharge 1 | Cell 1 phía Lower xả quá mức 1 | Over-Discharge | Lower C1 | No |
| `0x82` | Lower Side Cell 2 Over-Discharge 1 | Cell 2 phía Lower xả quá mức 1 | Over-Discharge | Lower C2 | No |
| `0x83` | Lower Side Cell 3 Over-Discharge 1 | Cell 3 phía Lower xả quá mức 1 | Over-Discharge | Lower C3 | No |
| `0x84` | Lower Side Cell 4 Over-Discharge 1 | Cell 4 phía Lower xả quá mức 1 | Over-Discharge | Lower C4 | No |
| `0x85` | Lower Side Cell 5 Over-Discharge 1 | Cell 5 phía Lower xả quá mức 1 | Over-Discharge | Lower C5 | No |
| `0x86` | Upper Side Over-Discharge 2 | Phía Upper xả quá mức 2 | Over-Discharge | Upper | No |
| `0x87` | Lower Side Cell 1 Over-Discharge 2 | Cell 1 phía Lower xả quá mức 2 | Over-Discharge | Lower C1 | No |
| `0x88` | Lower Side Cell 2 Over-Discharge 2 | Cell 2 phía Lower xả quá mức 2 | Over-Discharge | Lower C2 | No |
| `0x89` | Lower Side Cell 3 Over-Discharge 2 | Cell 3 phía Lower xả quá mức 2 | Over-Discharge | Lower C3 | No |
| `0x8A` | Lower Side Cell 4 Over-Discharge 2 | Cell 4 phía Lower xả quá mức 2 | Over-Discharge | Lower C4 | No |
| `0x8B` | Lower Side Cell 5 Over-Discharge 2 | Cell 5 phía Lower xả quá mức 2 | Over-Discharge | Lower C5 | No |
| `0x8C` | Over-Discharge 3 | Xả quá mức 3 | Over-Discharge | Pack | No |
| `0x8D` | Over-Discharge 4 | Xả quá mức 4 | Over-Discharge | Pack | No |
| `0x8E` | Over-Discharge 5 | Xả quá mức 5 | Over-Discharge | Pack | No |
| `0x8F` | Over-Discharge 6 | Xả quá mức 6 | Over-Discharge | Pack | No |
| `0x90` | 18V Over-Current | Quá dòng chế độ 18V | Current | 18V | No |
| `0x91` | MC-less Over-Current 1 | Quá dòng MC-less 1 | Current | Pack | No |
| `0x92` | MC-less Over-Current 2 | Quá dòng MC-less 2 | Current | Pack | No |
| `0x93` | Abnormal Current | Dòng điện bất thường | Current | Pack | No |
| `0x94` | High-Load Over-Current 1 | Quá dòng do tải nặng 1 | Current | Pack | No |
| `0x95` | High-Load Over-Current 2 | Quá dòng do tải nặng 2 | Current | Pack | No |
| `0x97` | Upper Side High Temperature During Discharge | Phía Upper quá nhiệt khi xả | Temperature | Upper | No |
| `0x98` | Lower Side High Temperature During Discharge | Phía Lower quá nhiệt khi xả | Temperature | Lower | No |
| `0x99` | Upper Side Temperature 60°C Event | Sự kiện Upper đạt 60°C | Temperature History | Upper | No |
| `0x9A` | Upper Side Temperature 65°C Event | Sự kiện Upper đạt 65°C | Temperature History | Upper | No |
| `0x9B` | Upper Side Temperature 70°C Event | Sự kiện Upper đạt 70°C | Temperature History | Upper | No |
| `0x9C` | Upper Side Temperature 75°C Event | Sự kiện Upper đạt 75°C | Temperature History | Upper | No |
| `0x9D` | Lower Side Temperature 60°C Event | Sự kiện Lower đạt 60°C | Temperature History | Lower | No |
| `0x9E` | Lower Side Temperature 65°C Event | Sự kiện Lower đạt 65°C | Temperature History | Lower | No |
| `0x9F` | Lower Side Temperature 70°C Event | Sự kiện Lower đạt 70°C | Temperature History | Lower | No |
| `0xA0` | Lower Side Temperature 75°C Event | Sự kiện Lower đạt 75°C | Temperature History | Lower | No |
| `0xA2` | Partial Charge - Upper C Bank | Hạn chế sạc Upper C Bank | Charge Control | Upper | No |
| `0xA3` | Partial Charge - Lower C Bank | Hạn chế sạc Lower C Bank | Charge Control | Lower | No |
| `0xA4` | Partial Charge - Upper (-) Bank | Hạn chế sạc Upper (-) Bank | Charge Control | Upper | No |
| `0xA5` | Partial Charge - Lower (-) Bank | Hạn chế sạc Lower (-) Bank | Charge Control | Lower | No |
| `0xA7` | Upper Bank Thermistor Open | Hở cảm biến nhiệt Upper Bank | Sensor | Upper | No |
| `0xA8` | Lower Bank Thermistor Open | Hở cảm biến nhiệt Lower Bank | Sensor | Lower | No |
| `0xA9` | Upper Bank Thermistor Short | Chập cảm biến nhiệt Upper Bank | Sensor | Upper | No |
| `0xAA` | Lower Bank Thermistor Short | Chập cảm biến nhiệt Lower Bank | Sensor | Lower | No |
| `0xAC` | Current Detection Error | Lỗi phát hiện/đo dòng | Detection | Current Sense | No |
| `0xAD` | Cell Voltage Detection Error | Lỗi phát hiện/đo điện áp cell | Detection | Cell Sense | No |
| `0xAE` | VIN12 Voltage Detection Error | Lỗi phát hiện điện áp VIN12 | Detection | VIN12 | No |
| `0xAF` | Thermistor Resistance Detection Error | Lỗi phát hiện điện trở nhiệt | Detection | Thermistor | No |
| `0xB0` | Upper Bank Voltage Detection Error | Lỗi phát hiện điện áp Upper Bank | Detection | Upper | No |
| `0xB2` | Bank Voltage Imbalance - Lower > Upper | Điện áp Lower > Upper bất thường | Balance | Bank | No |
| `0xB3` | Bank Voltage Imbalance - Lower < Upper | Điện áp Lower < Upper bất thường | Balance | Bank | No |
| `0xB4` | Severe Balance Error | Mất cân bằng nghiêm trọng | Balance | Pack | No |
| `0xB6` | Temperature Imbalance - Lower > Upper | Nhiệt độ Lower > Upper bất thường | Temperature Balance | Bank | No |
| `0xB7` | Temperature Imbalance - Lower < Upper | Nhiệt độ Lower < Upper bất thường | Temperature Balance | Bank | No |
| `0xB9` | Cell Imbalance | Cell mất cân bằng | Balance | Cells | No |
| `0xBA` | Intermittent Short - Upper Bank | Chập gián đoạn Upper Bank | Short Circuit | Upper | No |
| `0xBB` | Intermittent Short - Lower Bank | Chập gián đoạn Lower Bank | Short Circuit | Lower | No |
| `0xBC` | Intermittent Short - Lower Bank | Chập gián đoạn Lower Bank | Short Circuit | Lower | No |
| `0xBD` | Abnormally High Temperature | Nhiệt độ cao bất thường | Temperature | Pack | No |
| `0xBE` | Extreme Over-Discharge | Xả quá sâu nghiêm trọng | Over-Discharge | Pack | No\* |
| `0xC9` | High-Temperature Protection 1 | Bảo vệ quá nhiệt 1 | Protection | Pack | No |
| `0xCA` | High-Temperature Protection 2 | Bảo vệ quá nhiệt 2 | Protection | Pack | No |
| `0xCE` | Over-Current Protection 1 | Bảo vệ quá dòng 1 | Protection | Pack | No |
| `0xCF` | Over-Current Protection 2 | Bảo vệ quá dòng 2 | Protection | Pack | No |
| `0xD3` | Low-Voltage Protection 1 | Bảo vệ điện áp thấp 1 | Protection | Pack | No |
| `0xD4` | Low-Voltage Protection 2 | Bảo vệ điện áp thấp 2 | Protection | Pack | No |
| `0xD8` | Over-Voltage Protection 1 | Bảo vệ quá áp 1 | Protection | Pack | No |
| `0xD9` | Over-Voltage Protection 2 | Bảo vệ quá áp 2 | Protection | Pack | No |
| `0xDD` | Broken Detection 1 | Phát hiện đứt mạch/đường đo 1 | Detection | Unknown | No |
| `0xDE` | Broken Detection 2 | Phát hiện đứt mạch/đường đo 2 | Detection | Unknown | No |
