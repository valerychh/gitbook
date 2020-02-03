---
description: Установка и настройка Gitbook
---

# Gitbook

Устанавливаем таймзону:

```bash
sudo dpkg-reconfigure tzdata
```

Обновляем убунту:

```bash
sudo apt update && sudo apt upgrade -y
```

Устанавливаем пакеты:

```bash
sudo apt install -y curl wget vim git unzip socat bash-completion apt-transport-https build-essential
```

Устанавливаем Node.js:

```bash
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt install -y nodejs 
```

Проверяем версии:

```bash
node -v && npm -v
# v10.15.1
# 6.4.1
```

Обновим npm:

```bash
sudo npm install -g npm@latest
```

Проверим версию:

```bash
npm -v# 6.8.0
```

Далее создаем директорию:

```bash
sudo mkdir /var/www/gitbook
cd /var/www/gitbook
```

Сразу же сюда клонируем нашу репу из гитхаба, моя будет создана в папке "gitbook":

```bash
git clone https://github.com/valerychh/gitbook.git
```

Теперь установим гитбук глобально:

```bash
npm install gitbook-cli -g
```

И установим его в текущую папку:

```bash
gitbook init
```

Теперь в текущей папке у нас будет создан гитбук и мы его даже сможем запустить. Но пока не будем этого делать, нам нужно его немного настроить.

Создаем файл book.json:

```bash
vim book.json
```

Со следующим содержимым:

```bash
{
        "root": "./docs",
        "title": "dpkb",
        "author": "valerych",
        "description": "gitbook",
        "plugins": [
                "folding-chapters-2",
                "theme-code",
                "-sharing"
        ],
        "pluginsConfig": {
                "theme-default": {
                        "showLevel": false
                }
        }
}
```

Там мы указали некоторые модули, которые мы будем использовать. Теперь их нужно установить командой:

```bash
gitbook install
```

Переместим файлы README.md и SUMMARY.md:

```bash
mv README.md SUMMARY.md /gitbook
```

Практически все готово. Теперь если мы запустим нашу базу знаний то там будет только один файл. И это потому, что до запуска нам нужно сгенерировать файл SUMMARY. Мы, конечно, можем это делать вручную. Но когда у нас десятки или сотни файлов это делать тяжеловато.

На помощь нам приходит плагин:

```bash
npm install -g gitbook-summary
```

Теперь запускаем его:

```bash
book sm g
```

Все. Файл сгенерирован. Теперь можем запускать нашу базу:

```bash
gitbook serve
```

Задать порт, по которому будет доступен наш gitbook-сервер, можно так:

```bash
gitbook --port 80 serve
```

