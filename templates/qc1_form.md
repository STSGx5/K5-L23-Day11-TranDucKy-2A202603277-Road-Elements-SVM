# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): tranducky03@gmail.com (chủ job CVAT 4750923)        Người kiểm (học viên): (chưa có thông tin — điền tên người kiểm)  
Ngày: 2026-11-20                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `job_4750923_annotations_2026_11_20_11_44_04_cvat_for_images_1.1.zip` (chỉ có `annotations.xml`); revision: chưa xác nhận được vì không có manifest đi kèm  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng) — A01 đến A06 (job có 12 ảnh, chỉ chấm 6 ảnh đầu)   Số nhãn đã kiểm (shape + tag): 80 (56 shape + 24 tag)

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 14 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 19 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 14 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 14 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 11 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 10 | 1 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 24 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 14 | 2 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 (không có ảnh fisheye) | 0 | chính |
| QC1-12 file | lỗi file | 1 | 0 | nhẹ / nặng |

Ghi chú cách đếm "số mục kiểm": QC1-01 = 6 tag camera; QC1-02 = 6 ảnh; QC1-03, 05, 06 = 14 polyline lane; QC1-04 = 14 lane + 5 road_curb; QC1-07 = 11 polygon drivable; QC1-08 = 10 đèn; QC1-09 = 10 đèn + 14 biển; QC1-10 = 14 biển; QC1-12 = 1 file zip (mở được, nhãn và thuộc tính hợp lệ, mọi ảnh đủ 4 tag; manifest và `sha256` chưa kiểm được vì không có manifest).

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-08 | A06 | traffic_light #6 (pedestrian, facing front), hộp (943,341)–(966,368) | nặng | color = off nhưng đèn đi bộ đang sáng (hiện hình người đi màu trắng). Giá trị đúng không phải off (xem ca mơ hồ về green hay unknown). Đèn hướng về xe nên tính nặng |
| 2 | QC1-04 | A05 | road_curb #1 | chính | Polyline vẽ ngược chiều: điểm đầu ở xa (905,342), điểm cuối ở gần (1280,424). Phải vẽ từ gần xe ra xa |
| 3 | QC1-09 | A01 | traffic_sign #7 (information), hộp (432,463)–(451,489) | chính | Bật edge_zone = true trên ảnh camera front. edge_zone chỉ dùng cho ảnh fisheye, ở đây phải để false |
| 4 | QC1-10 | A03 | (thiếu) traffic_sign information, vùng khoảng (272,290)–(307,301) | chính | Biển xanh tên đường trên cột bên trái, cao khoảng 11 px (≥ 8 px) chưa được gán |
| 5 | QC1-10 | A06 | (thiếu) traffic_sign information, vùng khoảng (578,330)–(593,342) | chính | Biển xanh tên đường ngay dưới biển công trường màu cam, cao khoảng 12 px (≥ 8 px) chưa được gán |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A06 | Đèn đi bộ đang hiện hình người đi màu trắng: color đúng là green hay unknown (không có giá trị white)? Dù chọn giá trị nào thì off vẫn sai, nên lỗi #1 giữ nguyên mức nặng | |
| A03 | Vạch vàng L1 gần xe là vạch đôi (hai vạch vàng song song, có khe tối ở giữa) rồi thu về một vạch ở phía xa. Gán kind = single có sai không, hay phải là double? Nếu sai thì thêm 1 lỗi QC1-06 (chính) | |
| A06 | Đèn góc trên trái (box #5, color = off, facing = front) nhìn nghiêng gần như thấy cạnh hộp: facing nên là side? Nếu đúng thì thêm 1 lỗi QC1-09 (chính) | |
| A06 | Có một khoảng mặt đường xám, rộng khoảng 100 px, giữa polygon direct và alternative không thuộc polygon nào. Có phải vùng lái bị bỏ sót (QC1-07, chính) hay là dải cột/dải phân cách? | |
| A04 | Đèn tín hiệu xanh nhỏ ở khoảng (605,279), cao khoảng 8–10 px, chưa được gán. Sát ngưỡng 8 px, có bắt buộc gán không? | |
| A03 | Biển trắng nhỏ ở khoảng (487,305)–(502,322) chưa được gán. Có phải biển giao thông không? Vạch trắng position = other ở làn đối diện bên trái có cần gán không? | |
| A04, A05, A06 | Tag weather = clear nhưng trời phủ mây xám trắng (A05 nghiêng nhiều về overcast; A04, A06 mây dày). Ranh giới clear / overcast ở đây có tính là sai tag không? | |
| A02 | Tag timeofday = dusk: ảnh nắng thấp, trời xanh sáng. Có thể là day, lead xác nhận | |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 4 / 80 nhãn = 5,0 %   Lỗi nhẹ: 0   Ca chờ lead: 8  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Có 1 lỗi nặng (#1, QC1-08: đèn đi bộ hướng về xe gán sai màu off), mà luật là có ít nhất một lỗi nặng thì Rework. Lỗi chính 4 / 80 = 5,0 %, chưa vượt 5 %, nhưng sát ngưỡng: nếu lead xác nhận thêm lỗi từ các ca mơ hồ (kind của L1 ở A03, facing của đèn ở A06, vùng lái ở A06, tag weather) thì tỉ lệ vượt 5 % và vẫn là Rework. Lỗi #1 sai chắc chắn bất kể câu trả lời, nên quyết định không chuyển sang Hold.

Các điểm đã kiểm và đạt: 6 ảnh đều có đủ 4 tag, camera = front đúng; L1, R1 có đủ ở A01–A04, A05 không có vạch sơn, A06 chỉ thấy L1; vạch đứt đều là một polyline; thuộc tính style / color / kind / position khớp ảnh (trừ ca A03 ở trên); màu đèn ở A03, A04 đúng; biển hình in (bảng "OPEN" ở A03) không bị gán nhầm.  
Giới hạn của lần chấm này: không có bảng kế hoạch ảnh (slide Task 1, Task 2) nên giả định mỗi ảnh được yêu cầu những nhóm label mà học viên đã gán (A05 chỉ road_curb); không có manifest nên chưa kiểm revision và sha256; độ lệch ≤ 5 px so với tâm vạch được kiểm bằng mắt trên ảnh phóng to, không đo bằng pixel.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
