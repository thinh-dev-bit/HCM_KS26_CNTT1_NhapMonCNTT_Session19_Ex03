# Phần 1: Báo cáo phân tích (IPO)

## 1. Input (Đầu vào - Dấu hiệu lây nhiễm)
*   **Dấu hiệu:** Các tài khoản cốt lõi như Facebook, Gmail liên tục bị mất quyền kiểm soát, có cảnh báo đăng nhập trái phép hoặc bị thay đổi thông tin.
*   **Bản chất rủi ro:** Mã độc **Infostealer** đã thâm nhập thành công (có thể do nhấp vào link Phishing hoặc cài phần mềm Crack). Chúng tiến hành quét bộ nhớ RAM và thư mục cục bộ của trình duyệt để đánh cắp toàn bộ Cookie phiên đăng nhập và mật khẩu đã lưu, sau đó gửi về máy chủ C2 của tin tặc.

## 2. Process (Quy trình xử lý - 4 Bước Cấp cứu)
Dựa trên nguyên tắc "Ngắt kết nối và Thu hồi", quy trình xử lý bao gồm 4 bước:

*   **Bước 1: Ngắt kết nối mạng ngay lập tức (Disconnect).** 
    Ngắt kết nối Wi-Fi hoặc rút dây cáp LAN của máy tính bị nhiễm. Hành động này sẽ cắt đứt đường truyền, ngăn chặn Infostealer tiếp tục đẩy dữ liệu (Mật khẩu, Cookie, SSH Keys) ra bên ngoài.
*   **Bước 2: Cách ly thiết bị & Sử dụng môi trường sạch.** 
    Tuyệt đối **không** thao tác đổi mật khẩu trên máy tính đang bị nhiễm (vì máy có thể đang dính kèm mã độc Keylogger ghi lại thao tác gõ phím). Hãy sử dụng một thiết bị sạch (như điện thoại cá nhân hoặc laptop khác) để xử lý.
*   **Bước 3: Thu hồi phiên làm việc (Revoke) & Đổi mật khẩu.** 
    Trên thiết bị sạch, truy cập vào phần bảo mật của Facebook/Gmail và chọn **"Đăng xuất khỏi tất cả các thiết bị"**. Bước này làm vô hiệu hóa (Revoke) các Session Cookie mà tin tặc đã đánh cắp. Sau đó, sử dụng Trình quản lý mật khẩu (như Bitwarden) để tạo một mật khẩu ngẫu nhiên trên 20 ký tự (chữ hoa, chữ thường, số, ký tự đặc biệt) để đổi mới.
*   **Bước 4: Thiết lập chốt chặn 2FA & Làm sạch hệ thống.** 
    Kích hoạt Xác thực 2 yếu tố (2FA) thông qua **Authenticator App** (sinh mã TOTP) làm chốt chặn cuối cùng. Cuối cùng, tiến hành diệt virus triệt để trên máy tính bị nhiễm hoặc cài đặt lại trắng hệ điều hành (tuân thủ quy tắc 5 KHÔNG: tuyệt đối không dùng phần mềm Windows crack để tránh rước lại backdoor vào máy).

## 3. Output (Đầu ra - Hệ thống sạch)
*   Quyền kiểm soát tài khoản (Facebook, Gmail) được lấy lại và bảo vệ bởi lớp khiên 2FA phần cứng.
*   Đứt gãy hoàn toàn khả năng thu thập và truyền tải dữ liệu của Infostealer.
*   Thiết lập lại một môi trường làm việc số an toàn, sạch bóng mã độc và tuân thủ các thói quen chuẩn mực về bảo mật.

---

# Phần 2: Triển khai
# HƯỚNG DẪN CHI TIẾT: ĐỔI MẬT KHẨU TỪ THIẾT BỊ KHÁC VÀ THU HỒI TOKEN TRÊN GITHUB

## Phần 1. Đổi mật khẩu từ thiết bị khác (Cách ly mã độc)

**Nguyên lý bảo mật:** Tuyệt đối không thao tác đổi mật khẩu trên máy tính đang nghi nhiễm mã độc. Nếu máy dính Keylogger, mọi phím bạn gõ (kể cả mật khẩu mới) đều bị ghi lại. Nếu dính Infostealer, mật khẩu mới lưu vào trình duyệt cũng sẽ bị đánh cắp lập tức.

**Các bước thực hiện an toàn:**

1.  **Chuẩn bị thiết bị sạch:** Sử dụng một thiết bị hoàn toàn khác (điện thoại cá nhân, máy tính bảng, hoặc laptop của người khác) đảm bảo kết nối mạng an toàn (không dùng Wi-Fi công cộng không có mật khẩu).
2.  **Đăng nhập và thu hồi phiên (Revoke Sessions):**
    *   Truy cập `github.com` và đăng nhập vào tài khoản của bạn.
    *   Nhấn vào Avatar ở góc phải màn hình ➔ Chọn **Settings (Cài đặt)**.
    *   Nhìn sang menu bên trái, chọn **Sessions**.
    *   Cuộn xuống dưới cùng và nhấn vào nút **Revoke all (Thu hồi tất cả)** hoặc **Sign out of all sessions (Đăng xuất khỏi tất cả các phiên)**. Thao tác này ngay lập tức vô hiệu hóa mọi Cookie phiên làm việc mà hacker có thể đã đánh cắp từ máy tính bị nhiễm.
3.  **Tạo và đổi mật khẩu mới:**
    *   Vẫn tại menu bên trái của phần Settings, chọn **Password and authentication (Mật khẩu và xác thực)**.
    *   Tại mục *Change password*, hãy sử dụng công cụ **Password Manager** (như Bitwarden) trên thiết bị sạch để sinh ra một mật khẩu ngẫu nhiên trên 20 ký tự (kết hợp chữ hoa, chữ thường, số, ký tự đặc biệt).
    *   Nhập mật khẩu cũ (nếu có yêu cầu), dán mật khẩu mới vào và nhấn **Update password**.
    *   *(Khuyến nghị)*: Nếu chưa có, hãy bật ngay **Two-factor authentication (Xác thực 2 yếu tố - 2FA)** qua Authenticator App tại chính trang này.

---

## Phần 2. Thu hồi Token và SSH Keys (Revoke)

**Nguyên lý bảo mật:** Tuyệt đối không được nghĩ rằng chỉ cần tạo một `commit` mới xóa dòng code chứa Token/Key là xong. Hệ thống Git lưu trữ toàn bộ lịch sử (Version History). Các Scraper Bots (bot cào dữ liệu của hacker) có thể quét và sao chép khóa của bạn trong vòng vài giây kể từ lúc bạn push code. Cách duy nhất là **Thu hồi (Revoke)** để làm cho chìa khóa đó trở thành mớ giấy vụn, không còn giá trị truy cập.

**Các bước thực hiện trên GitHub:**

1.  **Truy cập Cài đặt Nhà phát triển:**
    *   Nhấn vào Avatar ở góc phải ➔ Chọn **Settings**.
    *   Cuộn menu bên trái xuống dưới cùng, chọn **Developer settings**.
2.  **Thu hồi Personal Access Tokens (PAT):**
    *   Tại menu bên trái, chọn **Personal access tokens** (Kiểm tra cả hai mục *Fine-grained tokens* và *Tokens (classic)*).
    *   Tìm trong danh sách các Token đang hoạt động. Nếu có Token nào bạn nghi ngờ bị lộ hoặc được sinh ra từ thiết bị đã nhiễm mã độc, hãy nhấn nút **Delete** hoặc **Revoke** nằm ngay bên cạnh Token đó.
    *   Xác nhận xóa. Kể từ giây phút này, bất kỳ ai dùng Token đó để gọi API tới GitHub của bạn đều sẽ bị từ chối (Mã lỗi 401 Unauthorized).
3.  **Thu hồi SSH Keys (Chìa khóa quản trị máy chủ từ xa):**
    *   Quay lại menu **Settings** chính của tài khoản (không nằm trong Developer settings).
    *   Chọn mục **SSH and GPG keys**.
    *   Kiểm tra danh sách các SSH Keys đang cấp quyền truy cập vào kho code. Nếu thấy khóa của chiếc laptop đang bị nhiễm mã độc, hãy nhấn nút **Delete** bên cạnh khóa đó.
4.  **Kiểm tra và dọn dẹp mã nguồn (Hậu kiểm):**
    *   Sau khi đã Revoke thành công trên Dashboard, lúc này bạn mới quay lại dự án (trên một môi trường an toàn).
    *   Sử dụng các công cụ như `Gitleaks` để quét lại kho chứa.
    *   Chuyển toàn bộ các biến chứa khóa mới vào tệp `.env` và đảm bảo đã thêm tệp này vào `.gitignore` trước khi commit lần tiếp theo.