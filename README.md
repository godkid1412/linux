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

 - Create file: `touch file_name`
 - Copy Files and Directories:
   -  cp []
 


### 9.2: Filesystems

## 10:
