## Сессионный проект по курсу «Операционные системы семейства Unix»

Студент: Арыкова Ольга

Зачетная книжка: М368688

Среда: Fedora Workstation, VirtualBox

## Этапы выполнения задания
### Управление сетью
- Определено имя сетевого интерфейса с помощью nmcli connection show
- Настроен статический IP для подключения "Проводное подключение 1": IP-адрес: 192.168.1.100/24, Шлюз: 192.168.1.1, DNS: 8.8.8.8
- Установлено имя хоста: mephi-2026.domain.local через hostnamectl
### Управление программным обеспечением
- Установлены через dnf install пакеты: nginx, tcpdump, libcap-ng-utils
- Скачен пакет tcpdump через dnf download
- Установлен пакет tcpdump  через -Uvh для обновления, т.к. ранее был установлен
### Управление файловыми системами и сервисами
- Создан раздел на /dev/sdb через fdisk
- Отформатирован раздел /dev/sdb1 в ext4 с меткой MEPHI_DATA
- Автомонтирование в  /data/mephi-web через /etc/fstab по UUID
### Управление доступом
- Создан пользователь mephi-admin, пароль P@ssw0rd2026
- Создана группу mephi-devs, добавлен пользователь mephi-admin в группу
- Изменен владелец /data/mephi-web на mephi-admin:mephi-devs
- Установлены права 2775 (setgid бит)
### Аутентификация и итоговая проверка
- Создан файл /etc/ssh/denied_users с содержимым "root", вход для "root" заблокирован через PAM (listfile.so)
- Под пользователем mephi-admin создан файл /data/mephi-web/index.html с содержимым: Hello from Student: 368688
- Проверка через curl http://localhost - Hello from Student: 368688
- Проверка через curl http://192.168.1.100 - Hello from Student: 368688
- Проверка после перезагрузки - система настроена согласно требованиям

### Артефакты
| Файл                              | Раздел | Что проверяется                          |
|-----------------------------------|--------|------------------------------------------|
| project_history.txt               | Все    | История всех команд                      |
| network_check.txt                 | 1.2    | Результаты ping                          |
| nginx_recent_logs.txt             | 3.2    | Логи nginx                               |
| fstab.txt                         | 3.1    | Автомонтирование                         |
| selinux_status.txt                | 4.2    | Режим SELinux                            |
| file_contexts.txt                 | 4.2    | Контекст SELinux                         |
| tcpdump_capabilities.txt          | 4.2    | Настройка capabilities                   |
| permissions.txt                   | 4.1    | Права и владелец                         |
| users_groups.txt                  | 4.1    | Пользователи и группы                    |
| index.html                        | 5.2    | Web-страница                             |
| curl_output.txt                   | 5.2    | Результат тестирования                   |
| mephi-nginx-screenshot.png        | 5.2    | Визуальное подтверждение                 |
| tcpdump.rpm                       | 2.2    | Подтверждение скачивания RPM             |
| mephi-nginx-screenshot_reboot.png | -      | Проверка после перезагрузки              |
