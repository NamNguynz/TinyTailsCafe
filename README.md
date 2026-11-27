# Tiny Tails Café Game Introduction
## I. Sơ lược
- Tiny Tails Café là Game mô phỏng quản lý nhà hàng với chủ đề động vật và phong cách Pixel.
- Game được xây dựng dựa trên lối chơi ghép đồ ăn của dòng game Papa Louie và quản lý nhà hàng chủ đề động vật của Animal Restaurant.

## II. Công nghệ sử dụng
- Ngôn ngữ lập trình C#
- .NET SDK 10.0.402: Bộ công cụ phát triển phần mềm do Microsoft cung cấp.
- Godot.NET 4.7.2: Game Engine mã nguồn mở.
- SQLite: Cơ sở dữ liệu nhỏ gọn, có thể cài đặt trong ứng dụng khác.

## III. Tổ chức thư mục
- .godot: Tập các file cấu hình của Godot.
- Assets: Lưu tài nguyên của Game.
    - Audios: Âm thanh
    - Fonts: Phông chữ
    - Images: Hình ảnh & Giao diện
    - Scences: Khung cảnh(Thể hiện dưới dạng cây)
    - Scripts: Đối tượng, Dịch vụ & Tệp kịch bản
        - Controller: Script điều khiển cho các Khung cảnh.
        - DTOs(Database Transfer Object): Hỗ trợ truyền dữ liệu và truy vấn Database.
        - Models: Các Class/Giao diện.
        - Service: Các dịch vụ cung cấp dựa trên các Models.
- Infrastructure: Cấu hình và Hạ tầng khác.
    - Persistence: Thiết lập Database.
        - Context: DBContext - XD và Thiết lập mô hình CSDL bằng gói NuGet Microsoft.EntityFramework.Core.
        - Migration: File Migration đc gói NuGet trên tạo.

## IV. Thiết đặt Game
- Xem trong file: [Tiny Tails Café - Game Design](./TTCGameDesign.md).

## V. Cài đặt Game
- Vào phần Release tải file TinyTailsCafe.exe về và cài đặt (Chx làm).