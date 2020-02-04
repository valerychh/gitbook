# Git

### Установка

Устанавливаем Git:

```bash
apt install git
```

### Подготавливаем рабочее окружение

Создадим папку и перейдём в неё:

```bash
mkdir git && cd git
```

Установим имя и адрес электронной почты:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
```

> Копируем или создаём файлы и директории, которые вам необходимо отправить на github.

Инициализируем репозиторий:

```bash
git init
```

Добавляем файлы и директории, в которых необходимо отслеживать изменения:

```bash
git add 1.txt
```

Создадим файл **.gitignore** и пропишем туда файлы и директории, которые **git** будет игнорировать:

```bash
touch .gitignore
```

```bash
$ vim .gitignore
2.txt
```

Проверим статус:

```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   .gitignore
        new file:   1.txt
```

Файл **2.txt** игнорируется. Теперь необходимо закоммитить файлы **1.txt** и **.gitignore**:

```bash
$ git commit -m "test"
[master (root-commit) 747af15] test
 2 files changed, 1 insertion(+)
 create mode 100644 .gitignore
 create mode 100644 1.txt
```

Проверим статус:

```bash
$ git status
On branch master
nothing to commit, working tree clean
```

Изменим содержимое файла **1.txt**:

```bash
$ vim 1.txt
test
```

Проверим статус:

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   1.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Теперь у нас есть возможность снова добавить файл в репозиторий выполнив команду **git add**, либо отменить изменения командой **git checkout**

```bash
$ git ckeckout
$ git status
On branch master
nothing to commit, working tree clean
```

### Добавление репозитория на github

> Регистрируемся на github и создаём репозиторий

Добавляем удалённый репозиторий:

```bash
git remote add origin https://github.com/valerychh/git.git
```

И наконец пушим локальный репозиторий в **github:**

```bash
git push -u origin master
```

> Вводим логин и пароль от учётной записи на github

```bash
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 255 bytes | 255.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To https://github.com/valerychh/git.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

