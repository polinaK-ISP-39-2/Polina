# Polina
Перед началом установки, нужно установить Linux Oracle в VirtualBox, для этого нужного:
Иметь образ Linux 5096+ МБ оперативы.

Далее переходим к установке docker с использованием grafana, вводим следующий набор команд:
1. ```sudo yu install wget```
- устанавливает утилиту wget на нашу систему
![VirtualBox_Petrunina_14_02_2025_19_49_40](https://github.com/user-attachments/assets/c7a826ad-32cc-4d20-9238-37a06894471d)
2. ```sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo```
- Скачиваем файл репозитория
![3](https://github.com/user-attachments/assets/1c78dcec-3186-42b5-9fcf-b7be03fd0f80)
3. ```sudo yum install docker-ce docker-ce-cli containerd.io```
- Устанавливаем docker
![4](https://github.com/user-attachments/assets/941c0529-6d2e-4440-85cc-aaef436ea277)
4. ```sudo systemctl enable docker --now```
- Запускаем и разрешаем автозапуск
5. ```sudo yum install curl```
- Для этого убедимся в наличие пакета
6. ```COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)```
- Объявление переменной COMVERT, полученной в результате curl запроса, хранящей в себе номер последней версии Docker Compose
7. ```sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose```
- Теперь скачиваем скрипт docker-compose последней версии, используя объявленную ранее переменную и помещаем его в каталог ```/usr/bin```
![6](https://github.com/user-attachments/assets/ff39d03e-9ad7-4bca-b1d6-289e0764e034)
8. ```sudo chmod +x /usr/bin/docker-compose```
- Представление прав на выполнение файла docker-compose
9. ```docker-compose --version```
- Проверка установленных версии docker-compose
  
![9](https://github.com/user-attachments/assets/259acd80-6ea0-4ce1-8f29-8912fe494710)
- Можно скачать git прямо из командной строки прописав Y
10. ![10](https://github.com/user-attachments/assets/884bbe0d-a21b-47ca-b0ba-6a4d4b94ffb3)
  - Как заметим, произошла ошибка; ```Не удалось установить пакеты: Failed  to obtain authentication```
![Fail](https://github.com/user-attachments/assets/5e3b4dfb-61ac-43ed-8042-6a6e5826e264)
Что бы избавиться от проблемы, было принято ввести команду с использованием sudo, права суперпользователя. Это нужно, если мы хотим установить или изменить что-то в системе: ```sudo git clone https://github.com/skl256/grafana_stack_for_docker.git```
`sudo yum install git - команда, которая установила Git на систему.
![Problem](https://github.com/user-attachments/assets/0b0f9b74-2f52-464a-bec3-6f2b7605e1e9)
Ошибка была исправлена, Git был установлен.
![+](https://github.com/user-attachments/assets/72c9be2d-0aa0-4bde-bd87-ccebb87bf70a)
11. ```cd grafana_stack_for_docker```
    - переходим с помощью этой команды в нужную нам папку.
12. ```sudo mkdir -p /mnt/common_volume/grafana```
    - команда создает полный путь /mnt/common_volume/swarm/grafana/config, включая все все необходимые промежуточные каталоги, если они не существуют
13. ```sudo mkdir -p /mnt/common_volume/swarm/grafana/config```
![Снимок](https://github.com/user-attachments/assets/85eb0b76-c4e3-4f97-b262-c9b58b80f967)
    - команда создает структуру каталогов для Grafana и связанных с ней компонентов, если они ещё не существуют
14. ```sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}```
    - все файлы и каталоги в указанных директориях будут переделаны в собственность  текущему пользователю и его группе
![12](https://github.com/user-attachments/assets/440ad579-f46b-46e3-a552-4fd74adc645f)
15. ```touch /mnt/common_volume/grafana/grafana-config/grafana.ini```
    - файл уже существует. Команда обновит его временые метки.
16. ```cp config/* /mnt/common_volume/swarm/grafana/config/```
    - команда копирует все файлы и подкаталоги из директории config в директорию ```/mnt/common_volume/swarm/grafana/config/```
17. ```sudo mv grafana.yaml docker-compose.yaml```
![18](https://github.com/user-attachments/assets/421e9d3b-6780-42c1-9308-9c2f1b04af30)
    - команда переименовывает файл -grafana.yaml в docker
18. ```sudo docker compose up -d```
![image](https://github.com/user-attachments/assets/80745329-dbf0-448f-ae17-f34942366d6c)
    - команда создает и запускает контейнеры в фоновом режиме, используя конфигурация из файлов docker-compromise.yml с правами суперпользователя.
![stop](https://github.com/user-attachments/assets/4be56df0-e4f4-4bc7-a551-d1ad0bb1fdcc)
19. ```sudo vi docker.compromise.yaml```
    - эта команда предназначена для редактирования конфигурационного файла docker.compromise.yaml с правами суперпользователя.
![1](https://github.com/user-attachments/assets/93e53952-f3c1-49ee-91a7-724187735fe0)
![2](https://github.com/user-attachments/assets/3fdcddba-e665-499f-b51a-73bcfeb36cdd)
20. sudo docker ps
    -  эта команда позволяет увидеть текущие активные контейнеры в системе.
![-а](https://github.com/user-attachments/assets/92a10830-259b-44c7-8d0c-fd1ab7617708)
21. 




