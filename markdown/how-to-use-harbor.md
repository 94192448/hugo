#harbor ��װ��ʹ��
### ���߰�װ
- **[���ص�ַ](https://storage.googleapis.com/harbor-releases/release-1.5.0/harbor-offline-installer-v1.5.1.tgz)**

### �޸�����
- vi harbor.cfg hostname = ?
- (��ѡ)����Ĭ�϶˿�
	1. vi docker-compose proxy.ports=1180:80
	2. vi common/templates/registry/config.yml auth.token.realm=$public_url:1180/service/token
- �޸Ĵ洢��ַ
```
vi docker-compose.yml   registry.volumes=/path
```
	
### ��ͣ����
- ��ʼ���������� sh install.sh
- �����������ݱ���
```
docker-compose down -v
```
- ��������
```sh
$ rm -r /data/database
$ rm -r /data/registry
```

### dockerʹ��˽��
- �޸����� 
```
vi /etc/docker/daemon.json  #"insecure-registries" : ["192.168.251.157:1180"]
```
- ����docker
```
systemctl restart docker
```
- ��¼docker
```
docker login -u admin -p Harbor12345 192.168.251.157:1180
```
- push����harbor˽��
```
docker tag SOURCE_IMAGE[:TAG] 192.168.251.157:1180/yusp/IMAGE[:TAG]
docker push 192.168.251.157:1180/yusp/IMAGE[:TAG]
```