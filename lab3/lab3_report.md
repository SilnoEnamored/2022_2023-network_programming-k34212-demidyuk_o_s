University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)    
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)    
Year: 2022/2023  
Group: K34212  
Author: Demidyuk Oleg Sergeevich  
Lab: Lab2  
Date of create: 11.12.2022  
Date of finished: ...

Цель работы:С помощью Ansible и Netbox собрать всю возможную информацию об устройствах и сохранить их в отдельном файле.

Ход работы:

1.На Yandex Cloud была поднята ещё одна виртуальная машина Ubuntu 20.04. Был установлен NetBox и запущен сервер http://51.250.126.78:8000/, подключилсь по http.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/1.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/2.jpg)

2. Заполнена некотарая информация о CHR машинах в Netbox.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/3.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/4.jpg)

3. Машина соединена с главной машиной, используя Wireguard тунель по аналогии с предыдущими работами.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/5.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/6.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/7.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/8.jpg)

4. Далее используя Ansible нам необходимо сохранить все данные в отдельный файл. Для этого меняем файл hosts.ini, добавляя группу [Netbox]. Создаем плейбук collect_netbox.yml. Запускаем плейбук. 
```
sudo ansible-playbook collect_netbox.yml -i hosts.in
```

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/9.jpg)
