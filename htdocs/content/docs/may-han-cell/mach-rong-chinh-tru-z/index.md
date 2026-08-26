---
title: "Hướng dẫn sử dụng nút chỉnh trụ Z mạch rồng"
description: "Chia sẻ nguyên lý điều khiển trụ Z trong máy hàn cell pin, lấy lực nén làm chuẩn thay vì hành trình, giúp mối hàn ổn định và ít lỗi."
tags: ["mach-han-cell", "mach-rong"]
type: docs
weight: 4
---

{{< figure src="drg-3D.png" alt="Chỉnh Z Mạch rồng" >}}



## 🔩 Điều khiển trụ Z – cốt lõi để chỉnh lực hàn cell pin cho chuẩn

Rất nhiều anh em khi làm máy hàn cell pin hay nhầm lẫn giữa **hành trình trụ Z** và **lực nén kim hàn**.  
Thực tế, thứ quyết định mối hàn **ăn hay không** lại chính là **lực nén**, còn hành trình chỉ là hiện tượng đi kèm.

👉 Vì vậy, cách điều khiển trụ Z cần xoay quanh **việc kiểm soát lực**, không phải chạy theo hành trình.

> **Qua thực nghiệm: Tổng lực nén cho cả 2 kim hàn nên là khoảng 3.6 kg đến 4 kg. Lực nén mạnh hơn hàn sẽ khó ăn, nhưng yếu hơn thì dễ bị nổ kim do kẽm không đủ lực ép kẽm xuống bề mặt pin**
---

## 💡 Nguyên lý điều khiển trụ Z

### 🔽 Nút đi xuống (DOWN)

- Nhấn và giữ nút **DOWN** → trụ Z đi xuống **liền mạch, mượt**
- Thả tay ra → trụ Z **dừng ngay lập tức**
- Giúp người dùng **canh lực nén chính xác**

### 🔼 Nút đi lên (UP)

- Nhấn và giữ nút **UP** → trụ Z đi lên đúng **1 hành trình kích hàn**
- Sau đó **tự động dừng khoảng 2 giây**
- Nếu trong thời gian dừng **vẫn giữ nút UP** → trụ Z sẽ **đi lên tiếp liên tục** và **không dừng lại** cho đến khi thả nút

---

## ⚙️ Vì sao phải làm như vậy?

Trong hàn cell pin:

- **Lực nén kim hàn** là yếu tố quyết định:
  - Mối hàn ăn sâu hay không
  - Có cháy kẽm hay không
  - Độ ổn định giữa các mối hàn
- **Hành trình trụ Z** chỉ là hệ quả của việc tạo ra lực đó

👉 Do đó:
> **Lấy lực nén làm gốc – hành trình chỉ để tham chiếu**

---

## 🛠️ Cách chỉnh lực nén chuẩn trong thực tế

1. Nhấn **DOWN** cho trụ Z đi xuống  
2. Khi kim hàn chạm kẽm, tiếp tục nén đến **lực mong muốn**  
   - Có thể dùng **cái cân** để đo lực nén
   - Đánh dấu **độ nén trên cân lực** - (khoảng dịch chuyển do lò so bị nén)
3. Khi đã đạt lực chuẩn → nhấn giữ **UP**
4. Trụ Z sẽ:
   - Đi lên đúng **1 hành trình kích hàn**
   - **Tự dừng** tại vị trí này

✅ **Vị trí dừng đó chính là “điểm chuẩn” để hàn**

---

## 🔥 Kết luận

- Chỉnh đúng **lực nén** → mối hàn ổn định
- Không phụ thuộc vào cảm giác tay hay hành trình ước lượng

> Khi lực đã đúng, mọi thứ còn lại sẽ trở nên đơn giản.

---

📌 *Bài viết chia sẻ kinh nghiệm thực tế cho anh em làm pin.  
Nếu thấy hữu ích, cứ lưu lại hoặc chia sẻ cho người cần.*  
