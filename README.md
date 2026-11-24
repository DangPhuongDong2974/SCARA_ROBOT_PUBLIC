# Cài đặt và cập nhật SCARA Studio

## Cài lần đầu

1. Mở [GitHub Releases](https://github.com/DangPhuongDong2974/SCARA_ROBOT_PUBLIC/releases) và tải `SCARA-Studio-Setup-X.Y.Z.exe` của bản phát hành đã được duyệt. Tệp cần gửi cho người dùng là Setup EXE.
2. Tải `SHA256SUMS.txt`. Trong PowerShell, chạy `Get-FileHash .\SCARA-Studio-Setup-X.Y.Z.exe -Algorithm SHA256` và kiểm tra giá trị trùng dòng ghi tên Setup.
3. Chạy Setup trên Windows x64 và dùng shortcut **SCARA Studio** ở Desktop hoặc Start Menu. Thư mục mặc định là `%LOCALAPPDATA%\Programs\SCARA Studio`. Setup cài cho tài khoản Windows hiện tại và mang sẵn .NET Desktop Runtime. Mở **Settings → Version** để xem phiên bản.
4. Cài [Mitsubishi MX Component](https://dl.mitsubishielectric.com/dl/fa/document/manual/plc/sh082395eng/sh082395engg.pdf) với **ActUtlType64** nếu cần PLC. Thiết lập Logical Station bằng Communication Settings Utility theo cấu hình tại máy.
5. Cài [Basler pylon Software Suite x64](https://docs.baslerweb.com/software-installation-%28windows%29) gồm driver camera và thư viện phát triển .NET nếu cần camera Basler. SCARA Studio tìm `Basler.Pylon.dll` trong thư mục SDK x64. Nếu SDK đặt nơi khác, đặt biến môi trường người dùng `SCARA_PYLON_DLL` thành đường dẫn tuyệt đối tới DLL x64 trong phiên bản SDK phù hợp, rồi khởi động lại. Với OpenCV, cài [Microsoft Visual C++ Redistributable x64](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) nếu Windows báo thiếu thư viện VC++.

Bộ cài hiện chưa ký Authenticode. Kiểm tra nguồn tải và SHA-256 trước khi chạy. ZIP x64 chứa payload dành cho updater. Mở ứng dụng ngoại tuyến để xem giao diện và Robot Model mà không cần PLC hoặc camera.

## Cập nhật sau khi cài Setup

1. Dừng robot tại máy, kết thúc mọi lệnh đang chạy và ngắt PLC lẫn camera trong SCARA Studio.
2. Mở **Settings → Version → UPDATE VERSION**. Xem phiên bản, đọc ghi chú rồi xác nhận robot đã dừng và hai thiết bị đã ngắt an toàn.
3. Chờ tải và kiểm tra gói. Ứng dụng tự đóng và khởi động bản mới. Xem lại **Settings → Version**.
4. Nếu cập nhật lỗi, mở lại bằng shortcut SCARA Studio nếu cửa sổ chưa tự mở. Nhật ký nằm ở `%LOCALAPPDATA%\SCARA Robot\update.log`. Khi cần hỗ trợ, gửi phần liên quan tới lần cập nhật.

Ứng dụng không đọc được trạng thái chuyển động thực của robot khi đã ngắt PLC. Người vận hành xác nhận robot đã dừng trước khi cập nhật.

## Chuyển từ bộ cài cũ

Các bản cũ trỏ cố định tới `SCARA_ROBOT_UPDATES`. Khi có bản đã duyệt trên kho mới, đóng bản cũ và chạy Setup một lần. Shortcut mới mở bản cài có kênh `SCARA_ROBOT_PUBLIC`. Cấu hình người dùng được đọc từ `%LOCALAPPDATA%\SCARA Robot`.

## Gỡ cài đặt

Mở **Windows Settings → Apps → SCARA Studio → Uninstall**. Uninstaller gỡ phiên bản do Setup quản lý, shortcut và thông tin cài đặt. Dữ liệu người dùng và tệp log ở `%LOCALAPPDATA%\SCARA Robot` được giữ lại.
