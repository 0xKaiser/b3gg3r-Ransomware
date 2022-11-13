# b$gg$r-Ransomware

Kịch bản: 
  Victim mắc b$gg$r thông qua việc tải 1 phần mềm phishing chứa nó. Trong bản demo sẽ dùng “Unikey.exe”. Quá trình chạy được thực hiện trên: Win 10 Pro, bản 1709 - 16299.125, vẫn bật Window Defender nhưng không có kết nối mạng.
  1. Khi Victim hiểu nhầm “unikey.exe”(b3gg3r.exe) với “unikey.exe”(bản chính chủ) và thực hiện chạy “unikey.exe”(b3gg3r.exe).
  2. Lúc đó, “b3gg3r.exe” sẽ tiến hành dò quét hết tất cả các file (ở đây để tăng tốc độ nên chỉ nhắm vào các file mục tiêu có đuôi “.txt, .doc, .pdf”) có trong “C:\\Users” và tiến hành nén với mật khẩu đã tạo bằng Fernet thành file mới với tên file nén theo định dạng  %tên file% + ”._b$gg$r_.rar”.
  3. Sau khi nén hết tất cả các file mục tiêu thành công, b3gg3r sẽ tạo file “Payload.txt” với nội dung là key đã mã hóa.
  4. Sau đó b3gg3r sửa Background của Desktop bằng hình ảnh kèm theo file và sẽ có tiếng “bíp” kéo dài 5s.
  5. Chương trình tiếp tục mở browser trỏ tới Url: 'https://bitcoin.org/en/' 
  6. Tiếp theo, “b3gg3r” mở file ransom_note.txt và sau cứ mỗi 5s nếu người dùng tắt thì sẽ tiếp tục hiện lên.
  7. Cuối cùng tiến hành lây lan đến tất cả ổ đĩa logic tìm được 
  8. Victim sau khi đọc file hướng dẫn, gửi file Payload đến Attacker sau khi xác nhận đã thực hiện thanh toán. Trên máy Attacker tiến hành tìm key bằng “Decrypt_Payload.py”
  9. Victim nhận key và tiến hành giải nén bằng “Extract.exe”

Để tránh việc chạy 1 cách vô tình, b3gg3r.py được lưu dưới dạng b3gg3r.txt.

Chức năng:
- b3gg3r.txt: Đây là con Ransomware, sau khi chạy xong sẽ có file Payload ngoài Desktop
- Decrypt_Payload.py: Lấy key từ file Payload
- Extract.txt: file thuốc giải với input là key được từ file Decrypt_Payload.py

Trước khi chạy:
  “b3gg3r.py” sẽ đươc chuyển đổi sang định dạng file executable bằng “pyinstaller” thông qua cú pháp “pyinstaller –onefile b3gg3r.py”. Tham số “--one file” nhằm mục đích để file “.exe” có thể chạy mà không cần sự hỗ trợ của tệp khác và để mặc định chạy trên console vì lí do nghiên cứu - có thể kiểm tra xem “unikey.exe” sẽ chạy như thế nào.

Sau khi chạy xong:
  Do “unikey.exe” đã được tạo trong thư mục Startup nên dù cho đã giải nén tất cả các file mục tiêu rồi hay chưa thì nó vẫn sẽ chạy, nhưng do có file “Payload.txt” nên sẽ không nén lại lần nữa. Nếu Victim xóa file này khi chưa giải nén những file nạn nhân thì rất khó để có thể lấy lại được dữ liệu (vì bị nén 2 lần và pass file nén cũ đã mất).
  
Mặt khác nếu máy Victim đã kết nối mạng thì Window Defender ngay lập tức có thể phát hiện và cách ly ngay “b$gg$r”.

***

> Đây là project phục vụ bài tập nhóm của mình.
