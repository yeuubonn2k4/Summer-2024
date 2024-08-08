## Challenge

Một lược đồ mã hóa phổ biến khác là Base64, cho phép chúng ta biểu diễn dữ liệu nhị phân dưới dạng chuỗi ASCII bằng bảng chữ cái gồm 64 ký tự. Một ký tự của chuỗi Base64 mã hóa 6 chữ số nhị phân (bit), do đó 4 ký tự của Base64 mã hóa ba byte 8 bit.

Base64 được sử dụng phổ biến nhất trực tuyến, do đó dữ liệu nhị phân như hình ảnh có thể dễ dàng được đưa vào các tệp HTML hoặc CSS.

Lấy chuỗi hex bên dưới, g

![image](https://github.com/user-attachments/assets/d39ccfdd-52b1-472e-8d4d-93827ef65762)

- Bài này khá đặc biệt khi mà giải mã từ Hex thành ASCII rồi lấy cái ASCII (nom khá xấu) mã hóa Base64 thành Base64 ta được flag

- Flag :

`
crypto/Base+64+Encoding+is+Web+Safe/
`
