# Наброски

#### Поддерживамые среды разворачивания 

* docker-compose
* kubernetes cluster with helm 

##### docker-compose

Поддерживает разворачивание из нескольких .yaml файлов, - [пример](example/docker-compose).   

##### kubernetes with helm
 
В репозитории микросервиса есть папка `deploy/helm/{SERVICE_NAME}`, в которой есть все необходимое для разворачивания
этого микросервиса в k8s, но без его зависимостей.

Но helm поддерживает [зависимости](https://github.com/helm/helm/blob/master/docs/helm/helm_dependency.md)

Helm charts store their **dependencies in** `'charts/'`. 

For chart developers, it is often easier to manage a single
**dependency file** (`'requirements.yaml'`) which declares all dependencies
 
```
# requirements.yaml
dependencies:
- name: nginx
  version: "1.2.3"
  repository: "file://../dependency_chart/nginx"
```
