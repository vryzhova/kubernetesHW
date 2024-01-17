# kubernetesHW
 
### Шаги исполнения
### Docker

1. Установка docker
```
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker run hello-world
```

2. [DockerFile](https://github.com/vryzhova/kubernetesHW/blob/main/docker/Dockerfile)

3. Cборкa Docker образа и разворачивания контейнера на порту 8000
```
docker run -d --name app_container -p 8000:8000 web:1.0.0
docker buildx build --tag web:1.0.0 .
```

4. Заливка образа на Docker Hub
```
docker image tag web:1.0.0 docker.io/vryzhova0309/web:1.0.0
docker push vryzhova03/web:1.0.0
```
###Kuber
5. Установка minikube на ubuntu архитектура arm64

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm64
install minikube-linux-arm64 /usr/local/bin/minikube
minikube start
```

6. [Deployment manifect](https://github.com/vryzhova/kubernetesHW/blob/main/kuber/deployment-file.yaml)

7. Применение манифеста  и port forwarding

```
minikube kubectl -- apply -f ./deployment-file.yaml
minikube kubectl -- port-forward --address 0.0.0.0 deployment/web 8080:8000
```
8. [Результат команды “kubectl describe deployment web”](https://github.com/vryzhova/kubernetesHW/blob/main/kuber/describe-cmd-output.yaml) 

9. [Результат](./screen.png)
