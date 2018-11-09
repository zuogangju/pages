
## centos7 安装自动补全

```bash
yum -y install bash-completion
```

## 设置docker加速

```bash
curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://abcd1234.m.daocloud.io
```

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://f8fknomo.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## 设置容器自动启动

```bash
docker update --restart unless-stopped mysql
```

## 安装部署 mysql
```bash
docker run --name mysql -p 3306:3306 -v /my/mysql/datadir:/var/lib/mysql -v /my/mysql/conf.d:/etc/mysql/conf.d -v /my/mysql/logs:/etc/mysql/logs -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

## 安装部署 RabbitMQ
==注意获取镜像的时候要获取management版本的，不要获取last版本的，management版本的才带有管理界面 #3f51b5==
```bash
docker run -d -p 5672:5672 -p 15672:15672 --name rabbitmq rabbitmq:management
```

## 安装部署 Redis
```bash
docker run -p 6379:6379 -v /my/redis/data:/data  -d redis:3.2 redis-server --appendonly yes
```

## 安装部署 mongodb
```bash

docker run --name mongodb -v /my/mongodb/data:/data/db -p 27017:27017 -d mongo

docker exec -it mongodb mongo admin

db.createUser({ user: 'root', pwd: 'root', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });
```

## 安装部署 Postgresql
```bash
docker run --name postgres -e POSTGRES_PASSWORD=root -p 5432:5432 -v /my/postgres/pgdata:/var/lib/postgresql/data -d postgres
```
## 安装部署 nextcloud
```bash
docker run -d --restart=always --name nextcloud -p 80:80 -v /my/nextcloud:/data docker.io/nextcloud
```
## 安装部署 elasticsearch
```bash
docker run -e ES_JAVA_OPTS="-Xms256m -Xmx256m" -d --name elasticsearch  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch
```