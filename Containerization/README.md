## Тестовое задание: Docker-контейнер для Python-скрипта  

Задание по ссылке: https://github.com/Raiffeisen-DGTL/DevOps-Bootcamp/tree/main/containerization.  

### Результат:  

1. Создан [`playbook`](https://github.com/OborinMaxim/devops-bootcamp/blob/master/Ansible/site.yml) для запуска написанной `role`. Команда для его отработки: `ansible-playbook -i inventory.yml site.yml`.  

Созданы Dockerfile и docker-compose.yml для предоставленного Python-скрипта. Контейнеры успешно запускаются через `docker-compose up -d` и работают вместе, приложение Python работает на Flask и взаимодействует с Redis. Веб-страница отображается корректно, и после нажатия кнопки выводится подтверждение результата:

![](../pic/cont_result.jpg)