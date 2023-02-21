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


### 5.3: htop
