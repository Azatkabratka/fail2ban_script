#!/bin/bash

# Проверка, выполняется ли скрипт от root
if [[ $EUID -ne 0 ]]; then
   echo "Этот скрипт должен быть запущен от root" 
   exit 1
fi

echo "Обновление пакетов..."
apt update

echo "Установка fail2ban..."
apt install fail2ban -y

echo "Создание конфигурационного файла jail.local..."
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

echo "Настройка защиты SSH в jail.local..."
# Удаляем старый блок [sshd], если он есть, и добавляем наш
sed -i '/^\[sshd\]/,/^\[.*\]/d' /etc/fail2ban/jail.local

cat <<EOF >> /etc/fail2ban/jail.local

[sshd]
enabled = true
port    = ssh
logpath = /var/log/auth.log
maxretry = 3
findtime = 10m
bantime  = 5m
EOF

echo "Перезапуск fail2ban..."
systemctl restart fail2ban

echo "Fail2Ban установлен и настроен для SSH!"
