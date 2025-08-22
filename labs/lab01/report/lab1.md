# Лабораторная работа №1 Установка ОС Linux.

### Цель работы: 
Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

### Обучающиийся группы НКАбд-04-24 Осипов Никита Александрович




### После установки
Войдите в ОС под заданной вами при установке учётной записью.
Нажмите комбинацию Win+Enter для запуска терминала.
Переключитесь на роль супер-пользователя:
  sudo -i
### Обновления
Установите средства разработки:
sudo dnf -y group install development-tools
Обновить все пакеты



  sudo dnf -y update
### Повышение комфорта работы
Программы для удобства работы в консоли:
  sudo dnf -y install tmux mc
Другой вариант консоли:
  sudo dnf -y install kitty
Автоматическое обновление
При необходимости можно использовать автоматическое обновление.
### Установка программного обеспечения:
  sudo dnf -y install dnf-automatic
Задаёте необходимую конфигурацию в файле /etc/dnf/automatic.conf.
Запустите таймер:
  sudo systemctl enable --now dnf-automatic.timer
### Отключение SELinux
В данном курсе мы не будем рассматривать работу с системой безопасности SELinux.
Поэтому отключим его.
В файле /etc/selinux/config замените значение
  SELINUX=enforcing
на значение
  SELINUX=permissive
Перегрузите виртуальную машину:
  sudo systemctl reboot
### Настройка раскладки клавиатуры
Войдите в ОС под заданной вами при установке учётной записью.
Нажмите комбинацию Win+Enter для запуска терминала.
Запустите терминальный мультиплексор tmux:
  tmux
Создайте конфигурационный файл ~/.config/sway/config.d/95-system-keyboard-config.conf:
  mkdir -p ~/.config/sway
  touch ~/.config/sway/config.d/95-system-keyboard-config.conf
Отредактируйте конфигурационный файл ~/.config/sway/config.d/95-system-keyboard-config.conf:
  exec_always /usr/libexec/sway-systemd/locale1-xkb-config --oneshot
Переключитесь на роль супер-пользователя:
  sudo -i
Отредактируйте конфигурационный файл /etc/X11/xorg.conf.d/00-keyboard.conf:
Section "InputClass"
            Identifier "system-keyboard"
            MatchIsKeyboard "on"
            Option "XkbLayout" "us,ru"
            Option "XkbVariant" ",winkeys"
            Option "XkbOptions" "grp:rctrl_toggle,compose:ralt,terminate:ctrl_alt_bksp"
EndSection
Для этого можно использовать файловый менеджер mc и его встроенный редактор.
Перегрузите виртуальную машину:
   sudo systemctl reboot

#### Установка программного обеспечения для создания документации
Нажмите комбинацию Win+Enter для запуска терминала.
Запустите терминальный мультиплексор tmux:
  tmux
Переключитесь на роль супер-пользователя:
    sudo -i
### Работа с языком разметки Markdown
Средство pandoc для работы с языком разметки Markdown.
Установка с помощью менеджера пакетов:
sudo dnf -y install pandoc
Для работы с перекрёстными ссылками мы используем пакет pandoc-crossref.
Пакет pandoc-crossref в стандартном репозитории отсутствует.
Придётся ставить вручную, скачав с сайта https://github.com/lierdakil/pandoc-crossref.
При установке pandoc-crossref следует обращать внимание, для какой версии pandoc он скомпилён.
Лучше установить pandoc и pandoc-crossref вручную.
Скачайте необходимую версию pandoc-crossref (https://github.com/lierdakil/pandoc-crossref/releases).
Посмотрите, для какой версии откомпилён pandoc-crossref.
Скачайте соответствующую версию pandoc (https://github.com/jgm/pandoc/releases).
Распакуйте архивы.
Обе программы собраны в виде статически-линкованных бинарных файлов
Поместите их в каталог /usr/local/bin.
### texlive
Установим дистрибутив TeXlive:
  sudo dnf -y install texlive-scheme-full
## Заключение
Я приобрел практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов
