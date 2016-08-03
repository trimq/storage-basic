##3 thông số cơ bản để đánh giá hiệu năng ổ cứng : throughput, latency và IOPS:

#####1. Throughput:
Chỉ ra tốc độ transfer data ( MB/s hoặc GB/s). Là thông số khi check performance của ổ cứng bằng câu lệnh "dd"
trong linux.

#####2. Latency(ms):
Thời gian ổ cứng bắt đầu thưc hiện 1 data transfer. Trong HDD vật lý truyền thống, latency bao gồm seek time
(thời gian đầu đọc tìm ra vị trí data ) và rotational latency (độ trễ chuyển động quay của trục). Thông số latency quyết
định hiệu năng của volume vì nó quyết định thời gian trễ khi bắt đầu thực hiện thao tác.

- <b>Seek time</b>: Với ổ đĩa quay, seek time là khoảng thời gian để head di chuyển giữa các track. Hay nói cách khác là khoảng thời gian mà head cần có để di chuyển đến các track của đĩa quay nơi chứa dữ liệu sẽ được đọc hoặc ghi.
- <b>Rotatinal latency</b>: Rotatinal latency hay còn gọi là latency là khoảng thời gian head được chuyển tới sector hay nói cách khác đó là khoảng thừoi gian 1 I/O được xử lí, latency sẽ tăng lên khi lượng I/O tăng lên. Rotatinal latency phụ thuộc vào tốc độ quay của ổ đĩa, tốc độ quay càng cao thì latency sẽ càng giảm
- <b>Typycal HDD figures:</b>

| HDD Spindle (rpm) | Average rotational latency (ms) |
|-------------------|---------------------------------|
| 4200 | 7,14 |
| 5400 | 5.56 |
| 7200 | 4,17 |
| 10000 | 3,00 |
| 15000 | 2,00 |





#####3. IOPS:
- Input/Output Operations Per Second - số thao tác đọc ghi trên ổ cứng trong 1s. Trong điện toán đám mây, nơi mà tài 
nguyên phần cứng được chia sẻ với nhiều người, IOPS quyết định độ nhanh và nhạy của volume do bản chất IOPS càng cao thì 
càng nhiều thao tác có thể thực hiện được đồng thời 1 lúc, tốc độ xử lý càng nhanh => tốc độ hoạt động ứng dụng càng cao
- Đối với ổ **HDD**, IOPS được tính bởi công thức:
```sh
IOPS = 1/(seek + latency)
```

