## Challenge

Đối với một vài thử thách tiếp theo, bạn sẽ sử dụng những gì vừa học được để giải một số câu đố XOR khác.

Tôi đã ẩn một số dữ liệu bằng XOR với một byte duy nhất, nhưng byte đó là bí mật. Đừng quên giải mã từ hex trước.

73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d

## Solve

![image](https://github.com/user-attachments/assets/2b1d508f-89fb-471e-a90b-06b050e177fa)

- Sau khi decode xong ta duoc zay, ma de bai bao chi XOR cac ki tu voi 1 byte duy nhat

- De y Flag luon la crypto

- Nen chac chan XOR voi byte gi do de ra c

- Vay la ta tim duoc byte bi ma do la 00010000

- Lay 33 byte ma nay XOR voi ma ban dau decode duoc ta duoc ma nhi phan cua Flag

![image](https://github.com/user-attachments/assets/c96fed30-28a1-46a9-bc9a-f25817a4bfb1)

- Decode ta duoc

![image](https://github.com/user-attachments/assets/86919240-8dc5-44f5-b173-8d09a31451a0)


`
crypto{0x10_15_my_f4v0ur173_by7e}
`
