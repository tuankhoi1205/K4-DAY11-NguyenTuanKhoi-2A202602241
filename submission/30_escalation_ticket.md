# Escalation ticket

## Ticket 1

- **Frame:** `adasind_212280.jpg`, đối tượng model `M5` và `M6` ở vùng `edge`.
- **Ảnh chụp:** `submission/screenshots/adasind_212280_edge_model.png` (cần lưu từ `submission/r3_diag/model_compare.html`).
- **Expected impact:** hai box chỉ có model phát hiện tại edge làm tăng false positive và có thể làm sai kết luận về chất lượng theo zone. Trên toàn slice B3, model không match được 2/2 reference ở edge và sinh 3 box thừa; kết quả giữ nguyên qua các ngưỡng IoU 0.3/0.5/0.7 nên không chỉ là sai số ghép nhỏ.
- **Owner:** `ai_team`.
- **Recommendation:** kiểm tra trực quan dự đoán `M5`, `M6` cùng calibration của vòng fisheye; chạy đánh giá trên một mẫu edge lớn hơn trước khi đổi threshold hoặc retrain. Giữ nguyên annotation/reference hiện tại cho tới khi có xác nhận, vì slice ba frame chưa đủ để kết luận nguyên nhân cuối cùng.
