## Challenge

Khi chúng ta mã hóa một cái gì đó, bản mã kết quả thường có các byte không phải là ký tự ASCII có thể in được. Nếu chúng ta muốn chia sẻ dữ liệu đã mã hóa của mình, thì việc mã hóa nó thành thứ gì đó thân thiện với người dùng hơn và dễ di chuyển hơn trên các hệ thống khác nhau là điều thường thấy.

Hệ thập lục phân có thể được sử dụng theo cách như vậy để biểu diễn các chuỗi ASCII. Đầu tiên, mỗi chữ cái được chuyển đổi thành một số thứ tự theo bảng ASCII (như trong thử thách trước). Sau đó, các số thập phân được chuyển đổi thành các số cơ số 16, hay còn gọi là hệ thập lục phân. Các số có thể được kết hợp với nhau, thành một chuỗi hex dài.

Bao gồm bên dưới là một cờ được mã hóa thành một chuỗi hex. Giải mã lại thành các byte để có được cờ.

63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d

Trong Python, bytes.fromhex()hàm có thể được sử dụng để chuyển đổi hex thành byte. .hex()Phương thức thể hiện có thể được gọi trên chuỗi byte để lấy biểu diễn hex.

## Solve

![image](https://github.com/user-attachments/assets/dfcd8fe0-958a-40cd-af0e-939f14653036)

- Flag :

`
crypto{You_will_be_working_with_hex_strings_a_lot}
`
