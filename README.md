# homeworkLinux

============================================================================================

Задание 1

Назовите по два DEB и RPM дистрибутива Linux

DEB: SteamOS, Raspberry Pi OS

RPM: Red Hat, CentOS

============================================================================================

Задание 2

Объясните, что делает команда:
ps aux | grep root | wc -l >> root
Ответ напишите в свободной форме

Список исполняющихся в данный момент процессов , в которых глобаный поиск greb нашёл совпадение root и построчная запись количества процессов в файл root

============================================================================================

Задание 3

Напишите команду, которая вывод все запущенные процессы пользователя root в файл "user_root_ps"

ps aux | grep root | tee user_root_ps

============================================================================================

Задание 4

В лекции была упомянута одна команда для получения информации о нагрузке на компьютер и в частности на ОЗУ.
Ее вывод выглядит вот так:
Как называется эта команда? Что такое si и so в примере на картинке?
Приведите ответ в свободной форме

vmstat - команда которая выводит такие данные. si, so - swap input, swap output
si (swap in) – количество блоков в секунду, которое система считывает из раздела или файла swap в память;
so (swap out) – и наоборот, количество блоков в секунду, которое система перемещает из памяти в swap.

============================================================================================

Задание 5

Приведите 3 команды, которые выведут на экран следующее:

Архитектуру ПК
Модель процессора
Количество памяти, которая уже не используется процессами, но еще остается в памяти(ключевое слово - inactive).
Примечание: при выполнении задания предполагается использование конструкции "{команда} | grep {параметр для фильтрации вывода}" в каталоге /proc

arch   
cat /proc/cpuinfo | grep 'model name'
???
============================================================================================

Задание 6

Создайте скрин вывода команды free -h -t
Создайте swap-файл размером 512 Мб в корне диска / с именем swapfile
Добавьте настройку чтобы swap-файл подключался автоматически при перезагрузке виртуальной машины (подсказка: необходимо внести изменения в файл /etc/fstab)
Создайте скрин вывода команды free -h -t
Создайте скрин вывода команды swapon -s
В качестве ответа приложите созданные скриншоты

![image](https://user-images.githubusercontent.com/98020376/166228494-29ca7365-236a-4b0c-94d5-59e4aeb0676c.png)

![image](https://user-images.githubusercontent.com/98020376/166229697-b9e4b414-d7c4-4d89-bce3-03e5e2f7546c.png)

![image](https://user-images.githubusercontent.com/98020376/166229783-89b35b62-46b2-4bc1-b431-b29a30cf565d.png)

============================================================================================

Задание 7

Найдите информацию про tmpfs.
Расскажите в свободной форме, в каких случаях уместно использовать эту технологию.
Создайте диск tmpfs (размер не более 512Мб), смонтируйте его в директорию /mytmpfs
В качестве ответа приведите скриншот вывода команды df- h до и после монтирования диска tmpfs.

![image](https://user-images.githubusercontent.com/98020376/166229938-bb9f3e5d-3052-4e48-9852-2991819035a9.png)

![image](https://user-images.githubusercontent.com/98020376/166230635-d81aa238-d5f1-47b0-8984-0debbd42deda.png)

tmpfs временное хранилище данных. После перезагрузки все данные, содержащиеся в Tmpfs, будут утеряны.

============================================================================================

Задание 8

Влияет ли количество операций ввода-вывода HDD диска на параметр load average?
Приведите развернутый ответ в свободной форме

load average выводит загруженность системы в целом, а быстродействие системы зависит на прямую от процессора, но от скорости чтения и записи на жёсткий диск быстродействие системы тоже зависит

============================================================================================

Задание 9

Чем hardlink отличается от softlink?
Приведите ответ в свободной форме

hardlink – жёсткая ссылка, является тем же файлом, на который ссылается.
softlink – мягкая ссылка, использует различные номера inod. Их можно использовать, если исходный файл был удален.

============================================================================================

Задание 10

Как посмотреть количество inodes?
Приведите ответ в свободной форме

Чтобы посмотреть статистику по inod (доступное количество, использованное количество, а также процент использования), нужно ввести команду
df -i

============================================================================================

Задание 11

При каких событиях выполнение процесса переходит в режим ядра в Linux?
Приведите ответ в свободной форме

Предположим, что система выполняет множество процессов, которые одновременно никак не могут поместиться в оперативной памяти, и программа подкачки выгружает один процесс, чтобы освободить место для другого процесса, находящегося в состоянии "готов к запуску, но выгружен". Первый процесс, выгруженный из оперативной памяти, переходит в то же состояние. Когда программа подкачки выбирает наиболее подходящий процесс для загрузки в оперативную память, этот процесс переходит в состояние "готовности к запуску в памяти". Планировщик выбирает процесс для исполнения и он переходит в состояние "выполнения в режиме ядра". Когда процесс завершается, он исполняет системную функцию exit, последовательно переходя в состояния "выполнения в режиме ядра" и, наконец, в состояние "прекращения существования".

============================================================================================

Задание 12

Найдите имя автора модуля libcrc32c при помощи утилиты modinfo
В качестве ответа приложите скриншот вывода команды

modinfo libcrc32c -a

![image](https://user-images.githubusercontent.com/98020376/166234194-4a9b74c5-2055-4851-9fda-7a981ee9befb.png)

============================================================================================

Задание 13

Используя утилиту strace выясните какой системный вызов использует команда cd
Примечание: она не является внешним файлом, но для наших целей использовать: strace -c bash 'cd /tmp'
В качестве ответа напишите название системного вызова или нескольких вызовов

![image](https://user-images.githubusercontent.com/98020376/166234508-1082f8b3-c924-4a9e-bbce-f505fa47ce88.png)

============================================================================================

Задание 14

Существует такой вид виртуализации как контейнеризация: контейнеры создаются на уровне ОС и работают в изолированных пространствах.
Вопрос: что произойдет, если в хостовой ОС установлен upstart или systemV, а в запущенном контейнере - systemd?
Приведите ответ в свободной форме со своим комментарием.

???















