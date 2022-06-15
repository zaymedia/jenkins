# Установка Jenkins через Ansible

**Development**
- Запустить команду: make init
- Открыть сервер по пути: localhost:8000

**Production**
1. Создать файл hosts.yml по примеру из hosts.yml.dist
2. Добавить A запись в DNS домена
3. Установить ansible на локальный компьютер:
   1. brew install ansible
   2. brew install ansible-lint
   3. brew link ansible
4. Перейти в папку provisioning (cd provisioning/)
5. Запустить команду: make server
   1. Если возникнет ошибка "Permission denied (publickey,password)", запустить команду: ssh-copy-id -i ~/.ssh/id_rsa.pub root@**_HOST_**
   2. Если возникнет ошибка на этапе с "Add Certbot repository" - нужно перейти на Debian 10
6. Запустить команду: make authorize
7. Вернуться в папку выше (cd ../)
8. Запустить deploy командой: HOST=**_HOST_** PORT=22 make deploy
9. Если ошибка с 80 портом, то перезагрузить сервер
10. Для получения ключа для Jenkins необходимо перейти в папку provisioning (cd provisioning/) и запустить команду: make show-initial-password 
