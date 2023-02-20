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
### 3.2 Redirection
