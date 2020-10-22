# console-commands
Консольные команды, которые могут быть полезны при повседневной работе

#Шапаргалка по использованию _Tmux_
[Исходный ресурс](https://habr.com/ru/post/327630/)

##Установка

+ CentOS (нужен подключенный репо EPEL) - `yum install tmux` 

+ Fedora - `dnf install tmux`

+ Ubuntu/Debian - `apt-get install tmux`


##Конфигурационные файлы

пользователя - `~/.tmux.conf`, системный - `/etc/tmux.conf`

С версии 2.1 для включения режима мыши (скролл, изменение размера панели, выбор панели и др.) нужно добавить в tmux.conf:

`set -g mouse on`


До версии 2.1

    set -g mouse-resize-pane on
    set -g mouse-select-pane on
    set -g mouse-select-window on
    set -g mode-mouse on


## Работа с Tmux

#####Старт

    tmux //без параметров будет создана сессия 0
    tmux new -s session1 //новая сессия session1. Название отображается снизу-слева в квадратных скобках в статус строке. Далее идет перечисление окон. Текущее окно помечается звездочкой.

#####Префикс (с него начинаются команды)
    <C-b> (CTRL + b)

#####Новое окно (нажать CTRL+b, затем нажать с)
    <C-b c>

#####Список окон
    <C-b w> // переключиться курсором вверх-вниз

#####Переключение
    <C-b n> // следующее окно
    <C-b p> // предыдущее окно
    <C-b 0> // переключиться на номер окна

#####Деление окна (на несколько панелей) горизонтально
    <C-b ">
    В консоли: tmux split-window -h

#####Деление окна вертикально
    <C-b %>
    В консоли: tmux split-window -v

#####Переход между панелей
    <C-b стрелки курсора> // либо режим мыши

#####Изменение размеров панелей
    <C-b c-стрелки> // либо режим мыши

#####Закрытие окон
    <C-b x> // нужно подтвердить y
    В консоли: exit

#####Отключение от сессии
    <C-b d>
    В консоли: tmux detach

#####Список сессий
    tmux ls

#####Подключиться к работающей сессии
    tmux attach //подключение к сессии, либо к единственной, либо последней созданной
    tmux attach -t session1 // подключение к сессии session1

#####Выбрать сессию
    <C-b s>

#####Завершение сессии
    tmux kill-session -t session1

#####Завершить все сессии
    tmux kill-server

#####Список поддерживаемых комманд
    tmux list-commands

#####Дополнительная информация
    man tmux

____
# Шапаргалка по использованию _Vim_
[Исходный ресурс]((http://highclouds.ru/2019/02/14/%D1%88%D0%BF%D0%B0%D1%80%D0%B3%D0%B0%D0%BB%D0%BA%D0%B0-%D0%BF%D0%BE-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B5-%D0%B2-vim/))
####Основы
    hjkl                            перемещение в разные стороны
    i                               режим вставки
    I                               добавление в начало строки
    a                               режим добавления
    A                               добавление в конец строки
    o                               добавить строку сразу за текущей
    O                               добавить строку перед текущей
    R                               писать поверх имеющегося текста
    u, :u[ndo]                      отмена предыдущего действия (undo)
    Ctrl+R, :red[o]                 отмена отмены предыдущего действия (redo)
    dd                              вырезать (удалить) строку
    cc                              удалить и начать редактирование
    yy                              копировать строку
    p                               вставить из буфера обмена
    <n>d                            удалить n+1 строку
    <n>y                            скопировать n+1 строку
    ESC                             перейти в режим просмотра
    DEL                             удалить следующий символ
    :<n>                            перейти на строку #n
    %                               перейти к парной скобке
    :e **/filename.c                редактировать файл (с поиском по имени)
    :w [fname]                      записать изменения
    :wa                             сохранить изменения во всех файлах
    :q                              выйти из редактора
    :q!                             выйти из редактора, не сохраняя изменения
    :color <name>                   выбор цветовой схемы. цветвые схемы:
                                    /usr/local/share/vim/vim72/colors/*.vim
    :pwd                            текущий каталог
    :cd [path]                      перейти в другой каталог
    :!команда                       выполнить команду – man, git, и так далее
                                    стрелочками веерх и вниз можно автодополнять
                                    команды и искать по истории
    Ctrl+p или Ctrl+n               автоматическое дополнение текста
                                    (в режиме редактирования)
    Ctrl+r, =, <expr>               вставить выражение, например 5*2 – 3
                                    (в режиме редактирования)
    Ctrl+u, Ctrl+d                  Page Up / Page Down
    Ctrl+y, Ctrl+e                  Перемотка вверх/вниз без движения курсора
    q:                              История команд
    .                               Повторение последней команды

####Подсветка синтаксиса
    :syntax on                      включить подсветку
    :syntax off                     выключить подсветку (по умолчанию)

####Перенос строк
    :set wrap                       разрешить word wrap (по умолчанию)
    :set nowrap                     запретить word wrap

####Печать
    :ha[rdcopy]                     распечатать документ
    :set printoptions=duplex:off    отключить двустороннюю печать

####Макросы
    qa                              записать макрос с именем a
    q                               в режиме записи макроса: закончить запись
    @a                              выполнить макрос с именем a
    @@                              повторить последний макрос

####Выделение
    v + hjkl                        выделение текста
    SHIFT + v                       выделить строку
    Ctrl + v                        выделение прямоугольника
    p                               вставить
    y                               копировать
    d                               удалить
    gu                              к нижнему регистру
    gU                              к верхнему регистру

####Отступы
    [#]>                            сдвинуть выделенное вправо
    [#]<                            сдвинуть выделенное влево
    [#]>>                           сдвинуть строку вправо
    [#]<<                           сдвинуть строку влево
    set tabstop=#                   для табуляции используется # пробелов
    set shiftwidth=#                в командах отступа используется # пробелов
    set [no]expandtab               заменять ли табуляцию на соответствующее
                                    число пробелов

####Поиск и замена в файле
    /Выражение                      поиск выражения в файле
    \cВыражение                     поиск без учета регистра
    n                               следующее совпадение
    N                               предыдущее совпадение
    :%s/foo/bar/gi                  замена строк, см http://eax.me/regular-expr/

####Поиск по всему проекту
    :vimgrep /EXPR/ **/*.c          поиск по регулярному выражению
    :copen                          показать все найденные места
    :close                          скрыть все найденные места
    :cn                             переход к следующему результату
    :cp                             переход к предыдущему результату

####Нумерация строк
    :set number                     включить нумерацию строк
    :set nonumber                   отключить нумерацию строк

####Работа с окнами
    :split                          горизонтальное разбиение
    :vsplit                         вертикальное разбиение
    
    Ctrl+W, затем
        с                           закрыть окно
        +-                          изменение высоты текущего окна
        <>                          изменение ширины текущего окна
        =                           установить равный размер окон
        hjkl или стрелочки          перемещение между окнами
        
        
#Linux

    du -hs * | sort -rh | head -5                       список самых больших файлов в директории
    
    cat /etc/passwd
    
    ifconfig
    nginx -t
    nginx -s reload
    
    find . -name php.ini
    lsof -i :80 пинг порта
    
    netstat -rn | grep "^0.0.0.0 " | cut -d " " -f10    поиск сети в вагранте

#Git

    ssh-keygen -t rsa -C "email" -b 4096
    
    git config --global user.name "name"
    git config --global user.email "email"
    
    git config core.autocrlf true
    
    git ls-remote origin
    git ls-remote .
    
    git checkout -b remote_branch origin/remote_branch      новая ветка из ремоута
    
    git remote set-url origin git@github.com:USERNAME/REPOSITORY.git    новый url адрес origin

#Composer

    composer update --ignore-platform-reqs  обновить композер без зависимостей в контейнере
    
    composer dump-autoload --optimize
