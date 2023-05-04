## Тестовое задание: Автоматизированное обновление операционной системы c помощью Ansible  

Задание по ссылке: https://github.com/Raiffeisen-DGTL/DevOps-Bootcamp/tree/main/ansible.  

### Результат:  

1. Написана [Ansible `role`](https://github.com/OborinMaxim/devops-bootcamp/blob/master/Ansible/roles/upgrade/tasks/main.yml) для обновления операционной системы Ubuntu:  
   - обновление системы реализовано с помощью модуля `apt`; результат выполнения задачи регистрируется с помощью модуля `register`;  
   - если выполненная задача привела к изменениям, выполняется перезагрузка сервера - реализовано с помощью `when` и модуля `reboot`;  
   - реализовано исключение обновления пакета `git` с помощью модуля `dpkg_selections`;  
   - после обновления операционной системы удаляются неиспользуемые ядра Linux и зависимости - реализовано с помощью модуля `apt` и его параметров `autoremove` и `purge`; в качестве альтернативы для удаления старых ядер, кроме последнего и предпоследнего, можно с помощью модуля `command` передать на сервер команду `apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)`.
2. Создан [`inventory` файл](https://github.com/OborinMaxim/devops-bootcamp/blob/master/Ansible/inventory.yml), в котором создана группа `servers` и внесен `localhost` сервер.
3. Создан [`playbook`](https://github.com/OborinMaxim/devops-bootcamp/blob/master/Ansible/site.yml) для запуска написанной `role`. Команда для его отработки: `ansible-playbook -i inventory.yml site.yml`.  

Структура каталога построена с учетом [лучших практик](https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html) Ansible.