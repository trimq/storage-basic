###So sánh Filesystem:

| Filesystem | EXT2 | EXT3 | EXT4 | Btrfs | XFS |
|------------|------|------|------|-------|-----|
| Journaling | Không có | Có Journaling | Có Journaling | Có Journaling | Có Journaling |
| Tốc độ ghi | tương đối nhanh | chậm hơn so với ext2 | tốc độ ghi nhanh hơn so với ext2,3 | tốc độ hoạt động nhanh | hiệu suất hoạt động không cao |
| Phục hồi dữ liệu | cần fsck để phục hồi dữ liệu | tự động file phục hồi dữ liệu | tự động file phục hồi dữ liệu | | |
| Max file size ( Block size 1KB-8KB) | 16GB-2TB  | 16GB-2TB | 16GB-16TB | 16 EB | 8 exbibytes-1 byte |
| Max filename size | 255 bytes | 255 bytes | 255 bytes | 255 ASCII character | 255 bytes |



####So sánh giữa FAT32 và NTFS

| Filesystem | NTFS | FAT32 |
|------------|-------|------|
| Max partition size | 2TB | 2TB |
| Số file trên partition | Không hạn chế | Không hạn chế |
| Max file size | Chỉ hạn chế bởi kích thước partition | 4GB |
| File name lenght | 255 characters | 255 characters |
| Chế độ bảo mật | Có | Không |
| Khả năng hồi phục | Có | Không |
| Hiệu năng hoạt động | Thấp trên các ổ đĩa nhỏ, cao trên các ổ đĩa lớn | Cao trên các ổ đĩa nhỏ và thấp trên các ổ đĩa lớn |
