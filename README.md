TICK stack

1. Подключение репозитория influx
/etc/apt/sources.list.d/influxdata.list
deb [signed-by=/usr/share/keyrings/influxdata-archive.gpg] https://repos.influxdata.com/debian stable main

2. Установка из него всех компонентов (Influxdb, Chronograf, Kapacitor, Telegraf)
    sudo apt install telegraf
    sudo apt install influxdb
    sudo apt install chronograf
    sudo apt install kapacitor

4. Создание конфигурации telegraf для сбора метрик со всех компонент и проверка через.
    sudo telegraf --config /etc/telegraf/telegraf.conf --config-directory /etc/telegraf/telegraf.d --test
   Проверка коректности вывода - вывод в файл.

5. Настройка influxdb
    Создание базы данных influxdb для сбора метрик
    influx -execute "CREATE DATABASE my_metrics"

6. Настройка конфигурации telegraf для отправки данных в influxdb (out.conf)

7. Проврка, что данные собираются:
        influx -database 'my_metrics' -execute 'SHOW MEASUREMENTS'
        name: measurements
        name
        ----
        cpu
        cpu_load
        disk
        http_response
        kernel
        mem
        mysql
        net
        nginx
        phpfpm
        processes

8. Настройка chronograf. Настройка подключения к influxdb и kapacitor по портам, где слушается API
   "kapacitord" *:9092
   "influxd": *:8086
   
<img width="840" height="557" alt="image" src="https://github.com/user-attachments/assets/1df6f37e-27cf-47d7-a75a-8fa4045c47d8" />

<img width="840" height="557" alt="image" src="https://github.com/user-attachments/assets/3638441a-ee59-4c6d-aa6f-6c4a0ee07952" />

10. Создан Dashboard отражающий здоровье системы
    <img width="1772" height="290" alt="image" src="https://github.com/user-attachments/assets/4138013a-42f9-4c2a-b1d5-e3b67580016b" />
    
    <img width="1308" height="275" alt="image" src="https://github.com/user-attachments/assets/f92c2124-ea46-4589-a4b8-de966c2eecd2" />

    <img width="1266" height="527" alt="image" src="https://github.com/user-attachments/assets/20bde058-0d61-43db-bcf6-f3465d97e304" />

