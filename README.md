# dopedez_platform
dopedez Platform repository

# 1st-homework:
  - Создан докерфайл с нужным пользователем и UID
  - подправлен конфи nginx + default
  - создана папка /app для проверки возврата страницы с localhost:8000/homework.html
  - создан и сблиджен docker image |
                                    docker build . ; docker tag %image_id% doped/nginx-without-su:latest ; docker push doped/nginx-without-su:latest
                                    
