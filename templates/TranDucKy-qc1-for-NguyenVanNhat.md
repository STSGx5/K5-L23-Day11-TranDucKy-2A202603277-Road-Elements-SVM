# Phiếu QC 1 — Road v1.0
Lô được kiểm (học viên): 2A202603273-Nguyễn Văn Nhất       Người kiểm (học viên): 2A202603277 - Trần Đức Kỳ
Ngày: 2026-11-20                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest):
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng) —    Số nhãn đã kiểm (shape + tag): 80 (60 shape + 20 tag)

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 4 | nặng (1) / nhẹ (3) |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 15 | 2 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 15 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 15 | 1 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 15 | 2 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 18 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 15 | 3 | nặng (1) / chính (2) |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 27 | 2 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 12 | 4 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính (không áp dụng cho ảnh front) |
| QC1-12 file | lỗi file | 1 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-06 | A01 | lane L2, #2044 | chính | Vạch mép trái là vạch liền trắng đơn nhưng gán `kind = double`; đúng là `single` |
| 2 | QC1-10 | A01 | traffic_sign (thiếu) | chính | Bỏ sót biển chỉ dẫn xanh lá nhỏ ở xa, khoảng x 433–450, y 463–489 (cao khoảng 26 px) |
| 3 | QC1-05 | A03 | lane (không nhãn nào bật occluded) | chính | Checkpoint yêu cầu A03 có đoạn vạch nối qua chỗ che và bật `occluded`; bài không có polyline nào bật cờ này |
| 4 | QC1-10 | A03 | traffic_sign (thiếu) | chính | Bỏ sót mặt sau biển trên cột góc trái, khoảng x 216–275, y 172–228; cần box với `facing = back` |
| 5 | QC1-10 | A03 | traffic_sign (thiếu) | chính | Bỏ sót biển tên đường xanh lá sau tán cây, khoảng x 253–306, y 287–302 (`group = information`) |
| 6 | QC1-03 | A04 | lane, #2082 | nặng | Vạch liền trắng bên phải (ranh làn xe đạp) gán `position = L1`, trùng với L1 vàng đôi #2071; đúng là `R2` |
| 7 | QC1-09 | A04 | traffic_sign, #2084 | chính | Biển tên đường xanh lá trên cột gán `group = mandatory`; đúng là `information` |
| 8 | QC1-10 | A04 | traffic_sign (thiếu) | chính | Bỏ sót mặt sau biển trên cùng cột (phía trên biển #2085), khoảng x 232–252, y 152–170; cần `facing = back` |
| 9 | QC1-01 | A05 | tag camera (thiếu) | nặng | Ảnh không có tag `camera` |
| 10 | QC1-01 | A05 | tag timeofday (thiếu) | nhẹ | Ảnh không có tag `timeofday` |
| 11 | QC1-01 | A05 | tag weather (thiếu) | nhẹ | Ảnh không có tag `weather` |
| 12 | QC1-01 | A05 | tag source (thiếu) | nhẹ | Ảnh không có tag `source` |
| 13 | QC1-03 | A06 | lane other, #2088 | nặng | Thừa: polyline nằm trên vạch dừng nằm ngang trước vạch ngựa vạn, không phải vạch kẻ làn |
| 14 | QC1-06 | A06 | lane L1, #2089 | chính | Vạch tim đường sau vạch ngựa vạn là vạch vàng nhưng gán `color = white`; đúng là `yellow` |
| 15 | QC1-08 | A06 | traffic_light, #2101 | chính | Đèn góc trên trái nhìn nghiêng, không thấy bóng nào sáng nhưng gán `color = red`; đúng là `unknown` |
| 16 | QC1-09 | A06 | traffic_light, #2101 | chính | Đèn này quay ngang so với xe nhưng gán `facing = front`; đúng là `side` |
| 17 | QC1-08 | A06 | traffic_light pedestrian, #2090 | nặng | Đầu đèn đi bộ quay về xe đang sáng hình người đi (walk) nhưng gán `color = off` |
| 18 | QC1-08 | A06 | traffic_light pedestrian, #2090 | chính | Một box gộp hai đầu đèn đi bộ (một đầu quay ngang, một đầu quay về xe); mỗi đầu cần box riêng |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A02 | Nắng chiều thấp, bóng dài nhưng trời còn sáng: `timeofday` là `dusk` (như bài) hay `day`? | |
| A03 | Polyline #2066 (`position = other`) nằm trên vạch trắng ở đường ngang bên trái: là vạch làn hay mép vạch dừng / ngựa vạn (nếu vậy là thừa, QC1-03 nặng)? | |
| A03 | Đoạn vạch nào trong A03 cần bật `occluded` (L1 vàng hay R1 đứt)? Lỗi #3 ghi theo checkpoint, chưa chỉ được đoạn cụ thể | |
| A03 | Vùng `alternative` bên phải kéo tới sát hàng xe đỗ: có phải trừ dải đỗ xe ra không? | |
| A05 | Ảnh không có vạch làn, bài chỉ có một `road_curb` bên phải và không có `drivable`: bảng kế hoạch ảnh có yêu cầu `drivable` và vỉa bên trái (bị xe đỗ che) không? | |
| A06 | Bên phải làn xe đi là hàng cột cầu cạn, không có vạch: có miễn QC1-02 (thiếu R1) cho ảnh này không? | |
| A06 | Đèn đi bộ đang sáng hình người đi (walk) thì ghi `color = green` hay giá trị khác? | |

## Quyết định
Lỗi nặng: 4   Lỗi chính: 11 / 80 nhãn = 13,75 %   Lỗi nhẹ: 3   Ca chờ lead: 7  
Quyết định (Release / Hold / Rework): Rework  
Lý do (theo luật của phiếu): Có 4 lỗi nặng (A04 #2082 sai `position`; A05 thiếu tag camera; A06 #2088 vẽ vạch dừng thành lane; A06 #2090 sai màu đèn quay về xe), một lỗi nặng là đủ để Rework. Tỉ lệ lỗi chính 13,75 % cũng vượt ngưỡng 5 %. Các ca mơ hồ không làm đổi kết luận nên không ra Hold. Phạm vi kiểm: task front, ảnh A01–A06; 80 nhãn đã kiểm (shape + tag): A01 12, A02 10, A03 19, A04 18, A05 1, A06 20.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: thang mức lỗi QC 1 (`docs/qc_severity_road_v1.0.md`).
