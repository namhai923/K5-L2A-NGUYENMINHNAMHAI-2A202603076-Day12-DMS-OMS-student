# Tự đánh giá — Nguyen Minh Nam Hai · G11

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_rgb | infant_seat | `extra` | 2 box infant_seat trùng nhau ở rear_right (copy shape 2 lần) | Có |
| S03_rgb | person, face | `wrong_class` | Gán trẻ em trong ghế trẻ em là `person` (§3: không gán trẻ em) | Có |
| D01 | face (eye_right), face13 | `flag` | Ghi eye_right=unknown và bật occluded dù mắt thấy rõ mí khép | Có |
| D03 | person (seatbelt) | `guess` | Ghi unknown dù thấy rõ không có dây trên áo sáng -> not_worn | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Box trùng nhau trên cùng ghế (S02, S03, S04, cả rgb lẫn ir) và quên đặt `light = unknown` cho ảnh SVIRO.

Vì sao mình mắc: Copy shape từ `_rgb` sang `_ir` nhiều lần mà không kiểm lại, và làm theo thói quen thay vì đọc lại §3.

Lần sau tránh bằng cách: Sau khi copy sang `_ir`, đếm box theo từng ghế; chạy `cabin_check --only` sau mỗi 2 cảnh thay vì chờ đến lần kiểm cuối.

## 3. Ghi chú về disagreement_log

Dòng D01 `eye_right`: bạn ghi `closed`, mình ghi `unknown`. Mình học được: `unknown` chỉ dùng khi thật sự không thấy; khi thấy rõ hai mí khép thì phải ghi `closed`, không dùng `unknown` cho an toàn.
