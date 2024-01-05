Front-End: React

Back-End: Laravel

API -> Authentication -> Token (JWT)

Request get Data: Gửi token thông qua Header (Authorization: Bearer <token>)

Server -> Kiểm tra token có hợp lệ hay không? -> Decode Payload -> Truy vấn Database trả về dữ liệu

## Bảo mật Token

AccessToken => Nếu bị đánh cắp => Hacker khai thác dựa vào Token

-> Giải pháp: Hạ thấp thời gian sống của AccessToken -> Gây phiền phức cho người dùng

-> Cần bổ sung: RefreshToken -> Thời gian sống lâu hơn -> Dùng để cấp lại AccessToken mới khi AccessToken cũ hết hạn

-> Khi logout -> Thêm token vào Blacklist -> Khi authorization -> Cần kiểm tra token có trong blacklist

-   Tính hợp lệ
-   Thời gian sống
-   Có trong blacklist hay không?

## Các vấn đề khi sử dụng Refresh Token

-   Refresh Token hết hạn => Client xử lý logout --> Call API /logout
-   Cấp lại accessToken mới bằng Refresh Token --> accessToken cũ vẫn hoạt động được
    Giải pháp: Khi cấp lại accessToken mới --> Thêm accessToken cũ vào Blacklist
