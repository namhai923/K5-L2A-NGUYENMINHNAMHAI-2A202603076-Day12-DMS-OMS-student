# Danh sách lớp v0 — Nguyen Minh Nam Hai · G11

Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_left`, `eye_right` | open / closed / unknown | Phát hiện buồn ngủ (mắt nhắm lâu) | Có, trừ khi vùng mắt quá tối (D04) |
| 2 | `gaze_zone` | road / mirror_* / cluster / center / lap / other | Phát hiện mất tập trung (nhìn xuống, nhìn màn hình lâu) | Có, theo hướng đầu; kém khi mặt quay đi (D05) |
| 3 | `phone` | held / mounted / lap | Cảnh báo dùng điện thoại khi lái | Có (hình dạng máy) |
| 4 | `hand.on_wheel` | yes / no / unknown | Cảnh báo bỏ tay khỏi vô lăng khi chuyển sang lái tay | Có; tay sau vô lăng dễ khuất (D03) |
| 5 | `seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Nhắc thắt dây, phát hiện thắt sai | Có, rõ trên áo sáng (D06) |
| 6 | `glasses` | none / clear / sun / unknown | Hạ độ tin cậy eye_state khi đeo kính | Một phần: kính râm có thể trông trong suốt (D05) |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` + `seat` | rear_left / rear_middle / rear_right | Đếm người theo ghế, cấu hình túi khí | Có (hình dạng) |
| 2 | `seatbelt` (hành khách) | not_worn / unknown | Nhắc thắt dây ghế sau | Có nếu dây tương phản với áo |
| 3 | `infant_seat.facing` | rear / front | Tắt túi khí ghế trước; nhắc quên trẻ | Có (hình dạng nôi) |
| 4 | `child_seat.occupied` | yes / no / unknown | Nhắc quên trẻ khi khóa xe | Có hình dạng; bên trong khó thấy khi phủ chăn (S01) |
| 5 | `object.type` | bag / box / cup / other | Nhắc quên đồ khi rời xe | Có theo hình dạng, mất màu (S05) |
| 6 | `face` (chỉ box) | box | Xác nhận có người thật, không phải vật | Có khi mặt hướng camera |

## 2 câu hỏi leo thang

1. Câu hỏi: Trẻ em ngồi trong ghế trẻ em / nôi thì gán thế nào? v1.0 không có lớp trẻ em và `occupied` không có `yes`.
   Khung ví dụ: G11 S03, S04, S07 (trẻ trong ghế trẻ em); G11 S02 (em bé trong nôi).
   Bạn tạm gán thế nào và vì sao: Không vẽ `person`/`face` cho trẻ (§3); `child_seat.occupied = yes` vì ghế rõ ràng không trống (đã thêm `yes` vào guideline và schema).

2. Câu hỏi: `gaze_zone` của hành khách ghế sau dùng vùng nào? Các vùng hiện tại chỉ định nghĩa cho tài xế.
   Khung ví dụ: G11 S08 (hành khách cúi đầu), G11 S01 (nhìn thẳng camera).
   Bạn tạm gán thế nào và vì sao: S08 = `lap` (nhìn xuống); S01 = `other` (không thuộc vùng nào).
