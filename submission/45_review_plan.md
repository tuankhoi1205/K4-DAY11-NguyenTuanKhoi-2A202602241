# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `B3-center / adasind_167700.jpg` | Trước rework có `TP=3`, `FP=3`, `FN=6`; gồm bỏ sót, sai class `Bike/Pedestrian`, `Truck/Car` và box Bike sai hình học. | Đây là frame có recall thấp nhất (`0.333`) và nhiều lỗi annotator tập trung nhất; review trước giúp xử lý đồng thời class, phạm vi rider và hình học box. | Ảnh gốc; `submission/r1_craft/compare.html`; `submission/r3_diag/local_quality_conflicts.csv`; các dòng `R1+M1`, `R2+M7`, `R3+M3`, `R4+M4`, `R5+M6`, `R9` trong findings; export trước/sau và mã khóa. |
| `B3-center / edge zone` (`adasind_152940.jpg`, `adasind_212280.jpg`) | Model match `0/2` reference và sinh `3` box thừa ở edge; kết quả không đổi tại IoU `0.3`, `0.5`, `0.7`, trong khi learner match `2/2`. | Sai lệch tập trung theo zone và lặp lại qua ngưỡng IoU, nên cần ưu tiên kiểm tra domain fisheye/calibration trước khi chỉnh threshold model. | `submission/r3_diag/model_compare.html`; `submission/r3_diag/iou_sweep.md`; `submission/r3_diag/zone_table.md`; screenshot `submission/screenshots/adasind_212280_edge_model.png`; ticket `submission/30_escalation_ticket.md`. |

Giới hạn của kết luận từ ba frame ADASIND: đây chỉ là ba frame của một camera và teaching reference chưa phải gold set đã phê duyệt. Edge chỉ có hai box reference, các frame có thể tương quan theo cảnh/thời gian, nên không thể suy ra tỷ lệ lỗi của toàn bộ ADASIND hay của bốn camera; kết luận chỉ dùng để chọn ca cần review tiếp.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: chia đủ tám ô `front/rear/left/right × normal/hard`, kiểm tổng đúng 200 và giữ số dương cho mọi ô. Trong từng ô, nhóm frame theo scene/time block rồi chọn frame cách nhau hoặc tối đa một frame đại diện cho một đoạn liên tiếp để tránh coi các ảnh gần như trùng nhau là bằng chứng độc lập. Soát thêm phân bố ngày/đêm, che khuất, mật độ và vùng `center/mid/edge`. Vì kế hoạch cố ý lấy nhiều hard case theo rủi ro chứ không lấy mẫu xác suất đại diện, nó giúp tìm lỗi và xây hàng đợi review nhưng chưa thể ước lượng tỷ lệ lỗi của quần thể nếu không có sampling weight và một mẫu ngẫu nhiên độc lập.
