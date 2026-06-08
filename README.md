# Zabbix Monitoring Stack
 
![Zabbix](https://img.shields.io/badge/Zabbix-7.4-red?style=flat&logo=zabbix)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=flat&logo=docker)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat&logo=mysql&logoColor=white)
 
Стек мониторинга на базе Zabbix 7.4, развёрнутый через Docker Compose с MySQL в качестве бэкенда.
 
## Состав стека
 
- **Zabbix Server 7.4** — ядро мониторинга
- **Zabbix Web** (Nginx + MySQL) — веб-интерфейс
- **Zabbix Agent** — сбор метрик с хоста
- **MySQL 8.0** — база данных
## Быстрый старт
 
```bash
cp .env.example .env
# Задайте пароли в .env
docker compose up -d
```
 
Веб-интерфейс: http://localhost:8090  
Логин: `Admin` / Пароль: `zabbix`
 
## Конфигурация
 
Все чувствительные параметры вынесены в `.env` файл. Пример — в `.env.example`:
 
```env
MYSQL_DATABASE=zabbix
MYSQL_USER=zabbix
MYSQL_PASSWORD=your_password_here
MYSQL_ROOT_PASSWORD=your_root_password_here
```
 
`.env` добавлен в `.gitignore` и не попадает в репозиторий.
 
## Что мониторится
 
- Загрузка CPU (кастомный триггер: avg > 0.1 за 5 минут)
- Утилизация памяти
- Использование дискового пространства
- Сетевые интерфейсы
- Аптайм системы
## Скриншот
 
![Dashboard](dashboard.png)