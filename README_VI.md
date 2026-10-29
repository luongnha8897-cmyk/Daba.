# Số tên danh bạ — bản thử nghiệm Android

Ứng dụng thử nghiệm dùng AccessibilityService để tìm số điện thoại trong nội dung chữ mà ứng dụng khác công khai qua cây Trợ năng, tra Contacts Provider và hiện tên bằng nhãn nổi trong 6 giây. Không đọc thành tiếng.

## Giới hạn quan trọng
- Không phải mọi ứng dụng đều cung cấp chữ cho Trợ năng. Chữ nằm trong ảnh, video, màn hình bảo mật hoặc một số giao diện tùy biến sẽ không được nhận diện ở bản này.
- Bản này chưa có OCR/chụp màn hình. OCR toàn màn hình cần thêm quyền chụp màn hình do Android yêu cầu xác nhận, và cần xử lý riêng.
- Chỉ xử lý cục bộ trên máy; cần quyền danh bạ và người dùng tự bật Trợ năng.

## Tạo APK ngay trên GitHub bằng điện thoại
1. Tạo repository GitHub mới, ví dụ `so-ten-danh-ba`.
2. Tải lên toàn bộ nội dung thư mục này, giữ nguyên cấu trúc và thư mục ẩn `.github`.
3. Mở tab **Actions** của repository, chọn workflow **Build Android APK**, bấm **Run workflow**.
4. Khi chạy xong, mở lần chạy thành công và tải artifact `SoTenDanhBa-debug-apk` (ZIP). Giải nén ZIP để lấy `app-debug.apk`.
5. Mở APK trên điện thoại để cài; nếu Android hỏi, cho phép cài ứng dụng từ nguồn này.
6. Mở ứng dụng, cấp quyền danh bạ, bấm mở Cài đặt Trợ năng và bật **Số tên danh bạ**.
7. Thử ở một ứng dụng có hiển thị số điện thoại dưới dạng chữ. Khi tìm được số đã lưu, nhãn tên sẽ hiện trên cùng màn hình trong khoảng 6 giây.

Nếu build lỗi, mở log của bước **Build debug APK** để xem lỗi cụ thể.


Nút BẬT/TẮT nhận diện: dùng nút trên màn hình chính. Khi tắt, dịch vụ ngừng xử lý các sự kiện và ẩn bảng kết quả; khi bật lại, cần bảo đảm dịch vụ Trợ năng vẫn được bật. Mỗi kết quả hiển thị cả tên và số điện thoại.


## Lưu ý sửa lỗi "gói có vẻ không hợp lệ"
Không dùng `jarsigner` để ký lại APK đã build. Hãy build APK mới bằng Android Gradle Plugin qua GitHub Actions như hướng dẫn trên; APK debug do Gradle tạo sẽ được ký bằng debug key và có chữ ký APK chuẩn cho Android. Tải artifact `SoTenDanhBa-debug-apk` rồi giải nén lấy `app-debug.apk`.
