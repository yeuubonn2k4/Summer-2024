>Nếu như ở ngoài đời nhắc đến "ồ ạt" thì chúng ta thường nghĩ đến những cơ lũ thì trong An toàn thông tin nó lại gợi nhắc đến 2 loại tấn công đó chính là Tấn công từ chối dịch vụ (DoS) và Tấn công từ chối dịch vụ phân tán (DDoS). Nhiều người vẫn hay thường nhầm lẫn 2 khái niệm này nên hôm nay haỹ cùng mình làm rõ 2 khái niệm này nha. ^^

***DoS là gì?***

**Tấn công từ chối dịch vụ (Denial of Service – DoS)** là dạng tấn công nhằm ngăn chặn người dùng hợp pháp truy nhập các tài nguyên mạng

+ Phân loại : Nó được chia làm 2 loại:

*Tấn công logic* : dạng tấn công khai thác các lỗi phần mềm làm dịch vụ ngừng hoạt động hoặc làm giảm hiệu năng hệ thống.

Ví dụ : tấn công DoS sử dụng sâu SQL Slammer là dạng tấn công logic khi chúng        tấn công khai thác lỗi tràn bộ đệm trong phần mềm.

*Tấn công ngập lụt (Flooding attack)* : kẻ tấn công gửi một lượng lớn yêu cầu gây cạn kiệt tài nguyên hệ thống hoặc bang thông đường truyền mạng.

+ Có rất nhiều kỹ thuật tấn công DoS được sử dụng nhưng thường chúng ta sẽ gặp SYN Flood (khai thác điểm yếu trong thủ tục bắt tay 3 bước), Smuft (sử dụng giao thức điều khiển truyền ICMP và kiểu phát quảng bá có định hướng để gây ngập lụt đường truyền mạng của máy nạn nhân)……

+ Vậy để phòng chống chúng như thế nào?

*SYN Flood* : Sử dụng kỹ thuật lọc địa chỉ giả mạo (kỹ thuật phải chỉnh sửa giao thức TCP/IP nhằm không cho phép kẻ tấn công giả mạo địa chỉ), giảm thời gian chờ (SYN-RECEIVED Timer), sử dụng tưởng lửa (Firewall) và Proxy…


*Smuff* : Cấu hình các máy trong mạng và router không trả lời các yêu cầu ICMP hoặc các yêu cầu phát quảng bá, cấu hình các router không chuyển tiếp yêu cầu ICMP gửi đến các địa chỉ quảng bá….

***DDoS là gì?***

DDoS (Distributed Denial of Service – DDoS) là loại tấn công DoS đặc biệt gây ngập lụt các máy nạn nhân với 1 lượng rất lớn các yêu cầu kết nối giả mạo.

	Vậy điểm khác nhau giữa DoS và DDoS chính là phạm vi tấn công. 

-	DoS : số lượng máy tấn công thường *tương đối nhỏ* (chỉ gốm 1 số ít máy tại một hoặc một số địa điểm).

-	DDoS : số lượng máy tham gia tấn công thường *rất lớn* (có thể lên đến hang nghìn hoặc hang trăm nghìn máy và thậm chí có thể đến từ nhiều vị trí địa lý khác nhau trên toàn cầu).

+ Phân loại tấn công DDoS : chia làm 2 loại.

*Tấn công DDoS trực tiếp* : các yêu cầu tấn công được các máy tấn công gửi trực tiếp đến máy nạn nhân. (chi tiết mọi người có thể tự tìm hiểu)

*Tấn công DDoS gián tiếp* : các yêu cầu tấn công được gửi đến các máy phản xạ và sau đó gián tiếp chuyển đến máy nạn nhân.

+ Với phạm vi tấn công rộng hơn DoS rất nhiều vậy chúng ta nên phòng chống DDoS như thế nào? Chúng ta cần kết hợp nhiều biện pháp, sau đây là một số biện pháp mọi người có thể tham khảo:

1.	Sử dụng các phần mềm quét virus và các phần mềm độc hại khác nhằm loại bỏ bot, zombie, slave khỏi các hệ thống máy tính.

2.	Sử dụng các hệ thống lọc đặt trên các router, tường lửa của các nhà cung cấp dịch vụ Internet.

3.	Sử dụng các hệ thống giám sát, phát hiện bất thường nhằm phát hiện sớm các dấu hiệu của tấn công DDoS.

4.	Sử dụng tường lửa để chặn tạm thời các cổng dịch vụ bị tấn công.

Vậy là mọi người đã hiểu được sự khác nhau như thế nào giữa DoS và DDoS cũng như biết được các biện pháp phòng cũng như chống nếu như bản than có thấy được các dấu hiệu của các loại tấn công này. Bài viết của mình đến đây xin được hết. Cảm ơn mọi người đã dành thời gian đọc bài viết của mình.

#Cre nhiều tài liệu tham khảo

![image](https://github.com/user-attachments/assets/a76c2139-93a9-42f5-8e44-a8d8195789d7)

![image](https://github.com/user-attachments/assets/936ccc4a-8718-4f95-b0e6-ead135be6301)

Tấn công DDoS trực tiếp

![image](https://github.com/user-attachments/assets/aa22f125-e0dd-4af1-b606-4a200a3abe5e)

Tấn công DDoS gián tiếp

![image](https://github.com/user-attachments/assets/03a1870b-bc9f-49ec-a84e-784ef1b03930)

DoS smuff

![image](https://github.com/user-attachments/assets/e8bf8031-aa23-4c5d-9480-41c41ef79a64)

DoS SYN Flood
