# gitlab����Devops
### runner����
- executoĬ��ʹ��shell���ع���,[runner��ϸ����](https://gitlab.com/gitlab-org/gitlab-runner/blob/master/docs/configuration/advanced-configuration.md "runner����")
- runnerִ�й���������dockerȨ�����⣬runner��--user gitlab-runner�����������û�����docker�û��鼴��
```
vi /etc/passwd
�û���:����:�û���ʶ��:���ʶ��:ע��������:��Ŀ¼:��¼Shell
```

### .gitlab-ci.yml
- [�����﷨����](http://192.168.251.157/root/spring-boot-docker/-/ci/lint)
- ����ʹ��
```
build:
  stage: build
  script:
    - mvn compile
  tags:
    - tag-157
```
- [ʹ��gitlab ci����springbootӦ�õ�k8s](https://about.gitlab.com/2016/12/14/continuous-delivery-of-a-spring-boot-application-with-gitlab-ci-and-kubernetes/ "ʹ��gitlab ci����springbootӦ�õ�k8s")
