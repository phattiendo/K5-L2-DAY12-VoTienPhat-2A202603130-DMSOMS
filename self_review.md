# Tự đánh giá — Võ Tiến Phát · G08

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S05_rgb.png | person | seat_flip | Nhầm ghế bên phải ảnh thành rear_right, đúng chuẩn theo xe phải là rear_left | rồi |
| S07_ir.png | person | seat_flip | Người ngồi bên trái ảnh gán nhầm rear_middle, sửa lại rear_right đồng bộ với S07_rgb | rồi |
| D01.png | face | guess | Ban đầu đoán mắt closed khi tài xế cúi đầu, sửa lại open vì khe mí vẫn hé mở | rồi |
| D03.png | face13 | flag | Đốm phản xạ LED 940nm che khuất mí mắt nhưng chưa bật cờ, đã bật occluded=1 | rồi |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm chiều quy ước ghế OMS (bên trái ảnh tương ứng với ghế bên phải của xe `rear_right`) và nhầm hệ trục tọa độ mắt trái/phải trên ảnh DMS xoay 90°.

Vì sao mình mắc: Do thói quen phản xạ tự nhiên nhìn theo khung hình 2D thông thường thay vì chuyển đổi sang hệ quy chiếu của xe ô tô và của chính cơ thể người trong ảnh.

Lần sau tránh bằng cách: Luôn áp dụng phương pháp tưởng tượng mình ngồi ở vị trí lái xe nhìn về phía sau (cho OMS: trái ảnh = phải xe); xoay đầu nhìn theo chiều ảnh DMS và đối chiếu toạ độ trục $y$ (cho DMS: mắt trái của tài xế luôn có $y$ lớn hơn mắt phải).

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: Ở dòng D01, bạn chỉ ra rằng tài xế liếc nhìn xuống nhưng mí mắt vẫn hé mở nên phải gán `eye_left = open` thay vì đoán `closed`. Mình học được bài học quan trọng: chỉ ghi `closed` khi thấy rõ hai mí khép chặt thực sự trong khung hình đó, không suy diễn cảm tính.
