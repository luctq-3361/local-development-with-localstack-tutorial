# Hướng dẫn run Project with LocalStack.
## Prerequisites
Cài đặt pip
  ```sh
 sudo apt update
sudo apt install python3-pip
  ```
##  Bước 1: Cài đặt local stack
Cài đặt localstack giúp tạo mội trường AWS trên local

### Installation
1. Cài đặt localstack with pip
   ```sh
    Cài đặt theo link: https://github.com/localstack/localstack-cli/releases/download/v2.2.0/localstack-cli-2.2.0-linux-amd64-onefile.tar.gz
   sudo tar xvzf ~/Downloads/localstack-cli-2.2.0-linux-*-onefile.tar.gz -C /usr/local/bin
   ```

2. Kiểm tra cài đặt
   ```sh
   localstack --version
   ```
3. Config key của localstack
Đăng ký tài khoản localstack trên website: https://app.localstack.cloud/sign-in và lấy api key
   ```sh
   export  LOCALSTACK_API_KEY=<YOUR_API_KEY>
   ```

Tham khảo: https://docs.localstack.cloud/getting-started/installation/
##  Bước 2: Cài đặt samlocal 
Cài đặt samlocal giúp tương tác với môi trường AWS localstack tương tự như sam với môi trướng AWS thật

### Installation
1. Cài đặt samlocal with pip
   ```sh
    pip install aws-sam-cli-local
   ```

2. Kiểm tra cài đặt
   ```sh
   samlocal --help
   ```
Tham khảo: https://docs.localstack.cloud/user-guide/integrations/aws-sam/
##  Bước 3: Chạy project ở local
Sau khi cài đặt 2 bước trên sẽ tiến hành chạy project ở local

###  Run
1. Start môi trường localstack
   ```sh
    localstack start
   ```

2. Chuyển đến  folder project
   ```sh
   cd ../delivery-reservation-mvp/apps/backend/template
   ```
 3. Thao tác samlocal với môi trường localstack 
 - Build code với sam
    ```sh
   samlocal build
   ```
 - Deploy code 
   ```sh
   samlocal deploy
   ```
 4. Call api 
   ```sh
   https://${ServerlessRestApi}.execute-api.execute-api.localhost.localstack.cloud:4566/Prod/${api}
   ```
  **Note**: ServerlessRestApi lấy được sau khi chạy lệnh `samlocal deploy`
- Ví dụ:
![image](https://github.com/luctq-3361/local-development-with-localstack-tutorial/assets/144312162/4ab2623a-98bd-489a-a580-568f0314b961)

