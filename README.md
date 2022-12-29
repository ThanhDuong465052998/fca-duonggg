Repo Này Là Một Nhánh Rẽ Từ Repo Chính Và Thường Sẽ Có Các Tính Năng Mới Được Tích Hợp Nhanh Hơn So Với Repo Chính (Và Cũng Có Thể Kèm Theo Một Số Lỗi).
Xem Repo Chính [here](https://github.com/Schmavery/facebook-chat-api).
# Api Cho ChatBot Messenger
Facebook Hiện Có API Chính Thức Cho Trò Chuyện Bot [here](https://developers.facebook.com/docs/messenger-platform).

API Này Là Cách Duy Nhất Để Tự Động Hóa Các Chức Năng Trò Chuyện Trên Tài Khoản Người Dùng. Chúng Tôi Làm Điều Này Bằng Cách Giả Lập Trình Duyệt. Điều Này Có Nghĩa Là Thực Hiện Chính Xác Các Yêu Cầu GET/POST Và Lừa Facebook Suy Nghĩ 

# Lưu ý:
 Chúng Tôi Không Chịu Trách Nhiệm Nếu Tài Khoản Của Bạn Bị Cấm Vì Các Hoạt Động Spam Như Gửi Nhiều Tin Nhắn Cho Những Người Bạn Không Biết, Gửi Tin Nhắn Rất Nhanh, Gửi Các URL Có Vẻ Spam, Đăng Nhập Và Đăng Xuất Rất Nhanh... Hãy Là Công Dân Có Trách Nhiệm Của Facebook. 
# Cài đặt
Nếu Bạn Muốn Sử Dụng, Hãy Vô Terminal Hoặc Command Promt Nhập:
```bash
npm install fca-duong
```
Nó Sẽ Tải Xuống Từ Kho NPM

## Tải Bản Mới Nhất Hoặc Update
Nếu Bạn Muốn Sử Dụng Phiên Bản Mới Nhất Hay Cập Nhật Thì Hãy Vô Terminal Hoặc Command Promt Nhập:
```bash
npm install fca-duong@latest
```

## Nếu Bạn Muốn Test Api
Lợi Ích Cho Việc Này Thì Bạn Sẽ Không Tốn Thời Gian Pay Acc Và Có Acc. Hãy Sử Dụng Với Tài Khoản Thử Nghiệm [Facebook Whitehat Accounts](https://www.facebook.com/whitehat/accounts/).

## Ví dụ sử dụng
```javascript
const login = require("fca-duong");

// Create simple echo bot
login({email: "FB_EMAIL", password: "FB_PASSWORD"}, (err, api) => {
    if(err) return console.error(err);

    api.listen((err, message) => {
        api.sendMessage(message.body, message.threadID);
    });
});
```

Kết quả:

<img width="517" alt="screen shot 2016-11-04 at 14 36 00" src="https://cloud.githubusercontent.com/assets/4534692/20023545/f8c24130-a29d-11e6-9ef7-47568bdbc1f2.png">


## Tài liệu

Bạn Có Thể Đọc Các Api Tại: [here](DOCS.md).

## Lưu Lại Thông Tin Đăng Nhập.
Để Lưu Lại Thì Bạn Cần 1 Apstate Kiểu (Cookie, etc,..) Để Lưu Lại Hoặc Là Sử Dụng Mã Login Như Trên Để Đăng Nhập !

Và Chế Độ Này Đã Có Sẵn Trong 1 Số Bot Việt Nam Nên Bạn Cứ Yên Tâm Nhé !

### Hướng Dẫn Với Appstate
```javascript
const fs = require("fs");
const login = require("fca-duong");

var credentials = {email: "FB_EMAIL", password: "FB_PASSWORD"}; // thông tin tk

login(credentials, (err, api) => {
    if(err) return console.error(err);
    // đăng nhập
    fs.writeFileSync('appstate.json', JSON.stringify(api.getAppState())); //tạo appstate
});
```
Hoặc Dễ Dàng Hơn ( Chuyên Nghiệp ) Bạn Có Thể Dùng => Bạn Có Thể Đọc Các Api Tại: [c3c-fbstate](https://github.com/c3cbot/c3c-fbstate) Để Lấy Fbstate Và Đổi Tên Nó Thành Apstate 
