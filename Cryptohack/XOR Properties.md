## Challenge

Trong thử thách trước, bạn đã thấy XOR hoạt động như thế nào ở cấp độ bit. Trong thử thách này, chúng ta sẽ đề cập đến các thuộc tính của phép toán XOR và sau đó sử dụng chúng để hoàn tác chuỗi các phép toán đã mã hóa một cờ. Việc có được trực giác về cách thức hoạt động của phép toán này sẽ giúp ích rất nhiều khi bạn tấn công các hệ thống mật mã thực sau này, đặc biệt là trong danh mục mã hóa khối.

Có bốn thuộc tính chính mà chúng ta nên cân nhắc khi giải quyết các thử thách bằng toán tử XOR

![image](https://github.com/user-attachments/assets/33a778aa-cb28-4af8-86a0-75a319437a5a)

Hãy phân tích điều này. Giao hoán có nghĩa là thứ tự của các phép toán XOR không quan trọng. Kết hợp có nghĩa là một chuỗi các phép toán có thể được thực hiện mà không cần thứ tự (chúng ta không cần phải lo lắng về dấu ngoặc). Danh tính là 0, vì vậy XOR với 0 "không làm gì cả", và cuối cùng, một cái gì đó được XOR với chính nó sẽ trả về số không.

Hãy đưa điều này vào thực tế! Dưới đây là một loạt các đầu ra trong đó ba khóa ngẫu nhiên đã được XOR với nhau và với cờ. Sử dụng các thuộc tính trên để hoàn tác mã hóa ở dòng cuối cùng để có được cờ.

KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313

KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e

KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1

Flag ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf

## Solve

- Theo tinh chat ta se tim Flag = (flag^key1^key2^key3) / (key 1 ^(key 2^key3))

![image](https://github.com/user-attachments/assets/7bcaa52a-8370-4610-a718-ccf47e99322e)

- Ta co key 1 ^ key 2 ^ key 3 = 0110011110011100111000010010010101010100111001010101011110101101101000001110001110001111001011100101001011110001001001101110010101000010010000001011001001010111011011001000001111000100000110010110110011010010

- ![image](https://github.com/user-attachments/assets/334df5c2-2c95-4943-a61f-aab2353a9a76)

Chon Solve 1 XOR ??? = 2

Ta duoc day flag la : 0110001101110010011110010111000001110100011011110111101101111000001100000111001001011111011010010011010101011111011000010111001101110011001100000110001100110001011000010111010000110001011101100011001101111101

- Decode ta duoc flag la

![image](https://github.com/user-attachments/assets/c1fd9fb7-ecb3-414e-942a-b144547c2477)

`
crypto{x0r_i5_ass0c1at1v3}
`
