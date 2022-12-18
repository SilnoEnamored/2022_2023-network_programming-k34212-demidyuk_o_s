University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)    
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)    
Year: 2022/2023  
Group: K34212  
Author: Demidyuk Oleg Sergeevich  
Lab: Lab4  
Date of create: 18.12.2022  
Date of finished: ...

Цель работы: Изучить синтаксис языка программирования P4 и выполнить 2 задания обучающих задания от Open network foundation для ознакомления на практике с P4.

Ход работы:

1.1 Склонирован репозиторий p4lang/tutorials.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/1.jpg)

1.2 С помощью Vagrant была поднята VM P4 Tutorial Release 2022-12-18.
```
vagrant up 
vagrant provision
```
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/2.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/3.jpg)

1.3 Выполнен вход в учётную запись p4/p4. Выполнена первичная конфигурация сети "Basic Forwarding" при помощи Makefile. После этого запускается mininet схема.
```
make build
make run
```
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/4.jpg)

Проверяем пинг между хостами сети, свзязь не удалась, так как файл basic.p4 необходимо отредактировать.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/5.jpg)

1.4 Далее приступаем к редактированию файл basic.p4.
Добавлены парсеры для ethernet и ipv4.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/6.jpg)
 
 Добавлена логика для пересылка ipv4 пакетов, которая устанавливает выходной порт, обновляет MAC адрес назначения и исходный, уменьшает значение ttl.
 
 ![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/7.jpg)
 
 Добавлена проверка ipv4 пакета. 
 
 ![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/8.jpg)
 
 Добавлен депарсинг заголовков ethernet и ipv4.
 
 ![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/9.jpg)
 
 Затем заново сконфигурирована сеть при помощи Makefile и проверена связь хостов.
 ```
 pingall
 ```
 
 ![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/10.jpg)
 
 1.5 Схема сети basic.p4 Basic Forwarding.

 ![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab4/screenshots/15.jpg)
