# test-runner-cli

[RU](README_RU.md)

### Problem
How SIMPLE RUN specific tests (unit, ingeration, api, components, system, etc...) IN LOCAL machine with docker?

### Solution 
Run tests with test-run-cli

Example:
+ ```npm i -g test-run-cli```
+ ```test-run-cli run [unit | ingeration | api | components | system]```
This command deploy, need application containers (with docker compose) to local docker machine 
and run specific tests. You don’t need k8s or another tools. Need only app repo, 
docker, docker-compose (in windows pc included in the default) and test-run-cli in local machine. 

### How it is works?

#### How problems solved 

+ partial build/rebuild docker containers
+ run docker containers with dependencies 
(like mongodb, rabbitmq, mock server, redis, etc... or dependencies application service) 
on a shared network (need for api, system, components tests)
+  
