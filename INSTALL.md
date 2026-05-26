# CÀI ĐẶT HỆ THỐNG GIÁM SÁT HẠ TẦNG MẠNG ZABBIX
## 1. Cấu hình máy ảo
- **Zabbix Server**:
  - OS: `Ubuntu 24.04 LTS`
  - Bộ nhớ: `20GB`
  - RAM: `4GB`
  - CPU : `2 cores`
  - Mạng: 1 card mạng `NAT` và 1 card mạng `Host-Only`
- **Zabbix Agent 1**:
  - OS: `Windows 10`
  - Bộ nhớ: `30GB`
  - RAM: `2GB`
  - CPU: `2 cores`
  - Mạng: `Host-Only`
- **Zabbix Agent 2**:
  - OS: Ubuntu 24.04 LTS
  - Bộ nhớ: `15GB`
  - RAM: `3GB`
  - CPU: `2 cores`
  - Mạng: `Host-Only`
## 2. Cài đặt hệ thống
Toàn bộ quá trình cài đặt trên Ubuntu đều thực hiện ở terminal và cấp quyền quản trị cao nhất `root` dể dễ dàng thao tác.  
Cài đặt Agent trên Windows sử dụng package tải trên [Zabbix Download.](https://www.zabbix.com/download_agents)
### 2.1 Cài đặt Zabbix Server
**Bước 1**: Tải kho lưu trữ của Zabbix  
`wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb`  
`dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb`  
`apt update`  
**Bước 2**: cài đặt Zabbix Server, frontend, agent  
`apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent`  
**Bước 3**: cài đặt MySQL server  
`apt update`  
`apt install MySql-server`  
**Bước 4**: cấu hình database  
**Tạo database zabbix**  
`mysql -uroot -p`  
password  
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;  
mysql> create user zabbix@localhost identified by '<`password_da_tao`>';  
mysql> grant all privileges on zabbix.* to zabbix@localhost;  
mysql> set global log_bin_trust_function_creators = 1;  
mysql> quit;  
**nạp dữ liệu có sẵn của zabbix**  
`zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix`  
<`password_da_tao`>  
**vô hiệu hóa các tùy chọn tạm thời**  
`mysql -uroot -p`  
password  
mysql> set global log_bin_trust_function_creators = 0;  
mysql> quit;  
**Bước 5**: cấu hình database kết nối zabbix server  
chỉnh sửa file zabbix_server để kết nối với database zabbix vừa tạo: 
`nano /etc/zabbix/zabbix_server.conf`, cấu hình chi tiết ở trong file [zabbix_server.conf](configs/zabbix_server.conf)  
**Bước 6**: khởi động lại dịch vụ và cấu hình trên web  
`systemctl restart zabbix-server zabbix-agent apache2`  
`systemctl enable zabbix-server zabbix-agent apache2`  
Truy cập `192.168.27.100/zabbix` và cấu hình kết nối với database, sau khi kết nối thành công sử dụng tài khoản `Admin` với password là `zabbix` để đăng nhập zabbix web   
### 2.2 Cài đặt Zabbix Agent trên host Ubuntu  
**Bước 1**: tương tự như cài đặt Zabbix Server
**Bước 2**: cài đặt Zabbix Agent  
`apt install zabbix-agent`  










