ip a, здесь можно узнать есть ли и какой айпи, интерфейс сети - у меня ens33(пригодилось при натройке), если кратко то сетевые интерфейсы и адреса
<img width="1270" height="400" alt="ip a" src="https://github.com/user-attachments/assets/cf5e2ccd-bfe5-4afb-97de-64b42b1cc3e5" />
таблица муршрутизации, отображает текущую и по умолчанию
<img width="952" height="161" alt="ip r" src="https://github.com/user-attachments/assets/af6b8a5f-8814-4d35-aa67-7f4ffa02f6a3" />
cat/etc/resolv.conf видим в середине команду статус и пробуем ее
<img width="1074" height="535" alt="cat resolve 1 где видим команду status" src="https://github.com/user-attachments/assets/6f6ce930-d7cf-4d7a-89e5-5bd9195aa7f6" />
видим текущие используемые сервера (dns)
<img width="1287" height="309" alt="сама resolvectl status" src="https://github.com/user-attachments/assets/e7bc7c19-be62-48a6-a735-32d92d73e593" />

ping`и сначала по адресу потом по имени  
<img width="975" height="445" alt="pings" src="https://github.com/user-attachments/assets/95828770-e814-4561-b55d-5dfa4008a6b6" />

tulpn отображает активные открытые порты и слушашие службы
<img width="1298" height="343" alt="tulpn" src="https://github.com/user-attachments/assets/4183afde-6216-4177-8891-a1c191dc845f" />



Вопросы:
1. Какой адрес получила машина и откуда? - тачка получила адрес 192.168.244.128/129 на интерфейсе сетевом ens33, адрес был получен автоматически по протоколу dhcp/службу systemd-networkd
тк это арч линукс и сеть была не настроена из коробки пришлось вручную создавать файл профиля с параметром dhcp=yes и также вручную активировать службу systemd-networkd
2. Какой шлюз по умолчанию? - по ip r выясняем дефолтный шлюз 192.168.244.2
3. Какие службы слушают порты сразу после установки? - по команде ss -tulpn смотрим: слушают: systemd-resolve и sshd слушает 22 порт 
4. Разница меж результатами ping по адрему и по имени
 ping по 4 8.8.8.8 проверяет базовую связанность
 ping по имени ya.ru сначала делает днс запрос к указанным именам из конфига resolv для преобразования имени в ip 
