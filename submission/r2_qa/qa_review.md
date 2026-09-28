# QA review · B4-edge

Mã khóa: 5B46-395B

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_236370.jpg | L1 | R03 | Box `Pedestrian` chỉ ôm người đang tương tác với xe hai bánh nhưng không có box `Bike` cho xe. Theo R03, nếu đang lái phải là một box `Bike` chung; nếu đang dắt phải có `Pedestrian` và `Bike` tách riêng. |
| adasind_258420.jpg | L1+L3 | R03 | Cùng người và xe hai bánh bị tách thành một box `Pedestrian` và một box `Bike` chồng nhau; ảnh cho thấy ca rider nên cần một box `Bike` duy nhất bao người lái và xe. |
| adasind_258420.jpg | L2 | R10 | `edge_zone=false` nhưng tâm box có r/R khoảng 0.605, thuộc vùng `edge`; cần soát lại attribute. |
| adasind_310008.jpg | L1 | R10 | `edge_zone=false` nhưng tâm box có r/R khoảng 0.71, thuộc vùng `edge`; cần soát lại attribute. |
| adasind_310008.jpg | L2 | R10 | `edge_zone=false` nhưng tâm box có r/R khoảng 0.73, thuộc vùng `edge`; cần soát lại attribute. |
| adasind_310008.jpg | L4 | R10 | `edge_zone=false` nhưng tâm box có r/R khoảng 0.61, thuộc vùng `edge`; cần soát lại attribute. |
| adasind_310008.jpg | L5 | R10 | `edge_zone=false` nhưng tâm box có r/R khoảng 0.67, thuộc vùng `edge`; cần soát lại attribute. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
