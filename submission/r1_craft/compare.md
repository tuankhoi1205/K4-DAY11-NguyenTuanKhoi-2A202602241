# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_152940.jpg
- L3+R5 mid WRONG_CLASS
- R6 mid MISSING
## adasind_167700.jpg
- L5 mid IGNORE_SCOPE
- L1+R3 mid WRONG_CLASS
- L2+R4 center WRONG_CLASS
- L6+R5 center BOX_GEOMETRY
- R1 center MISSING
- R2 mid MISSING
- R9 mid MISSING
## adasind_212280.jpg
- R2 center MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 10 | 6 | 4 | 2 |
| mid | 6 | 1 | 5 | 2 |
| edge | 2 | 2 | 0 | 0 |
