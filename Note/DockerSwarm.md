# Docker swarm

**1. Tạo 1 node swarm manager**

```
sudo docker swarm init --advertise-addr=<IP_Manager>
```

Sau khi chay xong sẽ hiện token để kết nối các node worker
`docker swarm join --token SWMTKN-1-5xv7z2ijle1dhivalkl5cnwhoadp6h8ae0p7bs5tmanvkpbi3l-5ib6sjrd3w0wdhfsnt8ga7ybd 192.168.10.101:2377`

*Như VD hãy copy phần hiển thị khi tạo và chạy trên các máy worker*

Để kiểm tra lại mã token khi quên 

```
sudo docker swarm join-token worker
```
**2. Rời khỏi swarm**
```
sudo docker swarm leave --force
```

**Các lệnh kiểm tra**

- Kiểm tra docker swarm đã activite `sudo docker info`

- Kiểm tra các node `sudo docker node ls`

**3. Chạy dịch vụ trên docker swarm**

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

Chuyển phiên làm việc 
```
docker swarm join --token <token> <host>:<port>
```

