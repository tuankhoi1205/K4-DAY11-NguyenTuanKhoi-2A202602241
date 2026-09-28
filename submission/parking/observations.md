# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ: vạch trắng chéo rõ ở gần giữa cạnh dưới ảnh và vạch trắng chéo dài ở vùng dưới bên phải. Hai vạch này tạo ranh giới giữa các ô đỗ riêng biệt; polyline chỉ bám phần sơn còn nhìn thấy.
- Không vẽ đường gần như nằm ngang kéo dài qua phần giữa bãi vì đây là biên của hàng ô/lối xe chạy, không phải vạch chia một ô đỗ riêng lẻ.
- Polygon `free_space` bao phần lối xe chạy trống chạy ngang ở giữa bãi, nằm giữa hàng ô đỗ tiền cảnh và hàng ô phía xa. Polygon dừng trước xe màu đỏ và phần hàng ô phía xa, đồng thời dừng tại đầu các vạch ô đỗ ở tiền cảnh; không đi xuyên xe hay vùng bị che.
- Ca chưa chắc cần hỏi người soát: các vạch sơn rất mờ ở xa khó xác định là vạch chia ô hay dấu sơn cũ, nên tôi không gán nhãn cho chúng.
