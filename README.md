## Полезные скрипты для RouterOS MikroTik v.6 (для версии 7 не подойдет)
---
### Список и описание назначения скриптов 
1. **`active_users_counters`** - Скрипт подсчитывает количество авторизированных (активных) пользователей HotSpot MikroTik и дергает те или иные правила файрвола
2. **`check_sqldb_size`** - Скрипт считает размер файла базы данных sqldb  Usermanager MikroTik RouterOS и если размер больше установленного значения то запускает скрипт database_maintenance.                        см. описание скрипта database_maintenance.
3. **`database_maintance`** - Скрипт "сжатия" базы данных sqldb Usermanager MikroTik RouterOS. 
   * Удаляет сессии пользователей Usermanager
   * Удаляет лог базы данных sqldb
   * Перестраивает базу данных
   * `Уменьшение размера  базы данных sqldb происходит за счет вышеописанных действий
скрипт выключает в шедулере некоторые скрипты, жмет базу, включает в шедулере скрипты которые выключил.
Доработайте скрипт под свои задачи если необходимо`
4. **`reset_counters_monthly`** - Скрипт сброса счетчиков трафика пользователей HotSpot MikroTik RouterOS.
   * Скрипт ищет пользователей HotSpot где username в пределах 000000 - 999999
   * Сбрасывает счетчики трафика download/upload
   * Удаляет добавленный профиль с лимитом трафика
   * Добавляет профиль с лимитом трафика
5. **`reset_counters_weekly`** - Скрипт сброса счетчиков трафика пользователей HotSpot MikroTik RouterOS.
   * `Скрипт ищет пользователей HotSpot MikroTik в usermanager где в описании пользователя в поле location установлено значение, если например нашему пользователю добавлено значение поля location=3072 то происходит следующее`
   * Сбрасывает счетчики трафика download/upload у пользователей где в поле location установлено значение 3072
   * Удаляет добавленный профиль с лимитом трафика у пользователей где в поле location установлено значение 3072
   * Добавляет профиль с лимитом трафика у пользователей где в поле location установлено значение 3072
   * `Создайте свой profile с лимитом трафика и укажите его название в скрипте. По логике этого скрипта должен быть profile с названием 3072Mb и присвоенным лимитом трафика равным 3Gb`
6. **`stop_overload_traffic_weekly_1536`** - Скрипт лечит баг HotSpot MikroTik Usermanager который позваляет перебирать установленный лимит трафика во время активной сессии.
   * Скрипт мониторит счетчики пользователей по download и как только download становиться больше установленного значения активная сессия завершается, profile с лимитом трафика по сути израсходованным удаляется .
7. **`remove_all_authorized_users`** - Скрипт завершения всех активных сессии пользователей HotSpot MikroTik
8. **`remove_conflict_dhcp_leases`** - Скрипт удаления конфликтных leases в DHCP MikroTik
9. **`remove_hosts_anotherip`** - Скрипт удаления ip адресов из Hosts в HotSpot  MikroTik не входящих в pool DHCP
