#Các khái niệm cơ bản trong Storage
##Block storage:
Block storage hay còn trong Linux còn gọi là Block device. Block device là 1 phần của phần cứng dùng để lưu trữ dữ liệu, giống như 1 ổ đĩa cứng truyền thống (HDD), (SSD).
Được gọi là block bởi vì kernel tương tác với phần cứng bằng cách tham khảo các block cố định hoặc các khối của không gian
Về cơ bản, block storage được xem như là lưu trữ trên ổ đĩa của 1 máy tính. Một khi đã được set up, về cơ bản nó sẽ hoạt động như 1 phần mở rộng của filesystem tree và có thể viết và đọc thông tin từ ổ 1 cách liền mạch.
##Disk Partition:
Disk partition là 1 cách để phân vùng ổ đĩa thành các đơn vị nhỏ hơn có giá trị sử dụng.
 Một partition là 1 phần của thiết bị lưu trữ có thể được điều chỉnh cho giống như ổ đĩa đó
Partition cho phép người dùng có thể chia các không gian có sẵn và sử dụng chúng vào các mục đích khách nhau cho mỗi partition
Điều này cho phép người sử dụng có rất nhiều tính linh hoạt cho người sử dụng, cho phép linh hoạt, họ có thể dễ dàng phân khúc cài đặt và dể dang upgrading
####MBR vs GPT:
Khi phân vùng 1 ổ đĩa, cần phải làm biết loại ổ đĩa mà ta muốn sử dụng, có 2 loại đó là MBR(Master Boot Record)
và GPT(GUID Partition Table).
<ul>
<li><b>MBR</b>: Là 1 hệ thống phân vùng truyền thống, tuy nhiên có nhiều hạn chế. Nó không thể sử dụng cho đĩa có dung lượng lớn hơn 2TB, nó chỉ có duy nhất 4 phân vùng chính bởi vậy phân vùng thứ 4 thường được sử dụng để làm extend partition, trong đó logical partition có thể được tạo ra.</li>
<li><b>GPT</b>:Là 1 kĩ thuật phân vùng mới, nó đã khắc phục hiệu quả những hạn chế của MBR. Hệ thống sử dụng GPT có thể có nhiều hơn những phân vùng trên 1 ổ đĩa. Hơn nữa, GPT không giới hạn kích thước đĩa và bảng partition table có sẵn tại multiple location nhằm chống lại sự cố hỏng hóc. Trong nhiều trường hợp, GPT là lựa chọn tốt hơn so với MBR</li>
</ul>
##Formatting và filesystem:
##Quản lý thiết bị lưu trữ tring Linux:
<b>Device file in /dev:</b>
Trong Linux, tất cả mọi thứ đều thể hiện là file. Bao gồm phần cứng như các thiết bị lưu trữ, được thể hiện trong hệ thống như là các file trong thư mục `/dev`. Thông thường các file đại diện cho thiêt bị lưu trữ thường có dạng `sd`, `hd`. Ví dụ ổ đĩa  trên server có dạng
```sh
/dev/sda
```
ổ đĩa đầu tiên được tạo ra có dạng `sda`
Các partition trên ổ đĩa này cũng có các file trong thư mục `/dev`. Có dạng:
```sh
/dev/sda1
```
1 là số thứ tự của phân cùng trong ổ đĩa
Một số thư mục con tồn tại dưới thư mục /dev/disk
<ul>
<li><b>by-label</b>:Hầu hết các filesystem có 1 cơ chế ghi nhãn cho phép sự phân công của tên người dùng chỉ định cho một ổ đĩa hoặc phân vùng. Thư mục này bao gồm các liên kết được đặt tên theo các nhãn người dùng cung cấp</li>
<li><b>by-uuid</b>:Là 1 chuỗi các chữ số và con số được sử dụng như 1 ID cho 1 tài nguyên lưu trữ</li>
<li><b>by-id</b>:Thư mục này chứa các liên kết được tạo ra bởi con số serial riêng của phần cứng và các phần cứng được gắn vào</li>
<li><b>by-path</b>:Tương tự như thư mục by-id, thư mục này dựa trên việc kết nối các thiết bị lưu trữ cho hệ thống. Các liên kết ở đây được xây dựng bằng cách giải thích của hệ thống phần cứng sử dụng để truy cập vào thiết bị</li>
</ul>
##Mounting Block Devices:
Mounting là 1 quá trình gắn một phân vùng định dạng hoặc drive tới 1 thư mục trong file hệ thống Linux, nội dung của ổ đĩa sau đó có thể được truy cập từ thư mục đó.
Driver Luôn được mount trên các thư mục trống. Có các chế độ khác nhau để thiết lập mounted device như đọc, viết..
Các filesystem tiêu chuẩn khuyến cáo sử dụng thư mục `/mnt` hoặc thư mục dưới nó để mount tạm thời . Trong nhiều trường hợp, `/mnt` hoặc `/mnt` thư mục con được sử dụng để lưu trữ lâu dài hơn là tốt.
##Mount với thư mục /etc/fstab:
Nhằm giúp cho việc mount tự động trong quá trình boot hoặc giảm nhẹ việc sử dụng lệnh mount, ta đưa thông tin cấu hình vào file `/etc/fstab`
fstab là một file cấu hình chứa các thông tin về các phân vùng trên ổ cứng cũng như các thiết bị lưu trữ khác trong máy tính. File này nằm trên thư mục /etc.
/etc/fstab chứa các thông tin cần thiết để xác định xem một phân vùng hay thiết bị được mount như thế nào và mount vào đâu trong cấu trúc thư mục


