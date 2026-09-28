# Guideline patch

- **Rule mới đề xuất:** **R12 — `edge_zone`:** sau khi chốt bounding box, lấy tâm box và tính khoảng cách `r` tới tâm vòng fisheye theo calibration của frame. Gán `edge_zone=true` khi `r/R >= 0.6`, ngược lại gán `false`. Attribute này chỉ mô tả vị trí tâm box trên ảnh, không mô tả vật ở gần/xa xe và độc lập với `truncated`/`occluded`. Ví dụ, một Bike còn nhìn thấy đầy đủ nhưng có tâm box ở `r/R=0.67` vẫn phải có `edge_zone=true`.
- **Áp dụng cho:** attribute `edge_zone` của mọi class có bounding box và phép chia zone `center/mid/edge`.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** tài liệu hiện chỉ nói zone là vị trí trên ảnh và không phải khoảng cách tới xe, nhưng chưa nêu ngưỡng `0.6`, cách lấy tâm box hay nguồn tâm/bán kính fisheye. Khoảng trống này dẫn đến nhiều box ở `adasind_258420.jpg` và `adasind_310008.jpg` được gán `edge_zone=false` dù tâm nằm ở vùng edge trong vòng QA B4.
- **`rules_version` mới:** `v1.1.0` (từ `v1.0.0`).
- **Hiệu lực từ:** vòng gán nhãn kế tiếp sau khi guideline owner phê duyệt; không hồi tố âm thầm các bản đã khóa.
