# Bài tập 01: Dò vết & Sửa lỗi Duyệt Mảng Struct

## 1. Lỗi trong chương trình

Lỗi nằm trong vòng lặp:

```c
if (user_list[0].days_overdue <= 3)
```

và:

```c
total_revenue += user_list[0].monthly_fee;
```

Chương trình đang luôn kiểm tra và cộng dữ liệu của `user_list[0]`, trong khi vòng lặp đang duyệt từng phần tử bằng biến `i`.

Phải sửa thành:

```c
if (user_list[i].days_overdue <= 3)
```

và:

```c
total_revenue += user_list[i].monthly_fee;
```

## 2. Nguyên nhân

* `user_list[0]` luôn trỏ đến tài khoản đầu tiên.
* Vòng lặp `i = 0 → 3` nhưng điều kiện lại không sử dụng `i`.
* Vì vậy trạng thái của các tài khoản khác bị đánh giá sai.
* Doanh thu cũng bị cộng phí của tài khoản `1001` nhiều lần.

## 3. Test Cases

| Trường hợp kiểm thử | Dữ liệu đầu vào  | Kết quả sai thực tế       | Kết quả đúng mong đợi           |
| ------------------- | ---------------- | ------------------------- | ------------------------------- |
| Tài khoản quá hạn   | `1002, 90000, 5` | Có thể bị ghi `Hop le`    | `Qua han`, không cộng doanh thu |
| Tính tổng doanh thu | 4 tài khoản mẫu  | Cộng `180000` × nhiều lần | `180000 + 260000 = 440000 VND`  |

## 4. Kết quả đúng

* 1001 → Hop le
* 1002 → Qua han
* 1003 → Hop le
* 1004 → Qua han
* Tổng doanh thu thực thu: **440000 VND**
