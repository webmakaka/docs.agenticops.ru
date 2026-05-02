# Исходники сайта [docs.agenticops.ru](https://docs.agenticops.ru)

Запустить docs.agenticops.ru на своем хосте с использованием docker контейнера:

    $ docker run -i -t -p 80:80 --name docs.agenticops.ru marley/docs.agenticops.ru

<br/>

### Как сервис

    # vi /etc/systemd/system/docs.agenticops.ru.service

вставить содержимое файла docs.agenticops.ru.service

    # systemctl enable docs.agenticops.ru.service
    # systemctl start  docs.agenticops.ru.service
    # systemctl status docs.agenticops.ru.service

http://localhost:4006

<br/>

### Вариант для внесения изменений

Инсталлируете docker и docker-compose, далее:

    $ cd ~
    $ mkdir -p docs.agenticops.ru && cd docs.agenticops.ru
    $ git clone --depth=1 https://github.com/webmakaka/docs.agenticops.ru.git .
    $ docker-compose up

<br/>

Остается в браузере подключиться к localhost:80
