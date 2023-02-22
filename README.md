# Linux

## 1.Understand shell environment variables
Cách gán environment variables:
```
TEST_VAR='Hello World!'
```
 Cách tạo biến đó **CHỈ** hoạt động ở phiên tạo biến

Xem environment variables hiện có:
```
env 
printenv
```

Xem thông tin biến:
```
env NAME_VARIABLES
printenv NAME_VARIABLES
```

Nguồn: [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)
## 2.Getting Help
 Dùng `man [command]`, `[command] -h`, `whatis [command]`, `info [command]`
 
 ```
 man ping
 ping -h
 whatis ping
 info ping
 ```
tuy nhiên `whatis` cho ra thông tin hạn chế hơn so với những cái khác

Nguồn: [Vtux](https://vitux.com/get-help-on-linux-shell/#:~:text=How%20to%20use%20%E2%80%93h%20or,that%20command%20as%20shown%20below.)

## 3. Using Streams, Redirection, Pipes
### 3.1 Streams
  - Standard input stream `stdin`: cho phép text được làm đầu vào, đọc từ file text
  - Standard output stream `stdout`: text đc hiển thị từ các shell, ghi vào file text
  - Standard error `stderr`: error message được hiển thị từ các shell, ghi vào file text

Nguồn: [HowToGeek](https://www.howtogeek.com/435903/what-are-stdin-stdout-and-stderr-on-linux/)
Nguồn: []()
### 3.2 Redirection
 <img width="1200" alt="image" src="https://user-images.githubusercontent.com/54473576/220038871-038ab1b7-97f4-410f-94b1-b18d127ed807.png">
Nguồn: LPIC-1 page 54
### 3.3 Piping Data between Programing
 - Sử dụng vertical bar, vertical slash, or vertical line `|`
 - Có thể redirect STDOUT, STDIN, and STDERR giữa nhiều câu lệnh
```
COMMAND1 | COMMAND2 [|COMMAND3]...
```
<img width="570" alt="image" src="https://user-images.githubusercontent.com/54473576/220043409-67583a74-0347-40cc-ba40-fb9e484535dd.png">
Thực thi câu lệnh 1, output câu lệnh 1 đc tính như input câu lệnh 2 và thực thi 2,...

## 4.Processing Text
### 4.1 cat, join, paste + option
 - Cat
  - Hiển thị text
  - Sao chép file text vào 1 file mới
  - Nối 1 đoạn nội dung của text file vào text file khác và kết hợp với nhau
  - Option: 
    <img width="1133" alt="image" src="https://user-images.githubusercontent.com/54473576/220072276-8caf9568-0f73-42e2-9e92-9f29ff30f7f0.png">
 - join
  -
 - paste
### 4.2 tac, sort, split, uniq, nl
 - tac
 - sort
 - split
 - uniq
 - nl
### 4.3 File-Viewing Commands: head, tail, less, cut, wc
 - head
 - tail
 - less
 - cut
 - wc
### 4.4 grep, sed, awk
 - grep
 - sek
 - awk
## 5. Manage Processes
### 5.1: ps
<img width="741" alt="image" src="https://user-images.githubusercontent.com/54473576/220228385-8df641e6-e800-4bc2-b16f-ee2f701b4701.png">


 ps:
 
  - chọn tất cả processes giống User ID(UID) với người dùng hiện tại

  - PID: được gắn cho mỗi process

  - PPID: PID của process khác nếu nó đc khởi chạy từ 1 process khác
 
  - C:
  
  - STIME: System time khi process bắt đầu
  
  - TTY: terminal mà process bắt đầu
 
  - TIME: thời gian CPU dành cho process
 
  - CMD: Tên của ctrinh bắt đầu process
 
|Option|Description|
|---|---|
|`a`|Hiển thị toàn bộ process trên hệ thống kết hợp với tty terminal|
|`-A` `-e`|Hiển thị toàn bộ process trên hệ thống|
|`-C CommandList`|Hiển thị processes chạy command trong CommandList|
|`-g GIDList` `-group GIDList`|Chỉ hiển thị processes có effective group trong GroupList|
|`-G GIDList` `-Group GIDList`|Chỉ hiển thị processes có real group trong GIDList|
|`-N`|Hiển thị toàn bộ processes trừ các processes đc chọn|
|`p PIDList` `-p PIDList` `--pid PIDList`|Chỉ hiển thị processes có PIDList|
|`-r`|Chỉ hiển thị các processes có state: running|
|`-t ttyList` or `--tty ttyList`|Hiển thị các processes liên quan đến ttyList terminal|
|`-T`|Hiển thị các processes liên quan đến tty terminal hiện tại|
|`-u UserList` or `--user UserList`|Hiển thị các processes có effective user trong UserList|
|`-U UserList` or `--User UserList`|Hiển thị các processes có real user trong UserList|

`Real indicates that this is the user or group the account is associated with when logging into the system and/or the primary account’s group. Effective indicates that the user or group is using a temporary alternative user or group identification, as in the case of SUID and GUID permissions`

### 5.2: top

<img width="537" alt="image" src="https://user-images.githubusercontent.com/54473576/220238220-6ad92117-4325-4d3f-bc5b-5cbe70f88b0a.png">

 - Dòng 1: hiển thị thông tin chung của hệ thống, thời gian hiện tại, thời gian up, số user logged in, load averager của hệ thống.
   - Load average: mức độ tải trung bình của CPU trong 1m, 5m, 15m
 - Dòng 2: Hiển thị thông tin chung về process (tasks in top)
 - Dòng 3: Thông tin về CPU
 - Dòng 4 + 5: Thông tin về tình trạng RAM
 
|Command Output|Description|
|---|---|
|PID|The process ID of the process|
|USER|username thực thi task|
|PR|Độ ưu tiên của tiến trình. Số càng thấp thì mức độ ưu tiên càng cao|
|NI|Giá trị nice value của tiến trình, ảnh hưởng đến độ ưu tiên của tiến trình đó|
|VIRT|Bộ nhớ ảo đang được sử dụng cho tiến trình|
|RES|Bộ nhớ RAM đang được sử dụng cho tiến trình|
|SHR|Bộ nhớ được chia sẻ với process khác|
|S|Process status (D: `interruptible sleep (chờ 1 sự kiện hoàn tất)`, I: `idle`, R: `running`, S: `sleeping`, T:`traced` or `stopped`, and Z: `zombie`)|
|%CPU|% sử dụng CPU|
|%MEM|% sử dụng MEM|
|TIME+|Tổng CPU time đã chạy|
|COMMAND|Tên lệnh của process|

Sắp xếp danh sách `top`
 - `M` để sắp xếp theo mức sử dụng bộ nhớ
 - `P` để sắp xếp theo mức độ sử dụng CPU
 - `N` để sắp xếp theo ID tiến trình
 - `T` để sắp xếp theo thời gian chạy

### 5.3: htop

<img width="1251" alt="image" src="https://user-images.githubusercontent.com/54473576/220246476-c2c3d4f3-7145-4bf4-9772-6712614e96ab.png">

 - Mức dùng CPU:
   - Xanh lam: Các tiến trình độ ưu tiên thấp
   - Xanh lục: Các tiến trình người dùng
   - Đỏ: Các tiến trình hạt nhân( kernel)
 - Mức dùng RAM:
   - Xanh lục: bộ nhớ đã dùng
   - Xanh dương: bộ nhớ đệm
   - Vàng: bộ nhớ cache
 - Kill process: dùng điều hướng lên xuống di chuyển đến đúng process rồi nhấn F9 và nhấn Enter để xác nhận xoá hoặc Esc để huỷ
 - Nhấn F7 F8 để chỉnh quuyền ưu tiên của process
 - Tree view: Có những process chạy độc lập nhưng có những process có các threads chạy bên trong. Để xem được dưới dạng tree bạn chỉ cần ấn phím F5.
 - Searching: Ấn F3 rồi gõ tên process. Nếu khớp thì dòng process đc highlight lên, nhấn F3 để tìm tiếp
 - Filter: Nhấn F4 rồi gõ tên process. Sau đó htop hiển thị các process có cùng tên filter
 - Sort: Nhấn chuột vào tiêu đề cột để sắp xếp
 - Quit: Nhấn F10
## 6: Foreground and Background Processes

|Foreground Processes| Background Processes|
|---|---|
|1 process khi bắt đầu từ terminal chạy mặc định là foreground process||
|Không cho phép huỷ bỏ trừ khi process hoàn thành|Background process chạy process in background và ko chịu ảnh hưởng từ terminal prompt|
|Muốn quay lại terminal cần tạo 1 terminal mới hoặc stop or kill process|Có thể bắt đầu 1 session và có thể sử dụng terminal đó|
||Gửi 1 command chạy background cần thêm `&` ở cuối câu |

## 7: Killing Processes

Signal list:
<img width="516" alt="image" src="https://user-images.githubusercontent.com/54473576/220282044-917127e9-0e6f-4bda-b4d4-7eac855b81ba.png">

User thường dùng signal 9 hoặc 15
Command to kill process
```
kill -[signal] PID
kill -15 PID
kill -9 PID
kill -SIGTERM PID
kill [options] -SIGTERM PID
```
Rule to kill process
 - Kill process của chính mình
 - Mỗi `root` có thể kill process mức độ system
 - Mỗi `root` có thể kill process được bắt đầu bưởi user khác

Example:
```
kill  pid1 pid2 pid3
kill -15  pid1 pid2 pid3
kill -9  pid1 pid2 pid3
kill  -9 3546 5557 4242
```
## 8: Manage software
### 8.1: Package, dependencies, conflicts, binary packet
 - Packet: bundle được biên dịch từ các ứng dụng. Chứa các file bắt buộc để chạy 1 ứng dụng
 - Library dependencies: Cơ sở dữ liệu các package (thư viện file yêu cầu để chạy mỗi ứng dụng và có thể cảnh báo nếu dependent library file không có khi tải package về)
 - Conflic:
 - Binary package: Là 1 file lưu trữ chứa tất cả file và đường dẫn có thể cài đặt theo trình tự của ctrinh bao gồm cả package, maintainer script cần thiết để cài đặt
 
### 8.2: Các trình nén trong Linux: `tar` `zip` `unrar` `gunzip`


## 9: Managing File and Filesystems

#### 9.1: Managing File
 
 - Hiển thị file: ls [option] [file]
   <img width="619" alt="image" src="https://user-images.githubusercontent.com/54473576/220310478-83fe0131-4eaa-4dfc-aa70-1001871edbc0.png">


 - Create file: `touch file_name`
 - Copy Files and Directories:
   - `cp [option] SOURCE DEST`
   <img width="639" alt="image" src="https://user-images.githubusercontent.com/54473576/220309778-8c0845de-1f8b-4bcf-9808-155dcd079504.png">

   - pwd: vị trí hiện tại
 - Move File: `mv [option] SOURCE DEST`
   <img width="606" alt="image" src="https://user-images.githubusercontent.com/54473576/220312436-4176c314-53f7-48c3-b067-3b41af6ef1c2.png">

 -Delete File: `rm [OPTION]... FILE`
   <img width="614" alt="image" src="https://user-images.githubusercontent.com/54473576/220312765-3c5ff84f-3dbc-42ec-a483-fc37704a01eb.png">

### 9.2: Managing Filesystems

 - Retrieving Filesystem Stats
   - df: hiển thị ổ cứng sử dụng theo phân vùng
   - du: hiển thị sử dụng theo thư mục ( tốt cho tìm kiếm user, application chiếm nhiều không gian)
   - iostat: Hiển thị biểu đồ theo thời gian thực

## 10: Understand Files System Type
 - ext:
 - ext2:
 - ext3:
 - ext4:
## 11: Check file system `fsck`

 fsck: file system comsistency check: fsck chạy lúc khởi động nếu phát hiện 1 vài đkien:
   - 1 file system đc dánh dấu `dirty` 
   - 1 file system đc gắn số mà ko đc kiểm tra
  Lệnh `fsck` tự tương tác với lệnh `fsck` dành riêng cho hệ thống tập tin phù hợp được tạo bởi các tác giả của hệ thống tập tin. Bất kể loại hệ thống tập tin, `fsck` thường có ba chế độ hoạt động:
   - Kiểm tra và nhắc nhở user tương tác để quyết định hướng sửa lỗi
   - Kiểm tra lỗi và tự động sửa lỗi
   - Kiểm tra lỗi và không cố gắng sửa lỗi nhưng hiển thị lỗi qua `stdout` standard output
 Mặc dù thường chạy vào thời điểm khởi động, `fsck` có thể chạy thủ công trên các hệ thống tập tin không được xem xét bởi một superuser. 
 
 `filesys` là device name (/dev/hdc1, /dev/sdb2,...), 1 mount point (/usr, /home), 1 ext2 label, UUID specifier
 Mã thoát được `fsck` trả về là một số duy nhất biểu thị tổng của các giá trị điều kiện sau:
 |Number|Description|
 |---|---|
 |0|Không lỗi|
 |1|Filesystem đã được sửa lỗi|
 |2|System cần đc reboot|
 |4|Filesystem lỗi chưa đc sửa|
 |8|Lỗi hoạt động|
 |16|Lỗi sử dụng hoặc cú pháp sai|
 |32|`fsck` đc huỷ bởi user yêu cầu|
 |128|Share-library lỗi|
## 12: Monitoring Disk `df` `du`

- df: hiển thị ổ cứng sử dụng theo phân vùng
- du: hiển thị sử dụng theo thư mục ( tốt cho tìm kiếm user, application chiếm nhiều không gian)

## 13: Creating Filesystem: `mkfs`
 
 `mkfs` (makes file systems). HĐH khác, tạo file system là formating. Nó là quá trình cbi phân vùng để chứa dữ liệu
 Phân vùng cần cơ chế để lưu trữ tên, vị trí của file, nhiều thông tin khác: thời gian tạo, thời gina sửa, kích thước của file,...
 Syntax: `mkfs.file_sys_type device_filename`
   ```
   mkfs.ext2 /dev/fb0
   mkfs.ext2 ~/howtogeek.img
   ```
 ## 14: Mounting and Unmounting Filesystems
 
  Để có thể truy cập/ sử dụng các thiết bị USB, CD/DVD, file ISO, tài nguyên qua mạng,... thì các thiết bị này cần đc `mount` (gắn) vào thư mục trống `mount point`. Khi muốn gỡ các thiết bị đang hoạt động khỏi hệ thống thì cần ngắt kết nối `unmount` giữa các thiết bị vs mount point trước đó
  
  ```
  moubt -t <type> -o <option> <device file> <mount point>
  ```
  
  Để unmount dùng lênh `**umount**`
  ```
  umount device_file
  ```
  hoặc
  ```
  umount mounit_file
  ```
 Mount ổ cứng bằng UUID
  Kiểm tra UUID của ổ cứng sử dụng:
  ```
   lsblk -o NAME,UUID,SIZE
  ```
  Kết quả: 
  <img width="554" alt="image" src="https://user-images.githubusercontent.com/54473576/220550094-8a557363-167e-4865-a6a6-d267272ebd6d.png">
  
  Cách 1: Mở file /etc/fstab và thêm dòng vào cuối file:
    ```
    UUID=fb315fe6-xxxx-xxxx-8d30-80f44a874420 /home/tmp/ ext4 defaults 0 0
    ```
  Cách 2: Thực thi câu lệnh:
   ```
   echo "UUID=fb315fe6-xxxx-xxxx-8d30-80f44a874420      /home/tmp/   ext4    defaults     0   0" >> "/etc/fstab"
   ```
 ## 15: Partitioning Disk
  - Là 1 container với file system (NTFS: Windows, HFS+: MacOS, ext4: Linux,...)
  - `fdisk -l`: hiển thị danh sách các phân vùng
    <img width="543" alt="image" src="https://user-images.githubusercontent.com/54473576/220558590-101c8e57-bafe-4285-b9d0-d65fd4751019.png">

  - `fdisk /dev/sda`
  <img width="474" alt="image" src="https://user-images.githubusercontent.com/54473576/220560357-bfafe819-1c2f-4601-90a2-43550027fe46.png">

  - Xem bảng phân vùng dùng `p`
  - Xoá phân vùng dùng`d`
  - Tạo phân vùng dùng `n`
  - Dùng `w` để lưu những thay đổi và thoát
  - Dùng `q` để thoát mà ko lưu thay đổi
  - Sau khi tạo phân vùng, dùng `mkfs` để định dạng lại phân vùng và sử dụng chúng
  
## 16: Understanding RAID, `mdadm` command

 ### 16.1: Understanding RAID
  
  - Redundant Array of Inexpensive Disks (RAID) thay đổi môi trường lưu trữ hầu hết ở DC
  - Công nghệ RAID cho phép bạn cải thiện hiệu suất và độ tin cậy truy cập dữ liệu, cũng như triển khai dự phòng dữ liệu để dung sai lỗi bằng cách kết hợp nhiều ổ đĩa thành một ổ đĩa ảo. Một số phiên bản RAID thường được sử dụng:
    - RAID 0: Ghi dữ liệu theo phương thức đặc biệt: `Striping`. Chia dữ liệu thành nhiều phần rồi ghi các phần vào ổ cứng chạy RAID
    - RAID 1: Ghi dữ liệu theo phương thức `mirroring`. 
    - RAID 10: Cần tối thiểu 4 ổ cứng để làm việc. Dữ liệu được ghi đồng thời lên 4 ổ với 2 ổ dạng striping và 2 ổ dạng mirroring. Tổng dung lượng bằng 1/2 dung lượng 4 ổ cứng
    - RAID 4: 
    - RAID 5: 
    - RAID 6: 

### 16.2: `mdadm` command

## 17: Understanding LVM, create/resize/delete lvm, pv, pg
 Logical Volume Management (LVM) dùng quản lý các thiết bị lưu trữ.
 LVM là 1 tiện ích cho phép thay đổi không gian đĩa cứng thành những Logical Volume từ đó giúp việc thay đổi kích thước dễ hơn
 
 ### create/resize/delete lvm, pv, pg

## 17: Filesystem Hierarchy Standard
<img width="641" alt="image" src="https://user-images.githubusercontent.com/54473576/220582309-c611d5ae-22bc-43a2-a183-ce8f636d1389.png">

## 18: Managing Files and Link: `ls`, `cp`, `mv`, `rm`, `touch`, `ln`

 - Hiển thị file: ls [option] [file]
   <img width="619" alt="image" src="https://user-images.githubusercontent.com/54473576/220310478-83fe0131-4eaa-4dfc-aa70-1001871edbc0.png">


 - Create file: `touch file_name`
 - Copy Files and Directories:
   - `cp [option] SOURCE DEST`
   <img width="639" alt="image" src="https://user-images.githubusercontent.com/54473576/220309778-8c0845de-1f8b-4bcf-9808-155dcd079504.png">

   - pwd: vị trí hiện tại
 - Move File: `mv [option] SOURCE DEST`
   <img width="606" alt="image" src="https://user-images.githubusercontent.com/54473576/220312436-4176c314-53f7-48c3-b067-3b41af6ef1c2.png">

 -Delete File: `rm [OPTION]... FILE`
   <img width="614" alt="image" src="https://user-images.githubusercontent.com/54473576/220312765-3c5ff84f-3dbc-42ec-a483-fc37704a01eb.png">

## 19: Managing File Ownership: `chown`, `chgrp`

 ### 19.1: Changing a File's Owner
   Chỉ mỗi `root user` hoặc `super user privileges` có thể thay đổi quyền sở hữu 1 file hoặc 1 directory bằng cách sử dụng  `chown`
   ```
   chown [ OPTIONS ] NEWOWNER FILENAMES1 [FILENAME2 ...]
   ```
   <img width="472" alt="image" src="https://user-images.githubusercontent.com/54473576/220588512-dbac7f4a-445f-4ff4-b44e-f2c117919fa8.png">

   
 ### 19.2: Changing a File's Group
   Chỉ mỗi `root user` hoặc `super user privileges` có thể thay đổi nhóm chỉ định của 1 file hoặc 1 directory bằng cách sử dụng  `chgrp`
   ```
   chgrp [OPTIONS] NEWGROUP FILENAMES
   ```
   <img width="494" alt="image" src="https://user-images.githubusercontent.com/54473576/220588559-c11b41a6-6cef-43be-bb31-13bfdfc68d92.png">

## 20: Controlling Access fo Files: Permissions, `chmod`

 ### 20.1: Understanding Permissions
   <img width="364" alt="image" src="https://user-images.githubusercontent.com/54473576/220590856-8b3b07ea-2216-4694-ac87-9d0f48240c5c.png">

   - File type code `-`
   - Permission string`rw-r--r--`
   - Hard link count `1`
   - File owner `root`
   - File group `root`
   - File size `41`
   - Last modification date `Feb 20 17:18`
   - Filename `myfile1.txt`
 
 <img width="603" alt="image" src="https://user-images.githubusercontent.com/54473576/220594778-68901017-9996-4414-8115-ceab57e9270f.png">

<img width="496" alt="image" src="https://user-images.githubusercontent.com/54473576/220594828-92fe1ad3-b76c-4af0-9e30-29421f7997f8.png">

 
 ### 20.2: `chmod`
 #### 20.2.1: Using `chmod` with Symbolic Mode
   <img width="355" alt="image" src="https://user-images.githubusercontent.com/54473576/220597088-1b3deda3-f687-4c5c-b1c5-be212dc45f5d.png">

  
   
## 21: Tools for Locating Files


