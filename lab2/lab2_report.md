University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)    
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)    
Year: 2022/2023  
Group: K34212  
Author: Demidyuk Oleg Sergeevich  
Lab: Lab2  
Date of create: 28.11.2022  
Date of finished: ... 

Цель работы:С помощью Ansible настроить несколько сетевых устройств и собрать информацию о них. Правильно собрать файл Inventory.

Ход работы:
1. Был установлен второй CHR на виртуальной машине. Организован второй Wireguard на CHR.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/1.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/2.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/3.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/4.jpg)

2. Было проверено подключение первой CHR машины. 

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/5.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/6.jpg)

3. Ansible работает через ssh, поэтому для начала его стоит натсроить на обоих CHR. 

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/7.jpg)

4. Осуществлена первая настройка Ansible, создана директория, добавлен файл hosts.ini с ip роутеров.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/9.jpg)

5. Создан первый плейбук playbook.yaml.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/8.jpg)

6. Появилась ошибка.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/10.jpg)

7. Были скачены дополнительные Pytnoh библиотеки.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/11.jpg)

8. Плэйбук выполнен успешно. Используя Ansible, настроены пользователи(логин/пароль), настроены NTP-клиенты, настроен OSPF роутинг сразу на двух CHR.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/16.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/17.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/18.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/19.jpg)

9. Проверена работа OSPF, в случае корректной работоспособности роутеры будут видеть друг друга как соседи.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/20.jpg)

10. Создан плейбук collect.yml. Он предназначен для сбора данных по OSPF и полного конфига сразу двух CHR машин, после чего конфигурация сохранена в файлы r1.jason и r2.jason. 

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/30.jpg)

11. Не удалось успешно запустить плейбук. Нет прав создавать файлы конфигурации.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/24.jpg)

12. С помощью chmod исправили ситуацию. Плейбук выполнен успешно.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/25.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/26.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/27.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/28.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/29.jpg)

13. Составлена схема сети.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab2/screenshots/31.jpeg)

Вывод: В ходе выполнения работы был создан ещё один CHR. Были получены навыки составления плейбуков. После чего с помощью Ansible была проведена настройка обоих CHR, созданы пользоваетели, настроент NTP-клиент, OSPF.







