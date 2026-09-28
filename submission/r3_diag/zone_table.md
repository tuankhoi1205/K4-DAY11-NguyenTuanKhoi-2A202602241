# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 10 | 4 | 2 | 2 | 3 | MISSING (2) |
| mid | 6 | 5 | 2 | 2 | 3 | MISSING (3) |
| edge | 2 | 0 | 0 | 2 | 3 | — |

## Nhận xét

- Người gán nhãn (L) gãy nhiều nhất ở `mid`: thiếu 5/6 box reference và thừa 2 box; lỗi chính là `MISSING` (3). Model (M) gãy rõ nhất ở `edge`: thiếu 2/2 box reference và thừa 3 box. Ngược lại, L khớp đủ 2/2 box `edge`, không thiếu hoặc thừa.
- Các khác biệt của L tập trung ở `adasind_167700.jpg`, gồm ca rider/Bike, sai class và box hình học; vì vậy khả năng lớn là quyết định phạm vi/class và hình học box, không phải thiếu `ego_body`. M thất bại ở edge phù hợp với giả thuyết méo fisheye và lệch miền ảnh phẳng, nhưng slice chỉ có 3 frame và đúng 2 box reference ở edge nên chưa đủ để khái quát. IoU sweep cũng cho thấy L chỉ tăng từ 1 lên 2 match ở mid khi hạ IoU 0.50 xuống 0.30, còn kết luận về edge của M vẫn giữ 0 match ở cả ba ngưỡng.
