---
title: "Hướng dẫn nhanh mạch MVS01"
description: "Hướng dẫn đơn giản, dễ hiểu để điều chỉnh nhanh mạch MVS01-SDWF (cơ bản) ngay sau khi đấu nối."
tags: ["mach-han-cell", "mvs01-sdwf"]
type: docs
weight: 5
---

{{< figure src="cover.jpg" alt="Mạch MVS01-SDWF" >}}


## 1. Đồng bộ điện áp hiển thị trên mạch

* Tắt nguồn điện.
* **Ấn giữ núm xoay**, sau đó **bật nguồn** để vào Setup
* Tại vol Calib: Chỉnh cho **điện áp hiển thị bằng với điện áp thực tế**.
* Để lưu và thoát: Đạp cóc → Khởi động

---

## 2. Chỉnh thông số hàn

Ví dụ hiển thị trên màn hình:

```
Vol: 220 W:   82
P1 25 C 50 M1 60
```

### Giải thích thông số

> **Quy ước ký hiệu xung:** Mỗi xung được ghi theo dạng `[Chữ][Số] [Công suất]`.
> - **Chữ cái** cho biết loại xung: **P** = xung mồi (Pre), **M** = xung chính (Main).
> - **Chữ số ngay sau chữ cái** là thời gian xung, tính theo bội số **10 ms**: `P1` = 10 ms, `P2` = 20 ms, `M1` = 10 ms, `M2` = 20 ms...
> - **Số đứng sau (cách một khoảng trắng)** là **công suất**, tính theo **%**.
>
> Ví dụ: `P1 25` = xung mồi, thời gian **10 ms**, công suất **25%**.

#### 🔹 Vol: 220 W:     82 - Thông tin 
* Vol: 220 là đồng hồ hiển thị điện lưới.
* W:    80 là bộ đếm số lần hàn.


#### 🔹 P1 25 — Xung hàn mồi (Pre)

* **P** = xung mồi; **1** = thời gian xung **10 ms** (nếu `P2` thì là 20 ms); **25** = công suất **25%**.
* Đây là **xung làm mềm kẽm** trước khi hàn chính.
* Khuyến nghị để nhỏ: **15% – 25%**.

#### 🔹 C 50 — Thời gian nghỉ

* C 50 = **50 ms** nghỉ giữa xung mồi và xung chính.
* Điều chỉnh phù hợp với biến áp vì nó liên quan đến độ đẹp của mối hàn.

#### 🔹 M1 60 — Xung hàn chính (Main)

* **M** = xung chính; **1** = thời gian xung **10 ms** (nếu `M2` thì là 20 ms); **60** = công suất **60%**.
* Đây là **xung hàn chính**, ảnh hưởng trực tiếp đến độ ngấu.
* Nên chỉnh cao hơn P1 và tùy theo độ dày kẽm.

## 3. Video/ Link
* Hướng dẫn chi tiết Mạch Rồng: [Tài liệu](/docs/may-han-cell/mach-rong-chi-tiet/). 
* Cách chọn BTA100: [Tài liệu](/docs/may-han-cell/chon-bta100/)
* Liên hệ My My: [facebook](https://www.facebook.com/my.my.63808)
---

> **Gợi ý:** Mỗi biến áp khác nhau sẽ có một thông số khác nhau, cho nên cần chỉnh theo nguyên lý. Sau đó hàn thử và điều chỉnh phù hợp cho đến khi đạt được kết quả tối ưu.
