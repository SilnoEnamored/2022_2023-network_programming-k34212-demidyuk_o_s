University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)    
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)    
Year: 2022/2023  
Group: K34212  
Author: Demidyuk Oleg Sergeevich  
Lab: Lab3  
Date of create: 12.12.2022  
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

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/9.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/10.jpg)

```
sudo ansible-playbook collect_netbox.yml -i hosts.in
```
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/11.jpg)

5. Написан и запущен плейбук, который изменяет имя и добавляет Ip адрес на роутеры. Так же сверяет их до и после запуска. 

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/12.jpg)
```
sudo ansible-playbook changed.yml -i hosts.ini
```
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/13.jpg)

6. Написан и запущен плейбук, который собирает сериёные номера роутеров и добавляет их в Nebox.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/14.jpg)
```
sudo ansible-playbook serialnumber.yml -i hosts.ini
```
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/15.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/16.jpg)

7. Теперь у роутеров в Netbox появился серийный номер.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/17.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/18.jpg)

8. Обновлена схема сети.
 
![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/19.jpeg)

Пинг между Netbox и главной машиной.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/19.jpg)

Пинг между Netbox и CHR машинами.

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/20.jpg)

![Image text](https://github.com/SilnoEnamored/2022_2023-network_programming-k34212-demidyuk_o_s/raw/main/lab3/screenshots/21.jpg)
Вывод:
Была создана ещё одна виртуальная машина на Ubuntu 20.04 c Netbox, проложен Wireguard тунель к основной машине. Познакомились с инстурментом документирования сетей Netbox. С помощью Ansible и Netbox были настроены обе CHR машины. 
