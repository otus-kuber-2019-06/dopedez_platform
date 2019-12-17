# dopedez_platform
dopedez Platform repository

# 1st-homework:
  - Создан докерфайл с нужным пользователем и UID
  - подправлен конфи nginx + default
  - создана папка /app для проверки возврата страницы с localhost:8000/homework.html
  - создан и сблиджен docker image |
                                    docker build . ; docker tag %image_id% doped/nginx-without-su:latest ; docker push doped/nginx-without-su:latest

# 2nd-homework:
  - TASK 01:
      Создать Service Account bob, дать ему роль admin в рамках всего кластера;
      Создать Service Account dave без доступа к кластеру;
  - TASK 02:
      Создать Namespace prometheus;
      Создать Service Account carol в этом Namespace;
      Дать всем Service Account в Namespace prometheus возможность делать get, list, watch в отношении Pods всего кластера;
  - TASK 03:
      Создать Namespace dev;
      Создать Service Account jane в Namespace dev;
      Дать jane роль admin в рамках Namespace dev;
      Создать Service Account ken в Namespace dev;
# 3rd-homework:
    - Добавление проверок для pod/web
    - Создание deployment ./kubernetes-network/web-deploy.yaml
    - Создание сервисов ./kubernetes-network/web-svc-cip/yaml 
    - Cluster IP |
                 %host% ssh ; sudo -i ; iptables --list -nv -t nat 
                 KUBE-SVC - service
                 KUBE-SEP - Service Endpoint
                 for more information chek https://msazure.club/kubernetes-services-and-iptables/
    - Включение IPVS |
                for more information check https://github.com/kubernetes/kubernetes/blob/master/pkg/proxy/ipvs/README.md
    - Ingress |
                for more information https://kubernetes.github.io/ingress-nginx/deploy/#bare-metal                
#4th homework 
``` # kubernetes-volumes
git checkout -b kubernetes-volumes
mkdir kubernetes-volumes && cd kubernetes-volumes

# install kind
brew install kind
# my specifics - make kind specific config and export it via variable
# check that it uses your config
kind get kubeconfig-path # deprecated
kind create cluster

# now let's install MinIO- local S3 storage
curl -O https://raw.githubusercontent.com/express42/otus-platform-snippets/master/Module-02/Kuberenetes-volumes/minio-statefulset.yaml
# edit it to stop yaml linter complaining :-(
# change apiVersion to apps/v1 as well, 1.16 here
kubectl apply -f minio-statefulset.yaml

# now create headless service
curl -O https://raw.githubusercontent.com/express42/otus-platform-snippets/master/Module-02/Kuberenetes-volumes/minio-headless-service.yaml
kubectl apply -f minio-headless-service.yaml

# now test it
# install minio cli - mc
brew install minio/stable/mc
mc ls

# test k8s resources as well
kubectl get statefulsets
kubectl get pods
kubectl get pvc
kubectl get pv

# now delete it all
kubectl delete cluster

# now commit everything and prepare PR
# Выполнено ДЗ №4

 - [*] Основное ДЗ

## В процессе сделано:
 - Практика использования:
   - volumes
   - statefulset

## Как запустить проект:
```sh
kind create cluster
kubectl apply -f . --recursive
```
## Как проверить работоспособность:
 - `mc ls`

## PR checklist:
 - [*] Выставлен label с номером домашнего задания ```