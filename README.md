# Polina
Перед началом установки, нужно установить Linux Oracle в VirtualBox, для этого нужного:
Иметь образ Linux dsltkbnm 2 zlhf/ Dsltkbnm 5096+ МБ оперативы.

Далее переходим к установке docker с использованием grafana, вводим следующий набор команд:
1. sudo yu install wget
- устанавливает утилиту wget на нашу систему
![VirtualBox_Petrunina_14_02_2025_19_49_40](https://github.com/user-attachments/assets/c7a826ad-32cc-4d20-9238-37a06894471d)
2. sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
- Скачиваем файл репозитория
![3](https://github.com/user-attachments/assets/1c78dcec-3186-42b5-9fcf-b7be03fd0f80)
3. sudo yum install docker-ce docker-ce-cli containerd.io
- Устанавливаем docker
![4](https://github.com/user-attachments/assets/941c0529-6d2e-4440-85cc-aaef436ea277)
4. sudo systemctl enable docker --now
- Запускаем и разрешаем автозапуск
5. sudo yum install curl
- Для этого убедимся в наличие пакета
6. COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)
- Объявление переменной COMVERT, полученной в результате curl запроса, хранящей в себе номер последней версии Docker Compose
7. sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
- Теперь скачиваем скрипт docker-compose последней версии, используя объявленную ранее переменную и помещаем его в каталог /usr/bin
![6](https://github.com/user-attachments/assets/ff39d03e-9ad7-4bca-b1d6-289e0764e034)
8. sudo chmod +x /usr/bin/docker-compose
- Представление прав на выполнение файла docker-compose
9. docker-compose --version
- Проверка установленных версии docker-compose
  
![9](https://github.com/user-attachments/assets/259acd80-6ea0-4ce1-8f29-8912fe494710)
- Можно скачать git прямо из командной строки прописав Y
10. ![10](https://github.com/user-attachments/assets/884bbe0d-a21b-47ca-b0ba-6a4d4b94ffb3)
![Fail](https://github.com/user-attachments/assets/5e3b4dfb-61ac-43ed-8042-6a6e5826e264)
![Problem](https://github.com/user-attachments/assets/0b0f9b74-2f52-464a-bec3-6f2b7605e1e9)
![+](https://github.com/user-attachments/assets/72c9be2d-0aa0-4bde-bd87-ccebb87bf70a)
