---
title: "Hướng dẫn nhanh mạch Rồng"
description: "Hướng dẫn đơn giản, dễ hiểu để điều chỉnh nhanh mạch Rồng ngay sau khi đấu nối."
tags: ["mach-han-cell", "mach-rong"]
type: docs
weight: 2
---

{{< figure src="drg-3D.png" alt="Mạch rồng 3D" >}}


## 1. Đồng bộ điện áp hiển thị trên mạch

* Tắt nguồn điện.
* **Ấn giữ núm xoay**, sau đó **bật nguồn** để vào Hệ thống
* Vào mục **Nâng cao → Chỉnh áp AC**.
* Chỉnh cho **điện áp hiển thị khớp với điện áp thực tế**.
* Để thoát ra ngoài: Phần mềm → Khởi động
> 📝 Nên dùng nguồn **12V AC ≥ 2A** để đảm bảo hiệu suất tốt nhất.
---

## 2. Kiểm tra tín hiệu kích biến áp

* Kích hàn thử (không có pin và kẽm).
* Nếu **không có điện vào biến áp**, hãy **đảo lại dây nguồn 12V AC** cấp vào mạch (Các dây khác giữ nguyên).

---

## 3. Chỉnh thông số hàn

Ví dụ hiển thị trên màn hình:

```
SCH: 2 T: 0.20mm
P1 25 C 70 M1 60
```

### Giải thích thông số

> **Quy ước ký hiệu xung:** Mỗi xung được ghi theo dạng `[Chữ][Số] [Công suất]`.
> - **Chữ cái** cho biết loại xung: **P** = xung mồi (Pre), **M** = xung chính (Main).
> - **Chữ số ngay sau chữ cái** là thời gian xung, tính theo bội số **10 ms**: `P1` = 10 ms, `P2` = 20 ms, `M1` = 10 ms, `M2` = 20 ms...
> - **Số đứng sau (cách một khoảng trắng)** là **công suất**, tính theo **%**.
>
> Ví dụ: `P1 25` = xung mồi, thời gian **10 ms**, công suất **25%**.

#### 🔹 SCH: 2 T: 0.20mm - Chương trình hàn
* SCH: 2 là chương trình hàn thứ 2 trong 6 chương trình.
* T: 0.20mm là loại kẽm (khai báo tương ứng để dễ nhận diện).


#### 🔹 P1 25 — Xung hàn mồi (Pre)

* **P** = xung mồi; **1** = thời gian xung **10 ms** (nếu `P2` thì là 20 ms); **25** = công suất **25%**.
* Đây là **xung làm mềm kẽm** trước khi hàn chính.
* Khuyến nghị để nhỏ: **15% – 25%**.

#### 🔹 C 70 — Thời gian nghỉ

* C 70 = **70 ms** nghỉ giữa xung mồi và xung chính.
* Điều chỉnh phù hợp với biến áp vì nó liên quan đến độ đẹp của mối hàn.

#### 🔹 M1 60 — Xung hàn chính (Main)

* **M** = xung chính; **1** = thời gian xung **10 ms** (nếu `M2` thì là 20 ms); **60** = công suất **60%**.
* Đây là **xung hàn chính**, ảnh hưởng trực tiếp đến độ ngấu.
* Nên chỉnh cao hơn P1 và tùy theo độ dày kẽm.

## 4. Video/ Link
* Hướng dẫn chi tiết: [Tài liệu](/docs/may-han-cell/mach-rong-chi-tiet/). 
* Video nối SCR: [youtube](https://www.youtube.com/watch?v=M3AvCFaGgWk) / [tiktok](https://www.tiktok.com/@megavon.net/video/7287894647702064402). 
* Video nối mạch: [youtube](https://www.youtube.com/watch?v=P7BlRbaLrLs) / [tiktok](https://www.tiktok.com/@megavon.net/video/7288524798681156872). 
* Liên hệ My My: [facebook](https://www.facebook.com/my.my.63808)
---

> **Gợi ý:** Mỗi biến áp khác nhau sẽ có một thông số khác nhau, cho nên cần chỉnh theo nguyên lý. Sau đó hàn thử và điều chỉnh phù hợp cho đến khi đạt được kết quả tối ưu.
