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
   
