# Linux-Commands-Cheat-Sheet
Linux Commands Cheat Sheet

## Основные команды терминала Linux

### Навигация

* **cd /.** - Переход в основной каталог
* **cd** - Переход в домашний каталог (переменная $HOME)
* **cd /root** - Переход в каталог /root
* **cd ..** - Переход на один уровень ниже
* **cd /root/.ssh** - Переход в скрытую папку .ssh

### Работа с файлами

* **ls** – Показывает файлы и каталоги в текущей папке
* **pwd** - Отображает текущий рабочий каталог
* **mkdir NewFolder** - Создает новый каталог с именем "NewFolder".
* **cat FileName** - Открывает файл FileName
* **nano FileName** - Открывает файл FileName (возможно потребуется утсновка nano)
* **rm NewFile** - Удаляет файл с именем "NewFile"
* **rm -f NewFile** - Принудительное удаление файла с именем "NewFile"
* **rm -r NewFolder** - Рекурсивно удаляет каталог с именем "NewFolder"
* **rm -rf NewFolder** - Принудительное удаление каталога с именем "NewFolder" рекурсивно
* **cp oldfile1 newfile2** - Копирует содержимое oldfile1 в newfile2
* **cp -r olddir1 newdir2** - Рекурсивно копирует каталог "olddir1" в "newdir2". Dir2 будет создан, если он не существует.
* **mv oldfile1 newfile2** - Переименовывает "oldfile1" в "newfile2".
* **ln -s /etc/log/file logfile** - Создает ярлык на файл
* **touch newfile** - Создает пустой файл с именем newfile
* **cat > newfile** - Помещает STDIN в newfile
* **more newfile** - Выводит содержимое newfile по частям
* **head newfile** - Выводит первые 10 строк файла newfile
* **tail newfile** - Вывод последних 10 строк newfile

### Пользователи

* **Id** - Подробная информация о пользователе (uid, gid и группа).
* **last** - Список информации о последних входах в систему, включая время, имя пользователя, ip-адрес и длительность сеанса.

### Права доступа к файлам/каталогам

* **chmod 777 /root/ssh** - устанавливает права rwx(чтение, запись, выполнение) на файл ssh для всех, кто имеет доступ к серверу (владелец, группа, другие)
* **chmod 755 /root/ssh** - Настраивает разрешения rwx для владельца и r_x для группы и других.
* **chmod 766 /root/ssh** - Устанавливает права rwx для владельца и rw для группы и других.
* **chown newuser newfile** - Меняет владельца newfile на newuser
* **chown newuser:newgroup newfile** - Изменяет владельца и группу-владельца для newfile на newuser и newgroup
* **chown newuser:newgroup newfolder** - Меняет владельца и группу-владельца каталога newfolder на newuser и newgroup
* **stat -c "%U %G" newfile** - отображает владельцев пользователей и групп newfile

### Поиск

* **grep searchargument newfile** - Поиск аргумента searchargument в newfile
* **grep -r searchargument newfolder** - рекурсивно просматривает все файлы в папке newfolder на наличие поискового аргумента
* **locate newfile** - Показывает все местоположения нового файла
* **find /etc/ -name "searchargument"** - Находит файлы с именем, начинающимся с searchargument, в каталоге /etc
* **find /etc/ -size +50000k** - Найти файлы размером более 50000k в каталоге /etc.

### Архивирование

* **tar -cf archive.tar newfile** - Создать архив 'archive.tar' из файла 'newfile'
* **tar -xf archive.tar** - Распаковать файл 'archive.tar'
* **tar -zcvf archive.tar.gz /var/log/** - Создать архив из каталога /var/log
* **gzip newfile**- Сжать новый файл (он будет иметь расширение .gz).


### Процессы

* **ps** - Выводит текущие запущенные процессы
* **ps aux | grep 'bash'** - Найти идентификатор процесса 'bash'
* **pmap -x 11** - Сопоставить процесс с PID = 11 в памяти процесса
* **top** - Показывает все запущенные процессы
* **kill pid** - Завершить процесс по pid
* **killall process** - Завершить все процессы с именем "process"
* **pkill process-name **- Послать сигнал процессу
* **bg** - Отправить приостановленный процесс на фоновое выполнение
* **fg** - Вывести запущенный процесс из фона
* **fg process** - Вывести процесс с именем "process" из фонового режима
* **lsof** – Показать списки файлов, которые используют процессы
* **renice 19 PID** - Устанавливает самый низкий приоритет процесса
* **pgrep bash** - найти идентификатор процесса bash
* **pstree** - Показывает древовидное представление процессов

### Использование диска

* **df -h** - Показывает свободное пространство на смонтированных разделах (в байтах)
* **df -i** - Показывает свободные inodes в файловой системе
* **fdisk -l** - Показывает информацию о диске, разделах и файловой системе
* **du -sh** - Отображает нераспределенное пространство на смонтированных разделах в MB, GB, TB
* **findmnt** - Отображает все точки монтирования
* **mount /dev/sdb1 /mnt** - Монтирует раздел 1 диска sdb в /mnt

### Сеть

* **ip addr show** - Показывает IP-адреса всех доступных сетевых интерфейсов
* **ip address add 192.168.0.1/24 dev eth0** - Присваивает адрес 192.168.0.1 интерфейсу eth0
* **ifconfig** - Показывает IP-адреса всех доступных сетевых интерфейсов
* **ping 192.168.0.1** - Отправляет запрос по протоколу ICMP для подключения к узлу 192.168.0.1.
* **whois domain** - Показывает информацию о доменном имени
* **dig domain** - Получает информацию DNS о домене
* **dig -x 192.168.0.1** - Инвертирует разрешение имен
* **host serverspace.us** - Резолвит адрес хоста
* **hostname -I** - Показывает локальные адреса
* **wget имя_файла(ссылка на файл)** - Загружает файл
* **netstat -pnltu** - Показывает все порты, прослушиваемые на хосте (требуется "apt-get install net-tools")

### Удаленное подключение

* **ssh root@host** - Подключение к удаленному хосту по ssh от имени root
* **ssh -p port_number user@host** - Подключается к удаленному хосту, если используется порт ssh, отличный от 22.
* **ssh host** - Использует соединение по умолчанию в качестве текущего пользователя
* **telnet host** - Использует соединение telnet (порт 23).
* **ssh -i ~/.ssh/custom_key_name SYSUSER@x.x.x.x** - Подключение к удаленному хосту c помощью примватного ключа
  
### Просмотр списка пользователей


* *cat /etc/passwd* - Ознакомиться со списком пользователей
* *lastlog* - посмотреть, когда пользователь последний раз входил в систему
