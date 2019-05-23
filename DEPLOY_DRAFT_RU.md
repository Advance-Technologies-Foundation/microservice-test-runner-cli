# Наброски

#### Поддерживамые среды разворачивания 

* docker-compose
* kubernetes cluster with helm 

##### docker-compose

Поддерживает разворачивание из нескольких `.yaml` файлов, - [пример](example/docker-compose).  

docker-compose [поддерживает](https://docs.docker.com/compose/compose-file/#depends_on) возможность указывать от каких
 сервисов зависит конкретный сервис `depends_on`. 
 
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

#### Предполагаемая структура репозитория сервиса

**Вариант A**
```
├── ...
├── deploy

|   ├── .Dockerfile
|   |
|   ├── helm
|   |   |── templates
|   |   |── values.yaml # переменные окружения (зависимости)
|   |   |── ...
|   |
|   └── docker-compose
|   |   |── docker-compose.yaml
|   |   |── env.yaml # переменные окружения (зависимости)
|   |
|   └── .buid
|       |── info.yaml
|       |── deps.yaml
|
├── README.md
```

**info.yaml**
```$xslt
name: account-service
image: bpmonline/account-service
```

**deps.yaml**
```
dependencies:
    - name: permission-service
      git: http://tscore-git/bpmonline-designer/backend/permission-service
    - name: mongodb
      git: http://tscore-git/bpmonline-designer/infrastructure/mongodb
```

**Вариант B**

```
...
```
