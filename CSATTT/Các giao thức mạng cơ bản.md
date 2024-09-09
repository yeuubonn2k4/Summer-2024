### Mục đích: 

Giới thiệu các khái niệm mạng cơ bản trong môi trường Linux, bao gồm giao thức ARP, việc sử dụng lệnh ping và giới thiệu về TCP/IP. Tiện ích tcpdump được sử dụng để xem lưu lượng mạng

### Yêu cầu đối với sinh viên:

Có kiến thức cơ bản về hệ điều hành Linux, mô hình mạng khách/chủ, các giao thức cơ bản của mạng TCP/IP.

#### Nội dung thực hành

- Khởi động bài lab:

Vào terminal, gõ: 
 `labtainer network-basics`

 (chú ý: sinh viên sử dụng mã Sinh viên của mình để nhập thông tin email người thực hiện bài lab khi có yêu cầu, để sử dụng khi chấm điểm)

Sau khi khởi động xong hai terminal ảo sẽ xuất hiện, 1 terminal mang tên “box1” đóng vai trò máy tính 1 và 1 terminal mang tên “box2” đóng vai trò máy tính 2, hai máy tính kết nối với nhau qua mạng ảo có thể coi như kết nối qua dây cáp Ethernet .

##### Nhiệm vụ 1: Khám phá

Trên terminal box1 và box2 sử dụng lệnh:

ip addr 

để kiểm tra địa chỉ IP trên cả hai máy tính để làm quen với các giao diện mạng. Chúng ta sẽ tập trung vào mục thứ hai trong mỗi kết quả hiển thị từ lệnh ip addr, tức là các mục eth0. Giá trị link/ether, ví dụ như giá trị 02:42:ac:00:00:03, là địa chỉ MAC của giao diện mạng xuất hiện trong các tiêu đề gói Ethernet. Thông thường, các địa chỉ MAC được gắn với phần cứng vật lý, ví dụ như giao diện Ethernet. Trong bài thực hành này, mạng là ảo, và địa chỉ MAC cũng là ảo.

Địa chỉ khác cần quan tâm được gắn nhãn inet, ví dụ như 172.0.0.3/24. Đây là địa chỉ IPv4 xuất hiện trong tiêu đề gói IP. Trong ví dụ này, /24 cho biết subnet liên kết với giao diện này là 172.0.0, và địa chỉ của máy tính trên subnet đó là 3. Giá trị theo sau dấu gạch chéo cho bạn biết có bao nhiêu bit trong địa chỉ IP 32 bit được sử dụng để đặt tên cho subnet. Số bit còn lại được sử dụng để đặt tên cho thiết bị trên subnet.

Các địa chỉ IP được mô tả ở trên cho phép các máy tính đặt tên cho nhau, và do đó có thể giao tiếp. Tuy nhiên, ở tầng thấp nhất, tức là tầng liên kết (link layer) giao tiếp trực tiếp với phương tiện vật lý hoặc ảo, các địa chỉ MAC được sử dụng để giao tiếp. Vì vậy, cần có cách để dịch địa chỉ IP sang địa chỉ MAC.

##### Nhiệm vụ 2: ARP

Giao thức ARP (Address Resolution Protocol) được sử dụng để ánh xạ địa chỉ IP sang địa chỉ MAC. Trên box2, sử dụng lệnh:

arp -a

để xem bảng ánh xạ hiện tại. Lưu ý rằng không có gì hiển thị vì bảng ARP đang trống. Khi hai máy tính của chúng ta mới khởi động, chúng không biết địa chỉ MAC của nhau.

Trên box1, khởi động chương trình tcpdump để quan sát lưu lượng mạng:

sudo tcpdump -vv -n -e -i eth0

Các tùy chọn cho lệnh tcpdump này là:

-vv – Cung cấp thông tin chi tiết.

-n – Không thực hiện tra cứu DNS ngược, chỉ hiển thị các địa chỉ IP.

-e – Hiển thị địa chỉ MAC của Ethernet.

-i eth0 – Hiển thị lưu lượng trên giao diện eth0.

Bạn có thể nhận thấy một số lưu lượng được hiển thị không liên quan đến các hành động bạn thực hiện, ví dụ như các gói “router solicitation” hoặc gói flow. Bỏ qua những gói này. Trên box2, sử dụng lệnh ping để ping box1:

ping 172.0.0.2 -c 2

Quan sát lưu lượng trong tcpdump. Bạn sẽ thấy yêu cầu ARP từ box2 yêu cầu địa chỉ MAC của thiết bị xử lý lưu lượng đến địa chỉ IP của box1. Lưu ý rằng địa chỉ MAC đích trong yêu cầu ARP là ff:ff..., là một thông điệp broadcast được tất cả các giao diện Ethernet trên mạng LAN nhìn thấy. Và bạn sẽ thấy phản hồi ARP từ box1. Sau khi hai box ánh xạ địa chỉ IP với địa chỉ MAC, chúng có thể trao đổi các gói tin ở tầng mạng. Trong trường hợp này, bạn sẽ thấy các gói ICMP. Gói đầu tiên là yêu cầu ICMP echo từ box2 đến box1. Đây là một "ping". Gói tiếp theo là phản hồi ICMP echo từ box1.

Sử dụng ctrl-c để thoát khỏi tcpdump trên box1. Sau đó sử dụng lệnh arp -a trên cả hai box để xem nội dung hiện tại của bảng ARP. Những mục ARP này cho phép hai box định địa chỉ cho nhau mà không cần lặp lại yêu cầu/phản hồi ARP.

##### Nhiệm vụ con 2.1: Tin tưởng vào phản hồi ARP

Việc sử dụng ARP để ánh xạ địa chỉ IP với địa chỉ MAC yêu cầu một mức độ tin tưởng nhất định. Khi một box hỏi, "Tôi nên gửi gói tin cho địa chỉ MAC nào cho địa chỉ IP này?", nó đang tin rằng chỉ box đúng sẽ phản hồi. Xem bài thực hành về ARP spoofing để biết ví dụ về cách niềm tin này có thể bị đặt sai chỗ.

##### Nhiệm vụ con 2.2: Giao tiếp ngoài subnet

Bạn đã quan sát thấy cách ARP cho phép các máy tính trên một subnet chung giao tiếp bằng cách sử dụng địa chỉ IP được ánh xạ với địa chỉ MAC. Nhưng còn các máy tính không cùng chia sẻ một subnet thì sao? Loại giao tiếp này yêu cầu sử dụng chuyển tiếp gói tin và định tuyến, ví dụ như thông qua thành phần gateway. Xem bài thực hành về cơ bản định tuyến để biết các ví dụ về giao tiếp giữa các máy tính không chia sẻ một subnet.

###### Nhiệm vụ 3: TCP

Trong phần này, chúng ta sẽ xem xét ngắn gọn một số gói IP trong một phiên TCP, cụ thể là "bắt tay ba bước". Khởi động lại tcpdump trên box1, lần này không sử dụng tùy chọn -e:

sudo tcpdump -vv -n -i eth0

Sau đó, trên box2, khởi tạo một phiên SSH tới box1. Chúng ta sẽ không thực sự hoàn tất việc đăng nhập, chỉ đơn giản muốn xem xét phần đầu của phiên:

ssh 172.0.0.2

Điều này dẫn đến các gói IP bao gồm giao thức TCP, cho chúng ta biết rằng giao thức TCP đang được sử dụng. Thông tin địa chỉ trong gói đầu tiên, ví dụ:

172.0.0.3.34104 > 172.0.0.2.22

cho chúng ta biết gói tin được gửi từ box2. Số cuối cùng trong địa chỉ của box2, trong trường hợp này là 34014, là một cổng tạm thời của TCP sẽ được sử dụng cho phiên này. Số cuối cùng trong địa chỉ của box1 là 22, là cổng được sử dụng bởi giao thức SSH. Giá trị Flags trong dấu ngoặc vuông trên gói đầu tiên là [S], cho thấy đây là một gói SYN, tức là gói đầu tiên trong ba gói bắt tay để khởi tạo một phiên TCP. Gói thứ hai là từ box1 đến box2. Lưu ý các số cổng. Giá trị Flags trên gói thứ hai là [S.], cho thấy đây là một gói SYN-ACK, tức là gói thứ hai trong bắt tay. Gói thứ ba hoàn thành bắt tay với một gói ACK được gửi từ box2 đến box1. Giá trị Flags chỉ là một dấu chấm, thể hiện không có cờ nào.

Giá trị seq 1, ack 1 trong gói thứ ba cho thấy đây là ack và rằng số thứ tự của phiên TCP bắt đầu từ 1. Điều này hoàn thành bắt tay và các gói tiếp theo là một phần của phiên đáng tin cậy trong đó giao thức TCP đảm bảo rằng các gói tin không bị mất và được sắp xếp đúng thứ tự để giao cho ứng dụng, trong trường hợp này là một SSH client và SSH server. Khái niệm về việc các gói tin bị mất hoặc sai thứ tự có thể dường như khó xảy ra khi xem xét ví dụ đơn giản về hai box của chúng ta. Nhưng hãy xem xét các máy tính ở hai bên đối diện của thế giới trao đổi thông tin bằng cách sử dụng các đường dẫn router có thể thay đổi trong thời gian phiên TCP.

Kết thúc bài lab:
Trên terminal đầu tiên sử dụng câu lệnh sau để kết thúc bài lab:
stoplab network-basics

Khi bài lab kết thúc, một tệp zip lưu kết quả được tạo và lưu vào một vị trí được hiển thị bên dưới stoplab.
 

###### Khởi động lại bài lab:

Trong quá trình làm bài sinh viên cần thực hiện lại bài lab từ đầu, dùng câu lệnh:

labtainer -r network-basics

 
