University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)    
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)    
Year: 2022/2023  
Group: K34212  
Author: Demidyuk Oleg Sergeevich  
Lab: Lab1  
Date of create: 28.11.2022  
Date of finished: ... 

Цель работы: Развернуть виртаульную машину на Яндекс Облаке с установленной системой контроля конфигурации Ansible, установка CHR в VirtualBox и организовать VPN между ними.   
Ход работы:
1. Была создана виртульная машина на Yandex Cloud на Ubunt, установлено соединение по ssh. Обновлена операционная система. 
 
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/1.jpg)

2. На виртуальную машину установлен python3.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/2.jpg)

3. Так же установлен Ansible.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/3.jpg)

4. Создана виртуальная машина CHR в VirtualBox.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/4.jpg)
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/5.jpg)

5. Так как было решено работать с MikroTik при помощи графичесокго интерфейса WinBox, то была создана новая виртуальная машина CHR с версией MikroTik 7.6.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/6.jpg)

6. Установлен ip адресс виртуальной машины CHR, по нему WinBox был подключен.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/7.jpg)

7. В качестве VPN был выбран WireGuard. На удаленной виртуальной машине установлен WireGuard.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/8.jpg)

8. Возникли проблемы с правами при переходе в папку Wireguard, они были решены. Создана пара приватного и публичного ключа. Публичный ключ нам понадобиться для настройки WireGuard на CHR машине через WinBox.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/10.jpg)

9. Далее был настроен wg0.conf Interface и Peer wireguard на удаленной виртуальной машине. ListenPort взяли любой свободный порт, приватный ключ взяли из прошлого шага. Публичный ключ(ключ CHR) сгенерировали при помощи WinBox и вставили сюда.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/11.jpg)

10. При помощи WinBox настроили Interface WireGuard на CHR машине. Сгенерировали пару ключей. ListenPort использовали такойже, как в предыдущем шаге.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/12.jpg)

11. При помощи WinBox настроили Peer WireGuard на CHR машине. Публичный ключ взяли из ключа на удаленной виртуальной машине. 

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/13.jpg)

12. Последняя настройка WireGuard. Добавили ip адрес.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/14.jpg)

13. На удаленной виртуальной машине активирован сервис. Из CHR пропингована удаленная машина по внутреннему Ip туннеля, для того чтобы Wireguard клиент начал отправлять keepalive пакеты для поддержки существования туннеля.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/15.jpg)

14. Проверили существование VPN тунеля между машинами при помощи ping.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/16.jpg)
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab1/screenshots/17.jpg)

Вывод: В ходе выполнения работы были созданы две виртуальные машины (Unbuntu и CHR). Между ними был создан VPN тунель WireGuard. Для работы с RouterOS очень удобно использовать графический интерфейс WinBox. Необходимо быть очень внимательным с Ip и публичными ключами, если допустить ошибку, то ничего работать не будет совсем.
