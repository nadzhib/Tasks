                                                                        Задание:
Имеется app.jar файл.
Для его запуска используется команда java -jar app.jar some_out_files “Service is working!”.
Напишите простой демон для systemd (Linux), который будет поддерживать работу приложения и перезапускать его в случае выхода из стоя процесса. 
Необходимо сделать защиту от зацикливания перезапусков, когда процесс постоянно выходит из строя.


                                                                          Решение:

1) Создаём папку java в домашней директории и копируем туда файл app.jar (Напрример, на моем ПК /home/administrator/java/app.jar)
2) В файле java.service подправляем путь для app.jar и some_out_files (У меня /home/administrator/java/app.jar /home/administrator/java/some_out_file)
3) Файл java.service нужно скопировать в папку etc/systemd/system
4) Обновляем репозиторий -> sudo apt update
5) Устанавливаем openjdk 17 ->  sudo apt install openjdk-17-jdk
6) Разрешаем запуск -> systemctl enable java.service
7) Запускаем -> systemctl start java.service
8) Смотрим статус -> systemctl status java.service
9) Применяем изменения в юнитфайле -> systemctl daemon-reload
10) Проверяем some_out_file, который будет лежать в домашей директории в папке java
