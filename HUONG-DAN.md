# Hướng dẫn cài app Luyện phát âm

Thư mục gồm 7 file: index.html, manifest.webmanifest, sw.js, ba file icon (.png) và file hướng dẫn này. Làm lần lượt 4 bước dưới đây, mất khoảng 30–45 phút.

## Bước 1. Lấy khóa Azure Speech (bắt buộc)

1. Vào https://portal.azure.com và đăng nhập bằng tài khoản Microsoft cá nhân. Nếu chưa có gói Azure, đăng ký gói miễn phí; Microsoft sẽ yêu cầu thẻ để xác minh.
2. Bấm "Create a resource", tìm "Speech" và chọn "Speech" (thuộc Azure AI services).
3. Điền thông tin:
   - Resource group: tạo mới, ví dụ `phat-am`.
   - Region: chọn `Southeast Asia` (gần Việt Nam, phản hồi nhanh).
   - Name: đặt tên bất kỳ, ví dụ `phat-am-nga`.
   - Pricing tier: chọn `Free F0` để dùng miễn phí trong hạn mức. Khi luyện nhiều và hết hạn mức, đổi sang `Standard S0`.
4. Bấm "Review + create", rồi "Create". Chờ khoảng 1 phút.
5. Mở resource vừa tạo, vào mục "Keys and Endpoint". Ghi lại `KEY 1` và `Location/Region` (ví dụ `southeastasia`).

Nên đặt cảnh báo chi tiêu trong "Cost Management" để không bị phát sinh bất ngờ.

## Bước 2. Lấy khóa Claude API (không bắt buộc)

Bước này chỉ cần nếu muốn dùng nút "Nhận xét chi tiết bằng AI". Không có khóa này, app vẫn chấm điểm và đưa mẹo sửa cho từng âm.

1. Đăng nhập Claude Console của Anthropic bằng tài khoản cá nhân.
2. Nạp một ít credit (vài USD dùng được rất lâu), rồi tạo API key.
3. Đặt giới hạn chi tiêu hằng tháng thấp, ví dụ 5 USD.

## Bước 3. Đưa app lên mạng bằng GitHub Pages (miễn phí)

Micro chỉ hoạt động khi app chạy qua địa chỉ https, nên cần đưa lên mạng.

1. Tạo tài khoản tại https://github.com.
2. Bấm "New repository", đặt tên ví dụ `phat-am`, chọn Public, bấm "Create repository".
3. Bấm "uploading an existing file", kéo thả cả 7 file vào, rồi bấm "Commit changes".
4. Vào "Settings", chọn "Pages". Ở mục "Branch" chọn `main` và thư mục `/ (root)`, rồi bấm "Save".
5. Sau 1–2 phút, app có địa chỉ dạng `https://ten-cua-ban.github.io/phat-am/`.

Để repository ở chế độ Public vẫn an toàn: mã nguồn không chứa khóa nào. Khóa chỉ được lưu trong bộ nhớ của điện thoại sau khi bạn nhập ở bước 4. Bạn chỉ cần không chia sẻ đường link app cho người khác.

## Bước 4. Cài vào điện thoại

iPhone:
1. Mở địa chỉ app bằng Safari.
2. Bấm nút Chia sẻ, chọn "Thêm vào MH chính" (Add to Home Screen).

Android:
1. Mở địa chỉ app bằng Chrome.
2. Bấm menu ⋮, chọn "Cài đặt ứng dụng" hoặc "Thêm vào màn hình chính".

Sau đó:
1. Mở app từ icon vừa tạo, vào "Cài đặt".
2. Nhập Key 1 và Region của Azure, và khóa Claude nếu có.
3. Bấm "Kiểm tra kết nối". Nếu nghe thấy câu "Your settings are working." là đã xong.
4. Lần đầu bấm nút micro, cho phép app dùng micro.

## Cách dùng

- Theo chủ đề: chọn tình huống hoặc nhóm âm khó, nghe mẫu, chạm micro để nói, chạm lần nữa để dừng.
- Tự luyện: gõ từ hoặc câu bất kỳ, bấm "Luyện ngay". Câu hay dùng thì bấm "Lưu vào danh sách".
- Kết quả: từ màu xanh là tốt, vàng là tạm được, đỏ là cần sửa. Dưới mỗi từ là phiên âm IPA, âm nào màu đỏ là âm bị sai. Chạm vào một từ để nghe riêng từ đó và xem cách sửa.
- Tiến bộ: xem điểm trung bình, các âm bạn hay sai nhất, và luyện lại các câu cũ.

## Khi gặp lỗi

- "Khóa Azure hoặc vùng không đúng": kiểm tra lại Key 1 và Region, region phải viết liền và chữ thường, ví dụ `southeastasia`.
- Không ghi âm được: vào cài đặt trình duyệt, cho phép trang dùng micro. Trên iPhone, vào Cài đặt > Safari > Micrô.
- "Không nghe rõ giọng bạn": nói to, rõ, để điện thoại cách miệng khoảng 20–30 cm, tránh nơi ồn.
- Sửa nội dung bài học: mở index.html, tìm `const TOPICS`, thêm hoặc sửa câu trong danh sách, rồi tải lại file lên GitHub.
