# CÀI ĐẶT HỆ THỐNG GIÁM SÁT HẠ TẦNG MẠNG ZABBIX
Toàn bộ quá trình cài đặt hệ thống đều được ghi lại tại đây
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
  - Mạng: `Host-Only`
## 2. Cấu hình hệ thống
### 2.1 cấu hình Zabbix Server

