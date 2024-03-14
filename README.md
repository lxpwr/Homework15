Логирование 

Создал две виртуальные машины из Vagrantfile. На обеих включил синхронизацию времени по ntp согласно инструкции командой

timedatectl set-ntp true

Зашел на машину log и там настроил rsyslog согласно методички, раскомментировав и добававив строки в файл /etc/rsyslog.conf 

После этого, перезапустил сервис:

systemctl restart rsyslog


На машине web согласно методички, сделал конфигурирование файла nginx для настройки удаленного сбора логов доступа и ошибок, после чего перезапустил сервис:

systemctl restart nginx

И проверил его работу - стартовая страница открылась

На машине log появился файл /var/log/rsyslog/web/nginx_access.log  с логами доступа

Я перенес файл начальной страницы  на web в другой каталог и еще раз открыл страницу сайта в браузере - теперь появился и файл /var/log/rsyslog/web/nginx_error.log 

Готово!