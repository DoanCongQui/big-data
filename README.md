# Môn nhập môn dữ liệu lớn (Big Data)

Các kiến thức cần có:
- Docker
- Cloud
- Git

## Docker Swarm 
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

- Tạo 3 node với VPS1 là node chính
Ssh vào VPS1 chạy lệnh `sudo docker swarm init --advertise-addr=<IP_VPS>`

Sau khi chay xong sẽ hiện dòng chữ hãy copy và chạy
```
sudo docker swarm join --token SWMTKN-1-5xv7z2ijle1dhivalkl5cnwhoadp6h8ae0p7bs5tmanvkpbi3l-5ib6sjrd3w0wdhfsnt8ga7ybd <IP_VPS>
```
Kiểm tra docker swarm đã activite `sudo docker info`

Kiểm tra các node `sudo docker node ls`

- Chạy dịch vụ trên docker swarm

Chạy ứng dụng node từ nguồn có sẳn 
```
sudo docker service create --replicas 5 -p 8085:8085 --name <name> ichte/swarmtest:node
```

Kiểm tra các các dịch vụ chạy trên các máy 
```
sudo docker service ps <name>
```

Xem các dịch vụ chạy thời gian thực trên các node 
```
sudo docker stats
```

