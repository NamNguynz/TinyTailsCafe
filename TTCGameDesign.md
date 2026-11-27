# Tiny Tails Café Game Design & Ideology
## I. Thiết lập cơ bản.
- 1 màn chơi có 30 ải tương ứng vs 30 ngày trong 1 tháng.
- Đơn vị tiền tệ trong game được gọi là Piyo Coin.
- Nhân vật trong game được gọi là Furpal Critter.
- Có 3 mức độ khó:

| Độ khó | Diff Multiplier | Initial Capital |
| :--- | :---: | ---: |
| Little Paw | x0.5 | 1500 Piyo Coins |
| Busy Paw | x1 | 1000 Piyo Coins |
| Master Paw | x1.5 | 750 Piyo Coins |

- Tương tác giữa các hệ số nhân là nhân dồn (ví dụ 1.5 x 1.6 x base) thay vì cộng dồn (ví dụ (1 + 0.5 + 0.6) x base).

## II. Chỉ tiêu doanh thu/Điều kiện chiến thắng & Hệ thống ngày.
### II.1 - Hệ thống ngày.
- Qua mỗi ngày độ khó trò chơi sẽ tăng, được biểu diễn qua sự thay đổi của hệ số nhân ngày:

| Ngày | Day Multiplier |
| :--- | ---: |
| 1–10 | x1.0 |
| 11–20 | x1.1 |
| 21–25 | x1.3 |
| 26–30 | x1.5 |

- Các hệ số này độc lập theo ngày, không nhân dồn qua những ngày trước.
- Ví dụ ở ngày 26, hệ số ngày là 1.5, không phải: 1.0 × 1.1 × 1.3 × 1.5.
### II.2 - Chỉ tiêu doanh thu.
### II.2.1 - Doanh thu trung bình.
- 30 ngày chơi được chia thành 10 giai đoạn mx giai đoạn 3 ngày, sau ngày 3, 6, 9... 30, game tính doanh thu trung bình của giai đoạn vừa kết thúc.
- Mx giai đoạn có 1 doanh thu trung bình nhất định được khởi tạo ngẫu nhiên và bị ảnh hương bởi hệ số nhân độ khó và ngày.
- Nếu sau mx giai đoạn, người chơi thất bại trong việc đạt yêu cầu -> Phán thua cuộc ngay lập tức.
### II.2.2 - Tổng doanh thu cuối.
- Mx lần chơi sẽ khởi tạo doanh thu chỉ tiêu cuối cùng (sau 30 ngày) bằng tổng mức doanh thu tối thiểu của 10 giai đoạn, nhân thêm một hệ số mục tiêu cuối ngẫu nhiên trong khoảng x1.03 – x1.1, được thông báo khi bắt đầu màn chơi.
- Nếu sau khi kết thúc 30 ngày, người chơi thất bại trong việc chạm đến chỉ tiêu yêu cầu -> Phán thất bại; nếu ngược lại, họ chiến thắng.

## III. Lợi nhuận.
### III.1 - Công thức tính lợi nhuận.
- Lợi nhuận được tính sau khi khách ăn xong.
- Lợi nhuận của mỗi món ăn được phục vụ được tính bởi công thức:

``` R = R_base x M_spec x M_area x M_dec x M_tip ```

Trong đó:
- R: Lợi nhuận thu được
- R_base: Lợi nhuận cơ bản của món ăn đó
- M_spec: Hệ số nhân chủng loài của khách đặt món
- M_area: Hệ số nhân khu vực của nhà hàng
- M_dec: Hệ số nhân dựa trên các đồ trang trí trong của hàng
- M_tip: Hệ số nhân thêm khi giao đồ ăn trước 1 khoảng tg nhất định


### III.2 - Khu vực ăn uống.
Game có 3 khu vực ăn uống:
| Khu vực | Area Multiplier | Điều kiện mở khỏa |
| :--- | :---: | ---: |
| Trong nhà | x1.0 | Mặc định |
| Ngoài sân | x1.25 | Mở khóa sau ngày thứ 11 bằng Piyo Coin |
| Khu vườn | x2.0 | Cho phép mở khóa bằng Piyo Coin sau khi đã mở khu vực sân|

### III.3 - Nội thất trang trí.
- Mỗi khu vực có bốn món trang trí, mỗi món cung cấp hệ số nhân: decoration multiplier: x1.1 cho khu vực nó thuộc về.
- Người chơi bỏ tiền ra mua đồ trang trí bằng Piyo Coin.
- Mỗi món có giá khác nhau.

## IV. Nhân viên phục vụ & Bàn ăn.
### IV.1 - Bàn ăn.
- Trong nhà: 2 bàn.
- Ngoài trời: 4 bàn.
- Trong vườn: 4 bàn.
- Mỗi bàn ban đầu có 2 ghế.
- Có thể nâng cấp 2 bàn bất kỳ lên 4 ghế, giới hạn cho toàn bộ lượt chơi, ko phk khu vực.
### IV.2 - Nhân viên phục vụ.
- Mỗi nhân viên có thể nhận nhiệm vụ phục vụ một bàn.
- Nhân viên tự động đi theo lộ trình: bếp -> trong nhà -> ngoài sân -> vườn.
- Khi có đơn mới, hệ thống chọn nhân viên phù hợp dựa trên vị trí và trạng thái hiện tại.
- Tốc độ nhân viên ảnh hưởng trực tiếp đến thời gian vận chuyển món.
- Có thể dùng Piyo Coin để nâng cấp tốc độ của toàn bộ nhân viên, mx lần nâng cấp nhận hệ số nhận tốc độ speed multiplier: x1.1; tối đa được thực hiện 3 lần.

## V. Sự kiện ngẫu nhiên.
### V.1 - Khách làm bẩn bàn.
- Ngẫu nhiên có 1 khách bất kỳ làm bẩn bàn.
- Trong thời gian bàn bẩn, tất cả khách cùng bàn nhận hệ số lợi nhuận x0.8.
- Tại một thời điểm, tối đa một bàn bị bẩn.
- Bàn bẩn không tự sạch theo thời gian.
- Người chơi nhấp vào bàn để dọn.
- Khi bàn được dọn, hệ số trở về bình thường ngay lập tức.
- Xác xuất xảy ra được tính theo công thức:
``` P = P_base x M_diff x M_day ```, được kiểm tra theo khoảng thời gian, có thời gian chờ giữa hai lần xảy ra.

### V.2 - Ăn trộm đột nhập.
- Tối đa 2 tên trộm trong một ngày.
- Có thể xuất hiện đồng thời 2 tên.
- Mỗi lần nhấp trúng trộm gây 1 sát thương.
- Trộm có 2 máu cơ sở.
- Máu được tính theo công thức:
``` HP = HP_base x M_diff x M_day ``` và được làm tròn lên thành số nguyên dương.
- Trộm vào từ cửa khu vực trong nhà.
- Nếu trốn thoát thành công, người chơi mất tiền đã bị lấy.
- Nếu bị đánh bại, người chơi thu hồi số tiền bị trộm.
- Trộm lấy 10% số dư tại thời điểm bắt đầu trộm, nhân với hệ số độ khó.
- Xác xuất xảy ra được tính theo công thức:
``` P = P_base x M_diff x M_day ```, xác suất xuất hiện theo ngày, nhưng thời điểm xuất hiện được chọn trong ngày, không báo cho người chơi biết trước.
- Tốc độ của trộm được tính theo công thức:
``` SPD = SPD_base x M_diff ```

### V.3 - SuFUR Star Incoming.
- Mỗi giai đoạn 3 ngày có đúng một lần sự kiện.
- Sự kiện được kích hoạt vào một ngày được chọn trước trong cụm và được đánh dấu trong lịch trò chơi.
- Trong thời gian sự kiện, không có các sự kiện ngẫu nhiên khác.
- Hệ số độ khó và hệ số ngày không ảnh hưởng đến xác suất kích hoạt.
- Khi sự kiện xảy ra các thông số sau được thay đổi:

| Thông số | Bình thường | SuFUR Star Incoming |
| :--- | ---: | ---: |
| Thời gian ăn của khách | 100% | 75% |
| Tần suất xuất hiện khách | 100% | 150% |
| Tốc độ nhân viên | 100% | 150% |

## VI. Khách hàng(Furpal Critter).
| Chủng loài | Tần suất | Số món sẽ gọi | Spec Multiplier | Waiting Time |
| :--- | ---: | ---: | ---: | ---: |
| Thỏ|Cao|1	món bất kỳ |x1.0|60s|
| Mèo|Trung bình| 1 món bất kỳ hoặc 1 bánh + 1 nước	|x1.1|60s|
| Chó|Cực thấp|1 bánh + 1 nước|x1.5|40s|

Lịch xuất hiện:
- Thỏ: từ ngày 1.
- Mèo: từ ngày 7.
- Chó: từ ngày 17.

## VII. Nấu ăn
- Các nguyên liệu được chuẩn bị sản trên mặt bàn và ở trạng thái sống.
- Người chơi kéo nguyên liệu vào đạo cụ tương ứng để chế biến với thời.gian tương ứng (nguyên liệu ko bị cháy nếu để quá giờ)(Ko phk nguyên liệu nào cx cần làm chín).
- Sau đó người chơi ghép các nguyên liệu để tạo thành món ăn theo công thức cho trước.
- Có 2 loại món ăn là bánh và nước.
- Danh sách nguyên liệu:

|Tên|Thời gian chế biến|Cách chế biến|Đạo cụ tương ứng|
|:---|---:|---:|---:|
|Burger Bun| |Ko cần chế biến| |
|Sandwich Bread| |Ko cần chế biến| |
|Cà chua| |Ko cần chế biến| |
|Xà lách| |Ko cần chế biến|
|Thịt|? s|Rán|Chảo rán|
|Trứng|? s|Rán/Nướng cùng Bột mỳ|Chảo rán/Lò nướng|
|Bột mỳ|? s|Nướng với trứng|Lò nướng|
|Kem dâu||Ko cần chế biến||
|Kem Socola||Ko cần chế biến||
|Đậu nành|? s|Nấu thành sữa|Máy nấu sữa đậu|
|Sữa||Ko cần chế biến||
- Danh sách món ăn:

|Tên|Phân loại|Danh sách nguyên liệu|Lợi nhuận thu đc|Thời gian ăn|Xác suất gọi|Lưu ý|
|:---|---:|---:|---:|---:|---:|---:|
|Hamburger|Bánh|Burger Bun, Cà chua, Thịt, Xà lách|? Piyo Coins|? s|Cao||
|Sandwich|Bánh|Sandwich, Trứng, Cà chua, Xà lách|? Piyo Coins|? s|Cao||
|Bánh kem dâu|Bánh|Trứng, Bột mỳ, Kem dâu|? Piyo Coins|? s|Thấp|Cho trứng vào bột vào lò cùng lúc|
|Bánh kem Socola|Bánh|Trứng, Bột mỳ, Kem Socola|? Piyo Coins|? s|Thấp|Cho trứng vào bột vào lò cùng lúc|
|Sữa đậu|Nước|Đậu nành|? Piyo Coins|? s|Trung bình||
|Sữa dâu|Nước|Sữa, Kem dâu|? Piyo Coins|? s|Trung bình||
|Sữa Socola|Nước|Sữa, Kem Socola|? Piyo Coins|? s|Trung bình||

## VIII. Luồng trò chơi
- Bước 1: Khách vào nhà hàng
    - Khách tự tìm bàn trống và ngồi xuống.
    - Nếu không có bàn trống, khách có thể chờ ở cửa 15s trước khi rời đi. 
- Bước 2: Khách gọi món
    - Đám mây suy nghĩ hiển thị món ăn mà khách muốn gọi.
    - Thông tin đơn hàng được lưu lại trong hệ thống.
- Bước 3: Người chơi vào bếp
    - Khi nhấp vào khu vực bếp, cửa sổ chế biến xuất hiện. Ở góc trên bên trái có:
        - Avatar khách.
        - Danh sách món đã gọi.
        - Bộ đếm thời gian chờ.
        - Trạng thái món đã hoàn thành hay chưa.
- Bước 4: Hoàn thành món
    - Người chơi chế biến món bằng thao tác kéo-thả.
    - Khi món hoàn thành, thông báo đơn hàng được cập nhật.
- Bước 5: Gửi món
    - Khi người chơi nhấp vào thông báo, bộ đếm thời gian chờ của khách dừng lại và nhân viên tự động mang món đến bàn.
    - Nếu món được gửi đi khi thời gian còn ít nhất 75% thời gian chờ ban đầu, người chơi nhận hệ số thưởng x1.2.
    - Bộ đếm chờ dừng khi người chơi gửi món, nhưng thời gian khách ăn vẫn tiếp tục chạy sau khi món được phục vụ.
- Bước 6: Khách ăn xong
    - Khách rời khỏi bàn và tiền được cộng vào số dư.
    - Nếu khách bỏ đi sớm vì bất cứ lý do nào, không tính tiền cho lần này.
- Sau mx ngày có 1 quãng nghỉ để người chơi xem thống kê doanh thu và mua nâng cấp.

## IX. Thông số tạm thời(chx quyết định số chính xác):
- Chỉ tiêu doanh thu cơ sở: ?
- Giá mở khóa khu vực: ?
- Giá nội thất: ?
- Giá nâng cấp nhân viên: ?
- Xác suất xuất hiện sự kiện: ?
- Thời lượng một ngày chơi: 5'