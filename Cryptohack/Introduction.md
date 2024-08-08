Trong tất cả các ngôn ngữ lập trình hiện đại, Python 3 nổi bật là lý tưởng để viết nhanh các tập lệnh và tấn công mật mã. Để biết thêm thông tin về lý do tại sao chúng tôi nghĩ Python rất tuyệt vời cho việc này, vui lòng xem Câu hỏi thường gặp .

Chạy tập lệnh Python đính kèm và nó sẽ xuất ra cờ của bạn.

## 1 số câu hỏi thường gặp

### Tôi nên sử dụng ngôn ngữ lập trình nào?

Hầu hết các thử thách của chúng tôi đều được viết bằng Python 3 và chúng tôi sử dụng rộng rãi thư viện PyCryptodome để thực hiện các hoạt động mã hóa phổ biến. Một số thử thách nâng cao hơn được viết bằng Sage 9 (dựa trên Python 3).

Python là một ngôn ngữ tuyệt vời để tạo nguyên mẫu nhanh cho mật mã. Nó dễ đọc và có hỗ trợ gốc cho các số nguyên lớn; các mô-đun toán học mạnh mẽ gọi trực tiếp vào mã C để có tốc độ tối đa (ví dụ gmpy2 ); thậm chí là toán tử lũy thừa mô-đun tích hợp ( pow()). Cuối cùng, SageMath là công cụ nguồn mở có hỗ trợ tinh vi nhất cho mật mã hiện đại và được xây dựng trên Python.

Bạn có thể viết giải pháp của mình bằng một ngôn ngữ khác nhưng sẽ khó hơn.

### Làm thế nào tôi có thể cài đặt những công cụ tôi cần?

Chúng tôi cung cấp một hình ảnh Docker chính thức có chứa tất cả các công nghệ được đề xuất đã cài đặt. Nếu bạn có Docker , chỉ cần chạy:docker run -p 127.0.0.1:8888:8888 -it hyperreality/cryptohack:latest

Ngoài ra, nếu bạn chưa có Python, bạn có thể cài đặt nó bằng cách làm theo hướng dẫn này . Tiếp theo, bạn sẽ cần cài đặt một số gói Python:

Tiếng Việt

gmpy2

công cụ pwntools

Trên Linux và Mac, điều này có thể đơn giản như mở terminal rồi chạy pip install PyCryptodome gmpy2 pwntools. Trước tiên, bạn có thể cần cài đặt trình quản lý gói Pip ( sudo apt install python3-piptrên Ubuntu) rồi cài đặt gmpy2 dependency ( sudo apt install libgmp-dev libmpc-dev libmpfr-devtrên Ubuntu). Trên Windows, hãy xem hướng dẫn này để biết cách sử dụng trình quản lý gói Python pip.

Sau khi cài đặt hoàn tất, hãy mở trình thông dịch Python và chạy from Crypto.Util import *; strxor.strxor(b"C", b"H"); kết quả sẽ là b'\x0b'. Nếu bạn gặp lỗi, hãy xem tại đây để biết mẹo giải quyết.

Sage có thể khó cài đặt hơn (đặc biệt là trên Windows) nhưng nó chỉ được sử dụng cho một số thử thách nâng cao. Trên Ubuntu Linux, nó sẽ dễ như apt install sagemath. Kiểm tra tại đây để biết thêm hướng dẫn.

### Tôi có thể chia sẻ giải pháp của mình không?

Sau khi bạn giải quyết một thử thách, liên kết "Giải pháp" sẽ xuất hiện bên cạnh thử thách. Trên trang đó, bạn sẽ có thể đăng các tập lệnh giải pháp của mình dưới dạng GitHub Gist riêng tư và đọc và bình chọn cho các tập lệnh do người chơi khác gửi.

Để tránh làm hỏng các thử thách dành cho người mới, chúng tôi yêu cầu bạn chỉ gửi giải pháp bằng tính năng chúng tôi đã cung cấp trên trang web này. Vui lòng không đăng giải pháp hoặc bài viết bên ngoài nền tảng. Tuy nhiên, đối với các thử thách "Người mới bắt đầu" và các thử thách có giá trị 25 điểm trở xuống, chúng tôi sẽ có ngoại lệ - hãy thoải mái thảo luận công khai.

### Tôi có thể chơi thử thách ở chế độ Block Cipher như thế nào?

Các thử thách mã hóa khối được xây dựng trên các ứng dụng web. Mỗi thử thách cung cấp cho bạn mã nguồn của vấn đề và các biểu mẫu để tương tác với các hàm được xác định. Để tự động hóa giải pháp của mình, bạn có thể gọi các hàm trực tiếp bằng cách gửi dữ liệu dưới dạng tham số GET và nhận phản hồi JSON, ví dụ:

$ curl http://aes.cryptohack.org/ecb_oracle/encrypt/00000000000000000000000000000000/
{"ciphertext":"8b6a083e36541cb59840e2242de73e11e84bfaeb5722f80253120ab21da890037bbbcc054419106657728a2d4d368f6e"}
Để viết toàn bộ câu trả lời của bạn, chúng tôi khuyên bạn nên sử dụng gói Python Requests (thay vì cURL).

### Tôi có thể chơi thử thách tương tác như thế nào?

Một số thử thách trên CryptoHack được thiết kế theo hướng động. Để giải quyết vấn đề, bạn phải thu thập và gửi dữ liệu để khai thác điểm yếu trong quá trình triển khai.

Các thử thách giới thiệu cung cấp các tập lệnh để kết nối và tự động hóa các giải pháp của bạn cho các thử thách này, hoạt động trên mọi nền tảng bằng cách sử dụng mô-đun Python Pwntools . Xem hướng dẫn này để biết cách sử dụng. Đây là cách chúng tôi khuyến nghị nhất để giải quyết các thử thách này; có những giải pháp thay thế nhưng chúng luôn phức tạp hơn so với việc sử dụng pwntools, vốn đã trở thành một phần chính của CTF.

Để giao tiếp với máy chủ, dữ liệu của bạn phải được gửi dưới dạng đối tượng JSON. Mỗi thử thách sẽ chỉ định các giá trị khóa bạn cần gửi và các giá trị sẽ là dữ liệu bạn đang làm việc. Ví dụ, giả sử bạn muốn gửi một số dữ liệu đến máy chủ để mã hóa, bạn có thể gửi đối tượng {"encrypt": "656e63727970746d796d657373616765"}và sau đó máy chủ sẽ trả lời {"encrypted_data": "0e0b1a191c091f080006000a18041e0e"}.

Mã nguồn cho những thử thách tương tác này thường sẽ được cung cấp. challengeHàm trong Challengelớp sẽ được gọi trên đầu vào định dạng JSON của bạn và máy chủ sẽ xử lý nó theo đó.

### Tôi có thể chạy thử thách tương tác cục bộ không

Nguồn cho utils.listenermô-đun chạy thử thách động có sẵn tại đây . Để chạy thử thách cục bộ với nó, hãy đặt tệp trình nghe vào một utils/thư mục rồi chạy tệp thử thách bằng Python. Sau đó, bạn có thể kết nối với cổng thử thách trên máy chủ cục bộ của riêng bạn.

Ví dụ:

cd $DIRECTORY_WITH_CRYPTOHACK_CHALLENGES
mkdir utils
wget https://cryptohack.org/static/listener.py
mv listener.py utils
python $CHALLENGE_NUMBER.py

### So sánh với Cryptopals và MysteryTwister C3 thì thế nào?
Cryptopals rất tuyệt và một số thách thức của chúng tôi là sự điều chỉnh của họ. Sự khác biệt chính là chúng tôi hướng đến việc cung cấp một môi trường trò chơi hóa hơn, nơi bạn không phải lập trình mọi thứ từ đầu—trừ khi bạn muốn.

MysteryTwister C3 cung cấp nhiều thử thách về mật mã bao gồm nhiều chủ đề khác nhau theo cách ít mang tính trò chơi hơn. Hầu hết các thử thách của họ tập trung nhiều hơn vào thiết kế mật mã và các khía cạnh mang tính giáo dục (như hướng dẫn về phân tích mật mã khác biệt) và bao gồm nhiều thử thách với các quy trình và máy móc lịch sử hoặc "ít được biết đến" (như HandyCipher hoặc Sigaba).

### Bạn có API không?

Có, bạn có thể lấy thông tin về người dùng (ví dụ tên là USER) ở định dạng JSON bằng cách thực hiện yêu cầu sau:

$ curl https://cryptohack.org/api/user/USER/
  {                            
    "quốc gia": "gb",
    "first_bloods": 0,
    "tham gia": "22 tháng 7 năm 2021",
    "cấp độ 1,
    "xếp hạng": 17935,
    "điểm": 3,
    "solved_challenges": [
    {
      "category": "Giới thiệu",
      "ngày": "22 tháng 7 năm 2021",        
      "tên": "Rắn lớn",
      "điểm": 3,
      "giải quyết": 10000
    },
    ],
    "user_count": 26912,
    "tên người dùng": "NGƯỜI DÙNG",
    "trang mạng": ""
}

