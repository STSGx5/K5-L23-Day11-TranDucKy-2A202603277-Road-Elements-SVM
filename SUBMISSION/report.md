# Báo cáo cá nhân — Ngày 11
Họ tên: Trần Đức Kỳ              Mã học viên: 2A202603277  
Phiên bản CVAT (Help → About):  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): front 2026-11-21 08:41 (giờ Việt Nam, UTC+7), fisheye 2026-11-21 08:44    Số lần nộp lại sau Rework: 0

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | lane, road_curb: polyline; crosswalk, drivable: polygon; traffic_light, traffic_sign: rectangle |
| Thuộc tính và giá trị | Đúng | lane: position (L1, R1, L2, R2, other), style, color, kind; drivable: area_type; đèn: color, type, facing, edge_zone; biển: group, facing, edge_zone |
| 4 tag ảnh | Đúng | camera, timeofday, weather, source; mỗi tag có thuộc tính select `value` |
Cách kết thúc polyline trên bản CVAT này: bấm phím **N** sau khi click điểm cuối.  
Cách đặt tag ảnh trên bản CVAT này: dùng công cụ Tag ở thanh bên trái, đặt camera trước, sau đó timeofday, weather, source; mở Details của từng tag để kiểm giá trị vì CVAT tự điền giá trị đầu danh sách.

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 36 | 15 | 9 | 22 | 35 | 47 |
| front-extra (đã làm 4 / 4) | 4 | 10 | 2 | 5 | 6 | 12 | 23 |
| fisheye | 8 | 12 | 17 | 12 | 11 | 5 | 10 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 6 | 8 | 3 | 0 | 1 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A06 | traffic_light đi bộ, hộp (943,341) | green / unknown / off | color = unknown | Đèn đang sáng hình người đi màu trắng nên không phải off; guideline không có giá trị white nên chọn unknown thay vì green |
| A03 | lane (vạch ở đường ngang bên trái) | gán other / không gán | gán position = other, vẽ từ mép ảnh ra xa | Vạch trắng thật trên mặt đường, không thuộc làn đang đi nên không dùng L1/R1/L2/R2 |
| A05 | lane L1, R1 | vẽ thêm / không vẽ | Không vẽ | Đường không có vạch sơn, bên trái là xe đỗ che vỉa; chỉ có road_curb bên phải. Chờ coach xác nhận |
| A06 | lane R1 | vẽ thêm / không vẽ | Không vẽ | Bên phải làn xe đi là hàng cột cầu cạn, không có vạch. Chờ coach xác nhận |
| A07 | lane L1 | vẽ thêm / không vẽ | Không vẽ | Bên trái là dải bê tông, không có vạch sơn. Chờ coach xác nhận |
| A09, A14 | lane R1 | vẽ thêm / không vẽ | [Không vẽ  | `lint` vẫn báo thiếu R1; vạch bên phải ở hai ảnh này mờ hoặc nghiêng, cần xem lại và xác nhận với coach |
| A03 | lane occluded | bật occluded / không | không | Checkpoint nói A03 có đoạn vạch nối qua chỗ che; file hiện chưa có hình nào bật occluded |
| A08 | lane R1 (vạch trắng bên trái, từ (40,357) đến (482,281)) | Nối thành một polyline hay giữ hai polyline |(một solid, một dashed) | Giữ hai polyline: một solid, một dashed | Giữa nét liền và nét đứt có một khoảng trống nên không nối liền được. Hai đoạn là hai loại vạch khác nhau (`style` solid và dashed), mà guideline không có giá trị "nửa liền nửa đứt" cho `style` nên mỗi đoạn giữ đúng một giá trị.|
## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: Nguyễn Ngọc Đồng Quyết định nhận được: Rework
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-08 | A06 | nặng | đã sửa  |

Ghi chú: trước khi nộp, tôi đã tự kiểm và sửa những lỗi sau trên lô này: tag, position của 7 lane ở B05–B08 (đổi về other), chiều polyline ở A05 (gần ra xa), edge_zone sai ở A01, màu đèn đi bộ ở A06, thêm biển bị bỏ sót ở A03 và A06.

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| TranDucKy-front.zip | Có (`road_check lint` đọc được 16 ảnh) | A01: 9 / 9 | A02: 6 / 6 | Có, camera = front ở cả 16 ảnh |
| TranDucKy-fisheye.zip | Có (`road_check lint` đọc được 12 ảnh) | B01: 5 / 5 | B02: 8 / 8 | Có, đủ fisheye_front, fisheye_rear, fisheye_left, fisheye_right (mỗi loại 3 ảnh) |

## 6. Ảnh chụp màn hình
1. Tab Labels của project. 
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển). 
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong. 
4. Một đoạn XML có <polyline label="lane">. 

## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20: QC1-03 (position) và QC1-04 (chiều polyline). Bảy lane ở camera trái/phải (B05–B08) giữ nguyên giá trị mặc định L1 do CVAT tự điền, và các vạch ở A03, A05, A11 vẽ từ xa về gần. Ngày 20 tôi sẽ vẽ xong từng vạch thì mở ngay Details kiểm thuộc tính, và luôn bắt đầu từ điểm sát xe.  
Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào: Nhãn lane đi vào model phát hiện làn (row-anchor hoặc phân đoạn). Lỗi `position = L1` trên camera bên làm model học rằng vạch nhìn từ camera trái/phải là "làn sát xe", nên khi suy luận nó có thể nhầm làn mình đang đi với làn bên cạnh, mà nhầm làn là lỗi an toàn nặng của QC1.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
Không làm (không tính điểm).
