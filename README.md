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