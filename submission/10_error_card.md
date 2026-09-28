# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B3 | BOX_GEOMETRY | 1 |
| center | B3 | MISSING | 8 |
| center | B3 | SPURIOUS | 5 |
| center | B3 | WRONG_CLASS | 1 |
| center | C0 | SPURIOUS | 1 |
| center | C0 | WRONG_CLASS | 1 |
| edge | B3 | MISSING | 2 |
| edge | B3 | SPURIOUS | 3 |
| edge | B4 | ATTRIBUTE | 5 |
| mid | B3 | IGNORE_SCOPE | 1 |
| mid | B3 | MISSING | 8 |
| mid | B3 | SPURIOUS | 5 |
| mid | B3 | WRONG_CLASS | 2 |
| mid | B4 | DUPLICATE | 1 |
| mid | B4 | STRUCTURE | 1 |

## Top defects
- MISSING: 18 (ví dụ frame adasind_152940.jpg)
- SPURIOUS: 14 (ví dụ frame adasind_019560.jpg)
- ATTRIBUTE: 5 (ví dụ frame adasind_258420.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: lỗi nổi bật là `MISSING` do `E1_annotator_error`, đặc biệt ở `adasind_167700.jpg`. Với ca `R1+M1`, reference và model cùng phát hiện `Pedestrian` nhưng bản learner không có box tương ứng. Cảnh này có nhiều đối tượng nhỏ và chồng lấn nên người gán nhãn dễ tập trung vào xe lớn rồi bỏ sót người đi bộ.
- Cách sửa và ai nhận việc (`owner`): `annotator` cần bổ sung box `Pedestrian` bám sát phần nhìn thấy được và kiểm tra lại `occluded`, `truncated`, `edge_zone`; `qa` đối chiếu bằng R01. Rework đã cải thiện matched ở center từ 6 lên 7 và mid từ 1 lên 2, nhưng `R1+M1` vẫn được delta đánh dấu `chưa sửa`, nên đây là ca cần ưu tiên nếu có vòng sửa tiếp theo.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): dòng `r3_diag,B3-center,adasind_167700.jpg,R1+M1,RM_noL,MISSING` trong `submission/findings.csv`; overlay `submission/r3_diag/model_compare.html`; xung đột trong `submission/r3_diag/local_quality_conflicts.csv`; quy tắc R01 và bảng `submission/rework/delta.md`.
