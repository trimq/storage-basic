#Báo cáo tháng 4

##Mục lục:

###I.Tìm hiểu về VMware workstation.
###II.Đặt IP tĩnh và động.
###III.Đặt IP cho 2 card mạng.

##I.Tìm hiểu về VMware:
###1.Khái niệm:
VMware workstation là 1 phần mềm ảo hóa deskop, cho phép người dùng có thể tạo ra các máy ảo chạy HĐH như Window, Linux, Solaris và hoạt động như 1 máy thật mà không cần phải khởi động lại hay phân vùng ổ cứng.
###2.Tác dụng:
VMware giúp giả lập máy tính ảo trên một máy tính thật. Khi cài đặt VMware lên, ta có thể tạo nên các máy ảo chia sẻ CPU, RAM, Card mạng với máy tính thật. Điều này cho phép xây dựng nên một hệ thống với một vài máy tính được nối với nhau theo một mô hình nhất định
###3.Cách cài đặt 1 máy ảo trên vmware:
-Các bước cài đặt:
<ul>
<li>Tạo 1 thư mục để chứa máy ảo:</li>
<li>Trong Home -> Create a new virtual machine</li>
<img src="http://imgur.com/bBUB0Vu">
<li>Chọn hệ điều hành cần cài đặt, ở đây ta chọn ubuntu 64 bit</li>
<img src="http://prntscr.com/arzbyr">
<img src="http://prntscr.com/arzcaw">
<li>Đặt tên cho máy và lưa vào thư mục đã chọn</li>
<img src="http://prntscr.com/arzcsx">
<li>Tiến hành cài đặt phần cứng cho máy và finish</li>
<img src="http://prntscr.com/arzd5f">
</ul>

###4.Một số thao tác với card mạng ảo:
Trong Home -> edit -> Virtual network editor

<img src="http://prntscr.com/arzdxl">

Tại đây sẽ hiện ra 1 bảng bảo gồm các card mạng ảo của máy như VMnet 8, VMnet 1, VMnet 0…, ta có thể thêm hoặc xóa các card mạng ảo, gán  IP cho các card mạng.

##II.Thiết lập IP tĩnh và động bằng cách sửa file, câu lệnh:

###1.Thiết lập IP tĩnh bằng cách sửa file:
Tại root ta gõ câu lệnh `vi /etc/networking/interfaces` để vào file cấu hình sửa IP, gateway, netmask, dns-server...
<img src="http://prntscr.com/arzgaf">

###2.Gán IP bằng câu lệnh:
Sử dụng lệnh `#ifconfig eth0 địa chỉ ip netmask`
<img src="http://prntscr.com/arzh70">
Gán gateway bằng câu lệnh:
`#route add default gw địa chỉ gateway`
<img src="http://prntscr.com/arzhrs"

###3.Thiết lập IP động:
Để thiết lập máy nhận IP động từ DHCP server, ta dùng lệnh:

`#vi/ etc/networking/interfaces`

Sau đó sửa như sau:

<img src="http://prntscr.com/arzid7">

##Add 2 card mạng cho máy và cấu hình 

###B1: Tắt máy và add thêm card
<img src="http://prntscr.com/arzire">
<img src="http://prntscr.com/arziwy">
Kiểm tra xem máy đã nhận card hay chưa:
<img src="http://prntscr.com/arzjjx">
Sau đó sửa file cấu hình bằng câu lệnh:
`#vi /etc/networking/interfaces`
<img src="http://prntscr.com/arzjv4">
Sau đó restart lại card mạng bằng lệnh:
```sh
ifdown -a 
ifup -a 
```
<img src="http://prntscr.com/arzkf3">



