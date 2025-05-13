# Fail2Ban Setup Script

Автоматический скрипт для установки и настройки Fail2Ban на сервере Linux (Ubuntu/Debian). Предназначен для защиты SSH от brute-force атак.

## 📜 Что делает скрипт

- Обновляет список пакетов
- Устанавливает `fail2ban`, если он не установлен
- Создает конфигурационный файл `/etc/fail2ban/jail.local`
- Настраивает правила для защиты `sshd`
- Перезапускает службу `fail2ban`

## ⚙️ Установка и запуск

1. Клонируй репозиторий:
   ```bash
   git clone https://github.com/Azatkabrata/fail2ban-setup.git
   cd fail2ban-setup

chmod +x setup_fail2ban.sh
Запусти от имени root или через sudo:
sudo ./setup_fail2ban.sh
