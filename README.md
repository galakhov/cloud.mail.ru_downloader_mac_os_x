# Cloud&#64;Mail.Ru Downloader

### Installation on Mac OS X

- follow any tutorial to install [php 7](https://medium.com/@crmcmullen/how-to-install-php-on-macos-10-13-high-sierra-and-10-14-mojave-using-homebrew-and-pecl-ef2276db3d62) for your version of Mac OS X
- If you got "Cannot find libs..." errors when installing php, run the command below and try again:\n
  `xcode-select --install`
- test your php version by entering this line in the terminal (the version should be between _5.x.x and 7.2.x_):\n
  `php -v`
- check whether openssl for php in installed and enabled by running the following line in the terminal and looking for OpenSSL:\n`php -i | grep enabled`
- if you can't find the OpenSSL Support in the above list, install it by running or following some of the [tutorials](https://medium.com/this-old-code/installing-php-7-2-bc779b23dce8):\n
  `brew install openssl`
- download, install and configure [Progressive Downloader](https://www.macpsd.net) or any other similar downloader for Mac OS X

### Running on Mac OS X

- paste one or more links to the mail.ru cloud into the _links.txt_ file
- run the script to get the _direct links_ to all the files from the cloud as a console output:\n`php cloud.mail.ru_downloader.php`
- paste the retrieved _direct links_ into the downloads folder you've chosen in the _Progressive Downloader_

### Installation for Windows

- Для работы скрипта нужно установить php на компьютер, например отсюда http://windows.php.net/download/ (если уже установлен какой-нибудь Веб-сервер, например, [Denwer](http://www.denwer.ru/) или [OpenServer](http://open-server.ru/), то php от него тоже подойдет).
- Скрипт консольный, написан на PHP, поэтому работает в PHP версий _5.x.x-7.2.x_.
- Для скачивания можно использовать любой Download Manager. В примере ниже используется консольный загрузчик [Aria2c](https://aria2.github.io/).
- Скрипт умеет корректно обрабатывать папки в облаке любой вложенности.
- Поддерживается докачка файлов.

## Running on Windows

- Скачать релиз скрипта, в который уже включена минимальная версия php
- В файл `links.txt` записать публичные ссылки на скачивание с облака вида https://cloud.mail.ru/public/9bFs/gVzxjU5uC по одной на строку.
- Запустить `start.bat`
- Скрипт сформирует файл с прямыми ссылками на скачивание `input.txt`.
- После чего запустится Aria2c Downloader, который скачает файлы из `input.txt`.
- Остаётся наблюдать за закачкой и ждать её завершения. Скачанные файлы окажутся в папке `downloads`.

[![Скрипт за работой](image.png)](image.png)

## Настройка PHP, если используете уже установленный

В `php.ini` должно быть активировано openssl-расширение:

> extension_dir="ext"\
> extension=php_openssl.dll

### Видео-пример:

[![Cloud.MailRu.Downloader Video example](https://img.youtube.com/vi/WnJyXEdEqfI/0.jpg)](https://www.youtube.com/watch?v=WnJyXEdEqfI)

### If you want to emulate [WebDAV](https://github.com/yar229/WebDavMailRuCloud) of cloud.mail.ru

- `brew install mono # (you need to have _homebrew_ already installed)`
- alternatively you can download and install mono following [these instructions](https://www.mono-project.com/docs/about-mono/supported-platforms/macos/)
- then just start any exe file as it's described [here](https://github.com/yar229/WebDavMailRuCloud#mac-os-x):
  `mono wdmrc.exe -p 7000`

#### Thanks to [Geograph-us](https://github.com/Geograph-us/Cloud-Mail.Ru-Downloader)
