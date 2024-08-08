## Challenge

- Các hệ thống mật mã như RSA hoạt động trên các con số, nhưng các thông điệp được tạo thành từ các ký tự. Chúng ta nên chuyển đổi các thông điệp của mình thành các con số như thế nào để có thể áp dụng các phép toán?

Cách phổ biến nhất là lấy các byte thứ tự của thông điệp, chuyển đổi chúng thành hệ thập lục phân và nối lại. Điều này có thể được hiểu là một số cơ số 16/hệ thập lục phân, và cũng được biểu diễn ở hệ cơ số 10/hệ thập phân.

tin nhắn: XIN CHÀO

các byte ascii: [72, 69, 76, 76, 79]

các byte hex: [0x48, 0x45, 0x4c, 0x4c, 0x4f]

cơ số 16: 0x48454c4c4f

cơ số 10: 310400273487

Thư viện PyCryptodome của Python triển khai điều này bằng các phương thức bytes_to_long()và long_to_bytes(). Trước tiên, bạn sẽ phải cài đặt PyCryptodome và nhập nó bằng from Crypto.Util.number import *. Để biết thêm chi tiết, hãy kiểm tra FAQ .

Chuyển đổi số nguyên sau trở lại thành một thông điệp:

11515195063862318899931685488813747395775516287289682636499965282714637259206269

## Solve

![image](https://github.com/user-attachments/assets/3fe070f7-566c-4bc9-91ad-f5dca52b9aaa)

- Flag :

`
crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
`
