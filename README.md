
# Как скачать редакцию Bitrix автоматически и собрать любой PHP-проект в 1 файл без использования PHAR

*Для сборки поддерживается не только лишь Bitrix, но и любые современные PHP-фреймворки или проекты использующие автозагрузку классов.*
*По аналогии с тулингом dotnet - команды запускаются в рабочей директории проекта.*

## Установка

`git clone https://github.com/6umpukc-uHKBu3umop/6umpukc.git && cd 6umpukc && chmod +x bx && ./bx self-install`

для Windows запускать в командной строке Git Bash https://gitforwindows.org/ или http://www.msys2.org/

## Скачать скрипт инсталятора bitrixsetup.php

`bx fetch setup`

## Стандартные редакции

`bx fetch` или `bx fetch start`

`bx fetch business`

`bx fetch crm`

## Минимизированное ядро

Часть модулей/компонентов убрана, при этом будет рабочая Bitrix панель и шаблоны.

Данная сборка после установки уместится в лимиты на количество файлов бесплатного хостинга Beget - https://beget.com/ru/free-hosting

`bx fetch core`

## "Микроядро"

Оставлены только классы модулей - чтобы пилить свой микрофреймворк, переиспользуя кодовую базу Bitrix.

`bx fetch micro`

### Cборка на основе полученного списка классов и файлов

Для сопоставления классов и файлов используются данные автозагрузки composer

```
composer -o dump-autoload
bx build
```
или `bx rebuild`

Создать одно-файловое приложение
```
composer -o dump-autoload
bx build onefile
```
или `bx rebuild onefile`

### Пример структуры проекта

https://github.com/rivetweb/6umpukc/tree/master/example-project

В папке проекта должен существовать файл `vendor/.deps.log` - который содержит список полных названий классов, достаточный для запуска приложения.

```
Bitrix\Main\Application
Bitrix\Main\ArgumentException
Bitrix\Main\ArgumentNullException
Bitrix\Main\Config\Configuration
Bitrix\Main\Context
HelloWorld\App
HelloWorld\Config
HelloWorld\GreetingsService
```

`vendor/.replaces.log` - набор строк для замены кода
