# harbor 安装与使用
### 离线安装
- **[下载地址](https://storage.googleapis.com/harbor-releases/release-1.5.0/harbor-offline-installer-v1.5.1.tgz)**

### 修改配置
- vi harbor.cfg hostname = ?
- (可选)更改默认端口
	1. vi docker-compose proxy.ports=1180:80
	2. vi common/templates/registry/config.yml auth.token.realm=$public_url:1180/service/token
- 修改存储地址
```
vi docker-compose.yml   registry.volumes=/path
```
	
### 启停操作
- 初始化配置启动 sh install.sh
- 容器清理数据保留
```
docker-compose down -v
```
- 数据清理
```sh
$ rm -r /data/database
$ rm -r /data/registry
```

### docker使用私服
- 修改配置 
```
vi /etc/docker/daemon.json  #"insecure-registries" : ["192.168.251.157:1180"]
```
- 重启docker
```
systemctl restart docker
```
- 登录docker
```
docker login -u admin -p Harbor12345 192.168.251.157:1180
```
- push镜像到harbor私服
```
docker tag SOURCE_IMAGE[:TAG] 192.168.251.157:1180/yusp/IMAGE[:TAG]
docker push 192.168.251.157:1180/yusp/IMAGE[:TAG]
```
