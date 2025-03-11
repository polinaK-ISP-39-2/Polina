# Polina
Перед началом установки, нужно установить Linux Oracle в VirtualBox, для этого нужного:
Иметь образ Linux 5096+ МБ оперативы.

Далее переходим к установке docker с использованием grafana, вводим следующий набор команд:
1. ```sudo yu install wget```
- ***устанавливает утилиту wget на нашу систему***
![VirtualBox_Petrunina_14_02_2025_19_49_40](https://github.com/user-attachments/assets/c7a826ad-32cc-4d20-9238-37a06894471d)
- После выполнения этой команды система запросит подтверждение на установку и загрузит необходимые файлы, после чего утилита wget будет доступна для использования.

  
2. ```sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo```
- ***Команда используется для загрузки файла репозитория Docker для CentOS и сохранения его в определенном каталоге.***
![3](https://github.com/user-attachments/assets/1c78dcec-3186-42b5-9fcf-b7be03fd0f80)
- команда загружает файл docker-ce.repo с указанного URL и сохраняет его в директории /etc/yum.repos.d/. Файл репозитория необходим для настройки пакетного менеджера yum, чтобы он мог находить и устанавливать пакеты Docker.

  
3. ```sudo yum install docker-ce docker-ce-cli containerd.io```
- ***Эта команда устанавливает три ключевых компонента Docker на систему:***

     • ***Docker Community Edition (docker-ce)***: основной пакет, необходимый для работы с контейнерами.

     • ***CLI (docker-ce-cli)***: инструмент командной строки для взаимодействия с Docker.

     • ***Containerd (containerd.io)***: служба для управления контейнерами на уровне операционной системы.
![4](https://github.com/user-attachments/assets/941c0529-6d2e-4440-85cc-aaef436ea277)


4. ```sudo systemctl enable docker --now```
- Эта команда включает службу Docker и настраивает её на автоматический запуск при старте системы. Это важно для обеспечения работы контейнеров без необходимости вручную запускать службу после каждой перезагрузки.


5. ```sudo yum install curl```
Эта команда устанавливает пакет curl на вашу систему. Наличие curl может быть полезным для проверки доступности веб-ресурсов, загрузки файлов и выполнения различных сетевых запросов. Например, можем использовать curl для проверки состояния вашего веб-сервера или ***API***.


6. ```COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)```
- После выполнения этой команды, если текущая последняя версия Docker Compose — 1.29.2, то переменная COMVER будет содержать значение 1.29.2. Это значение можно использовать в последующих командах, например, для установки или обновления Docker Compose.
- ***Эта команда выполняет следующие действия***:
1. Отправляет запрос к GitHub API для получения информации о последнем релизе Docker Compose.
2. Извлекает строку, содержащую название тега (версию) из JSON-ответа.
3. Извлекает сам номер версии из этой строки.
4. Сохраняет полученное значение в переменной COMVER.

  
7. ```sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose```
- Теперь скачиваем скрипт docker-compose последней версии, используя объявленную ранее переменную и помещаем его в каталог ```/usr/bin```
- ***Эта команда выполняет следующие действия***:
1. С помощью curl она загружает исполняемый файл Docker Compose последней версии с GitHub.
2. Используя переменные $COMVER, $(uname -s) и $(uname -m), она формирует правильный URL для загрузки файла, соответствующего вашей операционной системе и архитектуре.
3. Сохраняет загруженный файл в каталоге /usr/bin под именем docker-compose.
![6](https://github.com/user-attachments/assets/ff39d03e-9ad7-4bca-b1d6-289e0764e034)


8. ```sudo chmod +x /usr/bin/docker-compose```
- После выполнения этой команды файл docker-compose получит право на выполнение, что позволит  запускать его из командной строки. Без этого шага не сможем использовать команду docker-compose, так как операционная система не распознает файл как исполняемый.

  
9. ```docker-compose --version```
- После выполнения этой команды в терминале вы получите вывод, содержащий номер версии установленного Docker Compose
![9](https://github.com/user-attachments/assets/259acd80-6ea0-4ce1-8f29-8912fe494710)
- Можно скачать git прямо из командной строки прописав Y

  
10.
    ![10](https://github.com/user-attachments/assets/884bbe0d-a21b-47ca-b0ba-6a4d4b94ffb3)
  - Как заметим, произошла ошибка; ```Не удалось установить пакеты: Failed  to obtain authentication```
![Fail](https://github.com/user-attachments/assets/5e3b4dfb-61ac-43ed-8042-6a6e5826e264)
        Что бы избавиться от проблемы, было принято ввести команду с использованием sudo, права суперпользователя. Это нужно, если мы хотим установить или изменить что-то в системе: ```sudo git clone https://github.com/skl256/grafana_stack_for_docker.git```
```sudo yum install git``` - команда, которая установила Git на систему.
![Problem](https://github.com/user-attachments/assets/0b0f9b74-2f52-464a-bec3-6f2b7605e1e9)
     ***Ошибка была исправлена, Git был установлен.***
![+](https://github.com/user-attachments/assets/72c9be2d-0aa0-4bde-bd87-ccebb87bf70a)


11. ```cd grafana_stack_for_docker```
    - Когда выполняется команда cd grafana_stack_for_docker, мы переходим в каталог grafana_stack_for_docker. Это значит, что все последующие команды, которые мы будем вводить в терминале, будут выполняться относительно этого каталога. Это удобно, так как мы можем работать с файлами и настройками, находящимися в этой папке, без необходимости указывать полный путь к ним.


12. ```sudo mkdir -p /mnt/common_volume/grafana```
    - После выполнения этой команды будет создан каталог /mnt/common_volume/grafana, включая все необходимые промежуточные каталоги. Это позволяет организовать структуру папок на вашем сервере или локальной машине для хранения данных Grafana, которые могут быть использованы для хранения конфигурационных файлов, логов или других данных. Создание такой структуры заранее помогает избежать проблем с отсутствующими директориями при запуске приложений и сервисов.
   
      
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

21. sudo docker compose stop
   - Останавливает все запущенные контейнеры, определённые в файле docker-compose.yml, но не удаляет их
![Без названия389_20250311174031](https://github.com/user-attachments/assets/9f69e0f9-f434-40b6-bb86-a4e5dffc2a6b)

23. 



