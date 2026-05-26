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
Toàn bộ quá trình cài đặt đều được cấp quyền quản trị cao nhất `root` dể dễ dàng thao tác.
### 2.1 Cài đặt Zabbix Server
**Bước 1**: Tải kho lưu trữ của Zabbix  
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb  
dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb  
apt update  
**Bước 2**: cài đặt Zabbix Server, frontend, agent
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent  
**Bước 3**: cài đặt MySQL server  
apt update  
apt install MySql-server  



