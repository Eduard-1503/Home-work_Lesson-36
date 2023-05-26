ДЗ №24: Строим бонды и вланы  (схема нормально отображается почемуто только в режиме редактирования)

Цель домашнего задания: Научиться настраивать VLAN и LACP.
Описание домашнего задания:
  - в office1 в тестовой подсети появляется сервера с доп интерфесами и адресами в internal сети testLAN:
    - testClient1 - 10.10.10.254
    - testClient2 - 10.10.10.254
    - testServer1- 10.10.10.1
    - testServer2- 10.10.10.1
    равести вланами:
      testClient1 <-> testServer1
      testClient2 <-> testServer2
  - между centralRouter и inetRouter "пробросить" 2 линка (общая inernal сеть) и объединить их в бонд, проверить работу c отключением интерфейсов

Для проверки представляю:
  - Vagrantfile развертывающий из трех роутеров, двух серверов и двух клиентов в соответствии со схемой в задании:

 _____________
|             |
|   vlan1     | vlan1
|             |_______
| testClient1 |       \
| testServer1 |        \
|_____________|         \        _______________         _______________         _______________
                         -----> |               |       |               |------>|               |
                                | office1Router |-----> | office1Router | bond0 | office1Router |
 _____________           -----> |_______________|       |_______________|------>|_______________|
|             |         /
|   vlan2     |        /
|             |_______/
| testClient2 | vlan2
| testServer2 |
|_____________|


  - playbook.yaml с помощью которого производится доустановка необходимых пакетов и конфигурация роутеров, серверов и клиентов для работы стенда;
  - а также подготовленные конфигурационные файлы  и hosts-файл используемые playbook-ом.
