# Networking Ubuntu Server 24.10

## 1. Set up static ip sử dụng netplan
Run terminal `sudo vim /etc/netplan/<name>.yaml`

Sau đó thay thế đoạn mã sau vào file `.yaml`

```
network:z
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
Cuối cùng run `sudo netplan apply` để reset lại ip

## 2. Set up static ip 

Download `sudo apt install ifupdown`

Sau khi download nhập lệnh: `sudo vim /etc/network/interfaces`

```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp0s3
iface enp0s3 inet dhcp

auto enp0s8
iface enp0s8 inet static
address <IP>
```
