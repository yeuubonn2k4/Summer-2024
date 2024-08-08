## Chalenge

XOR là toán tử bitwise trả về 0 nếu các bit giống nhau và trả về 1 nếu không giống nhau. Trong sách giáo khoa, toán tử XOR được ký hiệu là ⊕, nhưng trong hầu hết các thử thách và ngôn ngữ lập trình, bạn sẽ thấy dấu mũ ^được sử dụng thay thế.

![image](https://github.com/user-attachments/assets/2085a671-e690-4d0b-824c-40cd188401ae)

Đối với các số nhị phân dài hơn, chúng ta XOR từng bit: 0110 ^ 1010 = 1100. Chúng ta có thể XOR các số nguyên bằng cách đầu tiên chuyển đổi số nguyên từ thập phân sang nhị phân. Chúng ta có thể XOR các chuỗi bằng cách đầu tiên chuyển đổi từng ký tự thành số nguyên biểu diễn ký tự Unicode.

Cho chuỗi label, XOR từng ký tự với số nguyên 13. Chuyển đổi các số nguyên này trở lại thành chuỗi và gửi cờ dưới dạng crypto{new_string}.

Thư viện Python pwntoolscó một xor()hàm tiện lợi có thể XOR dữ liệu có nhiều kiểu và độ dài khác nhau. Nhưng trước tiên, bạn có thể muốn triển khai hàm của riêng mình để giải quyết vấn đề này.

## Solve

- ở đây chúng ta phải phân tích label thành mã nhị phân rồi XOR rồi phân tích lại ra ASCII

- Sau khi phan tich label ra ma nhi phan roi XOR ta được 1 dãy nhị phân rồi decode lại ASCII ta được
 
- ![image](https://github.com/user-attachments/assets/6f85b1f0-b8fc-4d9a-8f73-37720be82ae4)

- Flag

`
crypto{aloha}
`
