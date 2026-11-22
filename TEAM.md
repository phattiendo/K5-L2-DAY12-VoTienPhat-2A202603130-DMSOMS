# TEAM — Ngày 12

Mã bộ ảnh: **G08** · Hình thức: **cá nhân**

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Võ Tiến Phát | 2A202603130 | có | Tự rà soát đối chiếu benchmark guideline (Gói G08 làm cá nhân độc lập) | 7 |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- `S05_rgb/ir - person/child_seat`: Ca người lớn ngồi cạnh ghế trẻ em bị che khuất một phần thân dưới, đã thống nhất vẽ box `person` ôm sát phần nhìn thấy và gán `seat = rear_left`.
- `D03 - face13 / eye_state`: Ca đốm lóa LED hồng ngoại che phủ vùng mắt, thống nhất gán `eye = unknown` và bật cờ `occluded = 1` cho các điểm mốc mí mắt.

## Cá nhân

Mỗi người một mục, 1–2 dòng mỗi ý.

### VoTienPhat-2A202603130
- Phần mình làm: Tự thực hiện toàn bộ 22 ảnh (16 ảnh SVIRO và 6 ảnh Drive&Act); tự chạy kiểm thử Checkpoint A, B, Final; thực hiện rà soát độc lập đối chiếu guideline do mã G08 làm đơn lẻ; hoàn thiện đầy đủ báo cáo E1-E5.
- Điều mình học được hôm nay: Hiểu rõ sự khác biệt bản chất giữa ảnh hồng ngoại mô phỏng (IR-sim) và hồng ngoại gần thực tế (NIR 940nm); nắm vững nguyên tắc hệ quy chiếu xe và người (không gán theo màn hình ảnh).
