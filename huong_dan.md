======================================================== Cấu trúc: ==========================================================

/vps_simulator
|
├── apps
│   ├── app1
│   │   ├── docker-compose.yml
│   │   ├── .env
│   │   ├── storage/
│   │   └── deploy/
│   │
│   | 
|   |__ app2
|       ├── docker-compose.yml
|       ├── .env
|       ├── storage/
|       |__ deploy/
|      
|
|__ data
|   |__ mysql
|   |__ redis
|
|      
├── docker (global)
│   ├── mysql
|   |   |__ docker-compose.yml
│   |
|   |── redis
|   |   |__ docker-compose.yml
|   |
│   └── nginx
|       |__ certs
|       |__ conf.d
|       |   |__ app1.conf
|       |   |__ app2.conf
|       |__ log
|       |__ html
|       |__ nginx.conf
|       |__ docker-compose.yml
│
|
├── backups
|
|── logs
|
|__ scripts




================================================= Kiến trúc tổng quan: ==========================================================

            INTERNET
                ↓
            global_nginx
                ↓
            proxy-network
                |
 ┌─────────────────────────────────┐
 │                                 │
app1_php                       app2_php
 │                                 │
 └──────────────┬──────────────────┘
                │
         global_mysql
                │
          global_redis



================================================= Step by step setup run app từ đầu =============================================

1. Tạo network: docker network create proxy-network
2. dockers/mysql → docker compose up -d
3. Import SQL
4. Tiếp tục Redis, Nginx, từng app trong apps/*/