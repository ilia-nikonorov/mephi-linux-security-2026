# ДЗ №1: Изучение средств защиты ОС GNU/Linux
**Курс:** Безопасность операционных систем  
**Репозиторий:** mephi-linux-security-2026  
## Описание выполненной работы
| Раздел | Задание | Реализация / Команды | Артефакт |
| :--- | :--- | :--- | :--- |
| **Раздел 1** | Создание пользователя `user1` (UID 1234) в группе `students`, смена пароля каждые 90 дней | `groupadd students`<br>`useradd -u 1234 -m -g students -s /bin/bash user1`<br>`chage -M 90 user1` | `passwd`, `shadow`, `group`, `stat.out` |
| **Раздел 2** | Мониторинг SUID-файлов и процессов с повышенными привилегиями (EUID=0, RUID!=0) | `find / -perm -4000 -type f`<br>`ps -eo pid,ruid,euid,user,comm \| awk '$3 == 0 && $2 != 0'` | `suid_files.out`, `suid_processes.out` |
| **Раздел 3** | Изучение механизма set-UID | Копирование `/bin/cat` в `/home/user1/my_cat`<br>`chmod u+s /home/user1/my_cat` для чтения закрытого файла `/root/secret.txt` | `stat.out` |
| **Раздел 4** | Изучение Linux Capabilities | Копирование `/bin/chown` в `/home/user1/my_chown`<br>`setcap cap_chown+ep /home/user1/my_chown` для смены владельца файла без root | `getcap.out`, `stat.out` |
| **Раздел 5** | Делегирование прав через `sudo` | Настройка `/etc/sudoers.d/user1-time` с разрешением запуска `/usr/bin/date` и `/usr/bin/timedatectl` для `user1` | `sudoers`, `user1-time` |
| **Раздел 6** | Сбор артефактов | Снятие скриншота терминала с табельным номером, сбор выводов утилит | `mephi-screenshot.png`, `history.out`, `*.out` |
