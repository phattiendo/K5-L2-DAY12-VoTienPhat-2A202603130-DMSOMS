# Danh sách lớp v0 — Võ Tiến Phát · G08

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state (eye_left, eye_right) | open / closed / unknown | Phát hiện tài xế buồn ngủ (ngủ gật, micro-sleep qua chỉ số PERCLOS khi mắt nhắm liên tục > 1.5s) | Có, nhìn rõ khe mí mở/khép, trừ khi kính phản xạ chói lóa đèn LED |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung thị giác (visual distraction khi tài xế nhìn xuống đùi hoặc màn hình trung tâm liên tục > 2s) | Có, xác định được qua hướng quay đầu và vị trí đồng tử |
| 3 | phone_use (phone.state) | held / mounted / lap / none | Phát hiện hành vi sử dụng điện thoại khi đang lái xe (vi phạm an toàn giao thông, gây xao nhãng thao tác tay và mắt) | Có, nhận diện được đường viền máy, mặt lưng hoặc màn hình phát sáng |
| 4 | hand_on_wheel | yes / no / unknown | Giám sát tài xế đặt tay lên vô lăng (yêu cầu an toàn bắt buộc của hệ thống hỗ trợ lái bán tự động Level 2 / ADAS) | Có, thấy rõ bàn tay tiếp xúc với vành vô lăng |
| 5 | head_pose (từ face13) | pitch / yaw / roll | Ước lượng tư thế và hướng quay đầu để bổ trợ cho gaze zone khi mắt bị che khuất hoặc góc nhìn nghiêng | Có, tính toán hình học trực tiếp từ 13 điểm mốc khuôn mặt |
| 6 | seatbelt_driver | worn_correct / worn_incorrect / not_worn / unknown | Kiểm tra tuân thủ an toàn trước khi khởi hành hoặc kích hoạt tính năng tự lái; cảnh báo nhắc nhở thắt dây | Có thể thấy độ tương phản của dải dây vắt qua vai, nhưng khó nhận biết nếu áo màu tối |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | seat_occupancy | empty / person / child_seat / infant_seat / object | Quản lý trạng thái có người/vật trên từng ghế để điều khiển kích hoạt túi khí thông minh và bật chuông nhắc dây an toàn | Có, nhận diện qua biên dạng và hình khối của vật thể/người |
| 2 | infant_seat | có / không, facing (rear / front) | Nhắc nhở chống bỏ quên trẻ sơ sinh trong xe (CPD - Child Presence Detection); tự động ngắt túi khí ghế trước nếu lắp ghế ngược | Có, nhận diện tốt qua hình dáng nôi và quai xách |
| 3 | child_seat_occupied | no / unknown | Nhận biết có trẻ em ngồi trong ghế trẻ em hay không để cảnh báo phụ huynh khi tắt máy rời xe theo tiêu chuẩn Euro NCAP | Có, phát hiện bóng dáng cơ thể trẻ ngồi trong lòng ghế |
| 4 | left_behind_object | bag / box / cup / other | Cảnh báo hành khách bỏ quên tư trang có giá trị (túi xách, laptop) khi rời xe; cảnh báo nguy cơ trộm cắp cạy cửa | Có, phân biệt được hình khối dạng túi/hộp dù mất màu sắc |
| 5 | seatbelt_rear | worn_correct / worn_incorrect / not_worn / unknown | Giám sát hành khách hàng ghế sau thắt dây an toàn để hiển thị cảnh báo lên cụm đồng hồ táp-lô | Khó thấy hơn ảnh màu do mất màu sắc dải dây, chỉ nhận biết được nếp vắt chéo qua ngực |
| 6 | passenger_posture | normal / sleeping / out_of_position | Giám sát tư thế hành khách (ngồi thẳng, nằm ngủ, nghiêng người) để điều chỉnh lực bung túi khí phù hợp nhằm tránh chấn thương | Có, xác định được tư thế cơ thể hành khách trong điều kiện thiếu sáng |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. **Câu hỏi:** Khi một người lớn ở hàng ghế sau bị ghế trẻ em hoặc nôi xách tay đặt ở ghế bên cạnh che khuất phần lớn thân dưới (chỉ lộ nửa thân trên và một phần vai), quy chuẩn vẽ box `person` nên ôm sát phần nhìn thấy được hay ước lượng toàn bộ vị trí chỗ ngồi?
   * **Khung ví dụ:** `S05_rgb.png` và `S05_ir.png` (ghế sau bên trái `rear_left`).
   * **Bạn tạm gán thế nào và vì sao:** Tạm vẽ box `person` ôm sát phần cơ thể thực tế nhìn thấy được; gán `seat = rear_left` theo đúng vị trí ghế trong xe; các thuộc tính bị che khuất như `seatbelt` đặt `unknown` theo đúng Quy tắc chung 1 (không thấy thì unknown).

2. **Câu hỏi:** Trên ảnh NIR thực tế của camera DMS, khi tài xế đeo kính hoặc bề mặt nhãn cầu xuất hiện đốm phản xạ LED 940nm che lấp toàn bộ khe mắt khiến không thể phân biệt mắt mở hay nhắm, guideline có cho phép suy đoán dựa trên ngữ cảnh (ví dụ đầu đang hướng thẳng ra đường) hay bắt buộc phải gán `unknown`?
   * **Khung ví dụ:** `D03.png` (ảnh NIR chụp góc lái ban đêm có đèn LED phản xạ trên mắt phải).
   * **Bạn tạm gán thế nào và vì sao:** Tạm gán `eye_right = unknown`, không đoán `open` hay `closed`; đồng thời trên `face13` bật cờ `occluded = 1` cho các điểm mốc mí mắt bị lóa sáng theo đúng tinh thần Quy tắc chung 1 và mục 4.5.
