# nodejs
NodeJS là:
- Một mã nguồn được xây dựng trên nền tảng js v8 Engine của Google
- NodeJS hoàn toàn miễn phí chạy trên server
- Có thể cài đặt trên nhiều nền tảng khác nhau (Win,Linux,Unix,MAc OS,...)
NodeJS có một số đặc trưng như sau :
- Tối ưu hóa thời gian thực hiện tiến trình
- Có khả năng mở rộng các ứng dụng web với nhiều hoạt động I/O liên tục
- Dễ dàng xây dựng các ứng dụng real-time
- Cách viết ứng dụng với Node đó là các ứng dụng được cấu tạo từ các module nhỏ sau đó được kết hợp lại với nhau điều này đảm bảo cho việc sửa đổi bảo trì một cách nhanh chóng
CÀI ĐẶT:(chúng ta sẽ cài đặt NodeJS trên ubuntu)
Để cài đặt Nodejs trên ubuntu rất đơn giản bạn chỉ cần mở terminal lên và chạy command:
                 sudo apt install nodejs
Tiếp theo để kiểm tra xem đã cài đặt thành công Nodejs hay chưa bạn chỉ cần chạy command                 
 node -v hoặc node –version
 
 ![image](https://user-images.githubusercontent.com/54676091/120783478-48405600-c555-11eb-8047-6824f8af8c1d.png)
Nếu hiện ra như trên thì bạn đã thành công còn nếu không thì thôi nghỉ

Npm (Node package manager) là một công cụ tạo và quản lý các thư viện lập trình Javascript cho Node.js nó được tích hợp sẵn vào trong node.js. Nên khi các bạn cài đặt node.js thì đã có npm luôn rồi.

TẠO MỘT PROJECT NODEJS:
Để tạo 1 Project nodejs chúng ta chỉ cần chạy command như sau:

```jsx npm init ```  --yes hoặc ```jsx npm init ```

![image](https://user-images.githubusercontent.com/54676091/120788082-42993f00-c55a-11eb-9a4d-884f386cacb9.png)

```npm init --yes ``` hay hơn vì khi thêm --yes n sẽ tạo luôn project mặc định cho chúng ta mà không cần hỏi một vài tham số như author...

CẦN CÀI THÊM FRAMEWORK EXPRESS CỦA NODEJS :
Bởi khi đã có npm cài đặt ở trên thì chúng ta cài đặt thêm express của Nodejs rất đơn giản bằng command:
      ```jsx npm install express --save ```
![image](https://user-images.githubusercontent.com/54676091/120788015-2e554200-c55a-11eb-93ad-a463cffdfd26.png)


Thêm ```jsx --save ``` để có thể lưu phiên bản của module vào phần dependencies trong file package.json

HELLO WORLD BẰNG NODEJS:
Sau khi chúng ta chạy lệnh npm init --yes và install thêm module express thì chúng ta được một file có tên là package.json và đây là những gì có trong file package.json
```jsx
{
  "name": "Nodejs",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
Giải thích: khi chúng ta install các module thì Nodejs còn sinh ra một folder là node_modules để chứa các thứ liên quan đến module bạn vừa cài đặt, nhìn chung là cũng không cần quan tâm đến folder này lắm . Khi Nodejs chạy nó sẽ chạy vào file được chỉ định trong key main ở file packager.json và ở đây  đang để mặc đinh là file index.js vì thế ta sẽ tạo một file mới có tên là index.js để đảm bảo viết code vào đó thì chắc chắn code được chạy. Và đây là file index.js
```jsx
const express = require('express');
const app = express();
const port = 3000;

app.get('/', function(req, res){
    res.send("Hello World");
})

app.listen(port, function(error){
    if (error) {
        console.log("Something went wrong");
    }
    console.log("server is running port:  " + port);
})
```

Giải thích :

```jsx const express = require('express'): ```
Trong Nodejs bạn muốn sử dung module nào thì bạn cần phải require module đó vào, ở đây muốn sử dụng express nên phải require nó vào thôi
```jsx const app = express():  ```    
Tạo một app sử dụng module express vừa require ở trên
```jsx const port = 3000: ```
Khai báo một cổng để chạy ứng dụng NodeJS của bạn trên server, bạn có thể để cổng khác tùy ý tránh bị trùng cổng giữa các ứng dụng là được 

```jsx app.get('/', function(req, res){
    res.send("Hello World");
}) 
```
Hàm get() sẽ có 2 tham số, tham số đầu tiên là địa chỉ mà server sẽ nhận request từ client để thực thi function là tham số thứ 2. Ở đây khi truy cập vào đường dẫn http://localhost:3000/ thì bạn sẽ nhận được kết quả
![image](https://user-images.githubusercontent.com/54676091/120791622-a160b780-c55e-11eb-9018-3a8e61fa055b.png)
```jsx
app.listen(port, function(error){
    if (error) {
        console.log("Something went wrong");
    }
    console.log("server is running port:  " + port);
})
```
 Hàm listen() sẽ khởi động server
 Hàm này có 2 tham số, tham số đầu tiên là port mà ứng dụng NodeJS của bạn sẽ chạy, tham số thứ 2 là một callback function sẽ được gọi khi server khởi động. 
 Function này lại chứa một tham số error để bắt lỗi khi mà server không thể khởi động vì một lý do nào đó. Ở đây mình console.log() để biết là server có khởi động thành công hay gặp lỗi, còn nếu các bạn không thích thì có thể viết lại như thế này
 
```jsx app.listen(port) ```
thì vẫn chạy bình thường :V

thử chạy lênh node index.js để xem có lỗi gì không nhé. nếu terminal hiện server is running port: 3000 thì đã thành công\

