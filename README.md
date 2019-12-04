# Cloud.Mail.Ru Downloader

### Installation on macOS

- follow any of tutorials to install php 7 with OpenSSL support enabled ([like this one](https://medium.com/@crmcmullen/how-to-install-php-on-macos-10-13-high-sierra-and-10-14-mojave-using-homebrew-and-pecl-ef2276db3d62)) for your version of macOS
- (If you get "Cannot find libs..." errors during the php installation via terminal, run the command below and try again:
  `xcode-select --install`)
- test your php version by entering this line in the terminal (the version should be between _5.x.x and 7.2.x_):
  ```console
  php -v
  ```
- check whether OpenSSL for php is installed and enabled by running the following line in the terminal and looking for OpenSSL in the displayed list:
  ```console
  php -i | grep enabled
  ```
- (if you can't find the 'OpenSSL Support' in the list displayed after running the previous command, install it by running the next command or by following any of the [tutorials](https://medium.com/this-old-code/installing-php-7-2-bc779b23dce8):
  `brew install openssl`)
- download & install [aria2](https://github.com/aria2/aria2/releases/) (by default the dowloader tries to start the `aria2c` from the bash that's why the installation of the macOS version of aria2 is the prerequisite: [aria2-\*-osx-darwin.dmg](https://github.com/aria2/aria2/releases/). You can, however, use [Progressive Downloader](https://www.macpsd.net) or any other similar macOS' downloader.

### Running on macOS

- `open links.txt`
- paste one or more mail.ru cloud links into the _links.txt_ file (the links should look like `https://cloud.mail.ru/public/9bFs/gVzxjU5uC` and be placed one per line)
- run the script to first read the _direct links_ to all of the files from the cloud and display them as the console output:
  ```console
  php cloud.mail.ru_downloader.php
  ```
- the script appends the _direct links_ into the `input.txt` file
- the `aria2c` downloader will then start to download files from the `input.txt`
- (alternatively you can paste the retrieved _direct links_ into the _Progressive Downloader_)

### Installation for Windows

- Для работы скрипта нужно установить php на компьютер, например отсюда http://windows.php.net/download/ (если уже установлен какой-нибудь веб-сервер, например, [Denwer](http://www.denwer.ru/) или [OpenServer](http://open-server.ru/), то php от него тоже подойдет).
- Скрипт консольный, написан на PHP, поэтому работает в PHP версий _5.x.x-7.2.x_.
- [Скачать](https://github.com/galakhov/cloud.mail.ru_downloader_mac_os_x/archive/master.zip) и разархивировать либо склонировать с помощью команды (для её запуска нужен [git](https://git-scm.com/download/win)):

```console
git clone https://github.com/galakhov/cloud.mail.ru_downloader_mac_os_x.git cloud.mail.ru_downloader
```

- Для скачивания можно использовать любой Download Manager. В примере ниже используется консольный загрузчик [Aria2c](https://aria2.github.io/).
- Скрипт умеет корректно обрабатывать папки в облаке любой вложенности + поддерживается докачка файлов.

### Running on Windows

- Открыть файл `links.txt` и сохранить в него публичные ссылки для скачивания с облака вида `https://cloud.mail.ru/public/9bFs/gVzxjU5uC` по одной на строку.
- Скрипт запустить с помощью команды: `php cloud.mail.ru_downloader.php`
- Скрипт сформирует файл с прямыми ссылками на скачивание `input.txt`.
- После чего запустится Aria2c Downloader, который начнёт скачивать файлы из `input.txt`.
- Остаётся наблюдать за закачкой и ждать её завершения. Скачанные файлы окажутся в папке `./downloads`.

[![Скрипт за работой](image.png)](image.png)

### Настройка PHP, если используете уже установленный

В `php.ini` должно быть активировано openssl-расширение:

> extension_dir="ext"\
> extension=php_openssl.dll

### Видео-пример:

[![Cloud.MailRu.Downloader Video example](https://img.youtube.com/vi/WnJyXEdEqfI/0.jpg)](https://www.youtube.com/watch?v=WnJyXEdEqfI)

### If you want to emulate [WebDAV](https://github.com/yar229/WebDavMailRuCloud) of cloud.mail.ru on macOS

- you'll need to install `mono` first:

```console
brew install mono # (you need to have homebrew installed already)
```

- alternatively you can download and install `mono` following [these instructions](https://www.mono-project.com/docs/about-mono/supported-platforms/macos/)
- then just start any exe file as described [here](https://github.com/yar229/WebDavMailRuCloud#mac-os-x) by entering any open port (like '7000' in this example):

```console
mono wdmrc.exe -p 7000
```

#### Thanks to [Geograph-us](https://github.com/Geograph-us/Cloud-Mail.Ru-Downloader) for the initial version and the installation instructions for Windows
