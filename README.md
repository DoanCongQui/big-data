# Môn nhập môn dữ liệu lớn (Big Data)

Các kiến thức cần có:
- Docker
- Cloud
- Git

# Docker Swarm 
- Đặt địa chỉ ip tỉnh cho các máy ảo 

Run terminal `sudo vim /etc/netplan/<name>.yaml`

```
network:
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [192.168.1.<IP>/24] 
      routes:
        - to: 0.0.0.0/0
          via: 192.168.1.1
      nameservers:
            addresses: [1.1.1.1, 1.0.0.1, 8.8.8.8, 8.8.4.4]

  version: 2
```
Sau đó run `sudo netplan apply`


