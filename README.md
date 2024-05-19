[![Build Status](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06.svg?token=QmQqzGNVkZy8A7N9cEfZ&branch=master)](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06)

# Лабораторная работа 9. ИУ8-24 Бачулашвили София
## tp-lab09
# Как видете с первой попытки не получилось...
```sh
❯ rm -rf lab09     
```

# Но как говорил (пел) кот Леопольд: 😺😸
## Если получается всё наперекос,
## Не впадай в отчаянье и не вешай нос! 
## В самом трудном случае хвост держи трубой — 🦚
## И тогда получится всё само собой!

# /* Отчет состоит из команд, которые выполнены вчера и сегодня */

```sh
❯ export GITHUB_TOKEN=ssdg3435jho9485u9u459ufihi880359uihdsk

❯ export GITHUB_USERNAME=SofiaBachulashvili

❯ export PACKAGE_MANAGER=dnf

❯ export GPG_PACKAGE_NAME=gnupg
```

```sh
❯ sudo ${PACKAGE_MANAGER} install xclip
[sudo] пароль для sofia: 
Fedora 40 - x86_64 - Updates                                                             68 kB/s |  23 kB     00:00    
Fedora 40 - x86_64 - Updates                                                            930 kB/s | 2.7 MB     00:02    
Последняя проверка окончания срока действия метаданных: 0:00:02 назад, Вс 19 мая 2024 16:01:04.
Пакет xclip-0.13-21.git11cba61.fc40.x86_64 уже установлен.
Зависимости разрешены.
Нет действий для выполнения.
Выполнено!
```

# Это выполнено вчера
```sh
❯ sudo ${PACKAGE_MANAGER} install xclip                                                                           
Fedora 40 - x86_64 - Updates                                                             23 kB/s |  22 kB     00:00    
Fedora 40 - x86_64 - Updates                                                            2.1 MB/s | 2.7 MB     00:01    
Последняя проверка окончания срока действия метаданных: 0:00:03 назад, Сб 18 мая 2024 22:01:40.
Зависимости разрешены.
========================================================================================================================
 Пакет                  Архитектура             Версия                                    Репозиторий             Размер
========================================================================================================================
Установка:
 xclip                  x86_64                  0.13-21.git11cba61.fc40                   fedora                   37 k

Результат транзакции
========================================================================================================================
Установка  1 Пакет

Объем загрузки: 37 k
Объем изменений: 62 k
Все правильно? [Д/н]: 
Загрузка пакетов:
xclip-0.13-21.git11cba61.fc40.x86_64.rpm                                                385 kB/s |  37 kB     00:00    
------------------------------------------------------------------------------------------------------------------------
Общий размер                                                                             37 kB/s |  37 kB     00:00     
Проверка транзакции
Проверка транзакции успешно завершена.
Идет проверка транзакции
Тест транзакции проведен успешно.
Выполнение транзакции
  Подготовка       :                                                                                                1/1 
  Установка        : xclip-0.13-21.git11cba61.fc40.x86_64                                                           1/1 
  Запуск скриптлета: xclip-0.13-21.git11cba61.fc40.x86_64                                                           1/1 

Установлен:
  xclip-0.13-21.git11cba61.fc40.x86_64                                                                                  

Выполнено!
```
# Вот (конец вчерашнего)

```sh
❯ alias gsed=sed

❯ alias pbcopy='xclip -selection clipboard'

❯ alias pbpaste='xclip -selection clipboard -o'

❯ cd ${GITHUB_USERNAME}/workspace

❯ pushd .  
~/SofiaBachulashvili/workspace

❯ source scripts/activate
```

# Это выполнено вчера
```sh
❯ sudo ${PACKAGE_MANAGER} install go                      
[sudo] пароль для sofia: 
Последняя проверка окончания срока действия метаданных: 0:08:20 назад, Сб 18 мая 2024 22:01:40.
Зависимости разрешены.
========================================================================================================================
 Пакет                           Архитектура            Версия                            Репозиторий             Размер
========================================================================================================================
Установка:
 golang                          x86_64                 1.22.3-1.fc40                     updates                 666 k
Установка зависимостей:
 go-filesystem                   x86_64                 3.5.0-1.fc40                      fedora                  8.8 k
 golang-bin                      x86_64                 1.22.3-1.fc40                     updates                  26 M
 golang-src                      noarch                 1.22.3-1.fc40                     updates                  12 M
 libserf                         x86_64                 1.3.10-5.fc40                     fedora                   59 k
 re2                             x86_64                 1:20220601-5.fc40                 fedora                  206 k
 subversion-libs                 x86_64                 1.14.3-5.fc40                     fedora                  1.5 M
 utf8proc                        x86_64                 2.7.0-7.fc40                      fedora                   80 k
Установка слабых зависимостей:
 mercurial                       x86_64                 6.7.3-1.fc40                      updates                 6.4 M
 python3-fb-re2                  x86_64                 1.0.7-15.fc40                     fedora                   23 k
 subversion                      x86_64                 1.14.3-5.fc40                     fedora                  1.0 M

Результат транзакции
========================================================================================================================
Установка  11 Пакетов

Объем загрузки: 48 M
Объем изменений: 225 M
Все правильно? [Д/н]: 
Загрузка пакетов:
(1/11): libserf-1.3.10-5.fc40.x86_64.rpm                                                620 kB/s |  59 kB     00:00    
(2/11): python3-fb-re2-1.0.7-15.fc40.x86_64.rpm                                         221 kB/s |  23 kB     00:00    
(3/11): re2-20220601-5.fc40.x86_64.rpm                                                  1.5 MB/s | 206 kB     00:00    
(4/11): go-filesystem-3.5.0-1.fc40.x86_64.rpm                                            62 kB/s | 8.8 kB     00:00    
(5/11): utf8proc-2.7.0-7.fc40.x86_64.rpm                                                1.6 MB/s |  80 kB     00:00    
(6/11): subversion-1.14.3-5.fc40.x86_64.rpm                                             4.0 MB/s | 1.0 MB     00:00    
(7/11): subversion-libs-1.14.3-5.fc40.x86_64.rpm                                        5.3 MB/s | 1.5 MB     00:00    
(8/11): golang-1.22.3-1.fc40.x86_64.rpm                                                 1.9 MB/s | 666 kB     00:00    
(9/11): mercurial-6.7.3-1.fc40.x86_64.rpm                                               4.5 MB/s | 6.4 MB     00:01    
(10/11): golang-src-1.22.3-1.fc40.noarch.rpm                                            6.1 MB/s |  12 MB     00:01    
(11/11): golang-bin-1.22.3-1.fc40.x86_64.rpm                                            7.1 MB/s |  26 MB     00:03    
------------------------------------------------------------------------------------------------------------------------
Общий размер                                                                            8.8 MB/s |  48 MB     00:05     
Проверка транзакции
Проверка транзакции успешно завершена.
Идет проверка транзакции
Тест транзакции проведен успешно.
Выполнение транзакции
  Запуск скриптлета: golang-1.22.3-1.fc40.x86_64                                                                    1/1 
  Подготовка       :                                                                                                1/1 
  Установка        : golang-src-1.22.3-1.fc40.noarch                                                               1/11 
  Установка        : utf8proc-2.7.0-7.fc40.x86_64                                                                  2/11 
  Установка        : re2-1:20220601-5.fc40.x86_64                                                                  3/11 
  Установка        : python3-fb-re2-1.0.7-15.fc40.x86_64                                                           4/11 
  Установка        : mercurial-6.7.3-1.fc40.x86_64                                                                 5/11 
  Установка        : libserf-1.3.10-5.fc40.x86_64                                                                  6/11 
  Установка        : subversion-libs-1.14.3-5.fc40.x86_64                                                          7/11 
  Установка        : subversion-1.14.3-5.fc40.x86_64                                                               8/11 
  Запуск скриптлета: subversion-1.14.3-5.fc40.x86_64                                                               8/11 
  Установка        : go-filesystem-3.5.0-1.fc40.x86_64                                                             9/11 
  Установка        : golang-bin-1.22.3-1.fc40.x86_64                                                              10/11 
  Запуск скриптлета: golang-bin-1.22.3-1.fc40.x86_64                                                              10/11 
  Установка        : golang-1.22.3-1.fc40.x86_64                                                                  11/11 
  Запуск скриптлета: golang-1.22.3-1.fc40.x86_64                                                                  11/11 

Установлен:
  go-filesystem-3.5.0-1.fc40.x86_64           golang-1.22.3-1.fc40.x86_64         golang-bin-1.22.3-1.fc40.x86_64       
  golang-src-1.22.3-1.fc40.noarch             libserf-1.3.10-5.fc40.x86_64        mercurial-6.7.3-1.fc40.x86_64         
  python3-fb-re2-1.0.7-15.fc40.x86_64         re2-1:20220601-5.fc40.x86_64        subversion-1.14.3-5.fc40.x86_64       
  subversion-libs-1.14.3-5.fc40.x86_64        utf8proc-2.7.0-7.fc40.x86_64       

Выполнено!
```
# Вот (конец вчерашнего)

```sh                                                                              
❯ go install github.com/aktau/github-release@latest
go: finding module for package github.com/voxelbrain/goptions
go: finding module for package github.com/dustin/go-humanize
go: finding module for package github.com/github-release/github-release/github
go: found github.com/dustin/go-humanize in github.com/dustin/go-humanize v1.0.1
go: found github.com/github-release/github-release/github in github.com/github-release/github-release v0.10.0
go: found github.com/voxelbrain/goptions in github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: finding module for package github.com/tomnomnom/linkheader
go: finding module for package github.com/kevinburke/rest/restclient
go: found github.com/kevinburke/rest/restclient in github.com/kevinburke/rest v0.0.0-20231107185522-a9c371f90234
go: found github.com/tomnomnom/linkheader in github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
```

```sh
❯ ls -la ~/go/bin
итого 9744
drwxr-xr-x. 1 sofia sofia      28 мая 18 22:16 .
drwxr-xr-x. 1 sofia sofia      12 мая 18 22:16 ..
-rwxr-xr-x. 1 sofia sofia 9976612 мая 19 16:06 github-release

❯ git clone git@github.com:${GITHUB_USERNAME}/tp-lab08.git projects/lab09
Клонирование в «projects/lab09»...
remote: Enumerating objects: 100, done.
remote: Counting objects: 100% (100/100), done.
remote: Compressing objects: 100% (52/52), done.
remote: Total 100 (delta 36), reused 96 (delta 35), pack-reused 0
Получение объектов: 100% (100/100), 63.45 КиБ | 564.00 КиБ/с, готово.
Определение изменений: 100% (36/36), готово.
```
# А это уже так было
```sh
❯ cd projects/lab09 

❯ git remote remove origin

❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab09.git

❯ gsed -i 's/lab08/lab09/g' README.md

❯ sudo ${PACKAGE_MANAGER} install ${GPG_PACKAGE_NAME}
[sudo] пароль для sofia: 
Последняя проверка окончания срока действия метаданных: 0:08:50 назад, Вс 19 мая 2024 16:06:16.
Пакет gnupg2-2.4.4-1.fc40.x86_64 уже установлен.
Зависимости разрешены.
Нет действий для выполнения.
Выполнено!
```

```sh
❯ gpg --list-secret-keys --keyid-format LONG
[keyboxd]
---------
sec   rsa4096/D9E40212D59F8EB7 2024-05-18 [SC] [   годен до: 2024-06-01]
      AA637712B2E57F181CE72D9CD9E40212D59F8EB7
uid               [  абсолютно ] SofiaBachulashvili (test)
ssb   rsa4096/093CA11B1303CDC9 2024-05-18 [E] [   годен до: 2024-06-01]
```
# Ключ тоже был создан вчера
```sh
❯ gpg --full-generate-key 
gpg (GnuPG) 2.4.4; Copyright (C) 2024 g10 Code GmbH
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Выберите тип ключа:
   (1) RSA and RSA
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (9) ECC (sign and encrypt) *default*
  (10) ECC (только для подписи)
  (14) Existing key from card
Ваш выбор? 1
длина ключей RSA может быть от 1024 до 4096.
Какой размер ключа Вам необходим? (3072) 4096
Запрошенный размер ключа - 4096 бит
Выберите срок действия ключа.
         0 = не ограничен
      <n>  = срок действия ключа - n дней
      <n>w = срок действия ключа - n недель
      <n>m = срок действия ключа - n месяцев
      <n>y = срок действия ключа - n лет
Срок действия ключа? (0) 14
Ключ действителен до Сб 01 июн 2024 22:32:10 MSK
Все верно? (y/N) y

GnuPG должен составить идентификатор пользователя для идентификации ключа.

Ваше полное имя: SofiaBachulashvili
Адрес электронной почты: 
Примечание: test
Вы выбрали следующий идентификатор пользователя:
    "SofiaBachulashvili (test)"

Сменить (N)Имя, (C)Примечание, (E)Адрес; (O)Принять/(Q)Выход? O
Необходимо получить много случайных чисел. Желательно, чтобы Вы
в процессе генерации выполняли какие-то другие действия (печать
на клавиатуре, движения мыши, обращения к дискам); это даст генератору
случайных чисел больше возможностей получить достаточное количество энтропии.
Необходимо получить много случайных чисел. Желательно, чтобы Вы
в процессе генерации выполняли какие-то другие действия (печать
на клавиатуре, движения мыши, обращения к дискам); это даст генератору
случайных чисел больше возможностей получить достаточное количество энтропии.
gpg: создан каталог '/home/sofia/.gnupg/openpgp-revocs.d'
gpg: сертификат отзыва записан в '/home/sofia/.gnupg/openpgp-revocs.d/AA637712B2E57F181CE72D9CD9E40212D59F8EB7.rev'.
открытый и секретный ключи созданы и подписаны.

pub   rsa4096 2024-05-18 [SC] [   годен до: 2024-06-01]
      AA637712B2E57F181CE72D9CD9E40212D59F8EB7
uid                      SofiaBachulashvili (test)
sub   rsa4096 2024-05-18 [E] [   годен до: 2024-06-01]

❯ gpg --list-secret-keys --keyid-format LONG
gpg: проверка таблицы доверия
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: глубина: 0  достоверных:   1  подписанных:   0  доверие: 0-, 0q, 0n, 0m, 0f, 1u
gpg: срок следующей проверки таблицы доверия 2024-06-01
[keyboxd]
---------
sec   rsa4096/D9E40212D59F8EB7 2024-05-18 [SC] [   годен до: 2024-06-01]
      AA637712B2E57F181CE72D9CD9E40212D59F8EB7
uid               [  абсолютно ] SofiaBachulashvili (test)
ssb   rsa4096/093CA11B1303CDC9 2024-05-18 [E] [   годен до: 2024-06-01]


❯ gpg -K ${GITHUB_USERNAME}
sec   rsa4096 2024-05-18 [SC] [   годен до: 2024-06-01]
      AA637712B2E57F181CE72D9CD9E40212D59F8EB7
uid         [  абсолютно ] SofiaBachulashvili (test)
ssb   rsa4096 2024-05-18 [E] [   годен до: 2024-06-01]


❯ GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')

❯ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')

❯ gpg --armor --export ${GPG_KEY_ID} | pbcopy

    ~/SofiaBachulashvili/workspace/projects/lab09    main                                                       
❯ pbpaste
----BEGIN PGP PUBLIC KEY BLOCK-----

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
IZyBJg==
=IKL2
-----END PGP PUBLIC KEY BLOCK-----

```
# Вот (конец вчерашнего)

```sh
❯ git config user.signingkey ${GPG_SEC_KEY_ID}

❯ git config gpg.program gpg

❯ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.zshrc

❯ echo 'export GPG_TTY=$(tty)' >> ~/.profile
```
## Как жаль, что оно не цветное(((( 🌈🌈🌈
```sh
❯ source ~/.zshrc
Updating Oh My Zsh
master

Features:

 - fb91ca2 [amuse]        Add whitespace before virtualenv (#12423)
 - 8581ecd [autojump]     Add `nix-darwin` install path (#12389)
 - 5947c3c [dependencies] Add `wd` (#12405)
 - 423b9a8 [dependencies] Add support for semver tags
 - a8a747e [fzf]          Add support for Fedora package (#12421)
 - 8c5f64c [nvm]          Add `corepack` to `lazy_cmd`
 - d2cf10c [procs]        Add completions plugin (#12406)
 - 22bbc23 [python]       Autovenv keeps activated on subdirs (#12396)
 - 529f77a [termsupport]  Support `alacritty*` TERM (#12392)
 - b1c5315 [wd]           Update to version v0.6.1 (#12413)

Bug fixes:

 - b0561d2 [cli]          Fix edge cases in `omz plugin disable` command (#12401)
 - eb2ff84 [dependencies] Avoid creating PR if it's already there
 - 0493eab [dependencies] Check if repo is clean before committing
 - a258eb4 [dependencies] Improve typing
 - 668ca3a [extract]      `zst` now extracts as expected (#12395)
 - d91f4e8 [fzf]          Fix missing `is-at-least` error in setup (#12412)
 - 21963f4 [fzf]          Support old `fzf` versions
 - 0fabd5f [git]          Add checked-out branch support to `gbg*` (#12397)
 - 9af7ebc [nvm]          Use `command cat` to avoid alias (#12410)
 - b1af78d [nvm]          Use `nvm version` when needed (#12409)

Other changes:

 - 13c8a10 [dependencies] Style: Run `ruff` formatter

You can see the changelog with `omz changelog`
         __                                     __   
  ____  / /_     ____ ___  __  __   ____  _____/ /_  
 / __ \/ __ \   / __ `__ \/ / / /  /_  / / ___/ __ \ 
/ /_/ / / / /  / / / / / / /_/ /    / /_(__  ) / / / 
\____/_/ /_/  /_/ /_/ /_/\__, /    /___/____/_/ /_/  
                        /____/                       

Hooray! Oh My Zsh has been updated!

To keep up with the latest news and updates, follow us on Twitter: @ohmyzsh
Want to get involved in the community? Join our Discord: Discord server
Get your Oh My Zsh swag at: Planet Argon Shop
```

```sh
❯ cmake -H. -B_build -DCPACK_GENERATOR="TGZ" 
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 14.1.1
-- The CXX compiler identification is GNU 14.1.1
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 48e1753 | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Install (ver.: 1.14.0)
-- [hunter] Building GTest
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.1.1
-- The CXX compiler identification is GNU 14.1.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Build
[  6%] Creating directories for 'GTest-Release'
[ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
-- verifying file...
       file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- File already exists and hash match (skip download):
  file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
  SHA1='2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c'
-- extracting...
     src='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 18%] No update step for 'GTest-Release'
[ 25%] No patch step for 'GTest-Release'
[ 31%] Performing configure step for 'GTest-Release'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.1.1
-- The CXX compiler identification is GNU 14.1.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.3") found components: Interpreter 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
[ 37%] Performing build step for 'GTest-Release'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtest.a
[ 25%] Built target gtest
[ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_main.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmock.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_main.a
[100%] Built target gmock_main
[ 43%] Performing install step for 'GTest-Release'
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgmock.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgmock_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-release.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgtest.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgtest_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/args.cmake
[ 50%] Completed 'GTest-Release'
[ 50%] Built target GTest-Release
[ 56%] Creating directories for 'GTest-Debug'
[ 62%] Performing download step (download, verify and extract) for 'GTest-Debug'
-- verifying file...
       file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- File already exists and hash match (skip download):
  file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
  SHA1='2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c'
-- extracting...
     src='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 68%] No update step for 'GTest-Debug'
[ 75%] No patch step for 'GTest-Debug'
[ 81%] Performing configure step for 'GTest-Debug'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.1.1
-- The CXX compiler identification is GNU 14.1.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.3") found components: Interpreter 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (1.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
[ 87%] Performing build step for 'GTest-Debug'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtestd.a
[ 25%] Built target gtest
[ 37%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 50%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_maind.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmockd.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_maind.a
[100%] Built target gmock_main
[ 93%] Performing install step for 'GTest-Debug'
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgmockd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgmock_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-debug.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgtestd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/libgtest_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest/args.cmake
[100%] Completed 'GTest-Debug'
[100%] Built target GTest-Debug
-- [hunter] Build step successful (dir: /home/sofia/.hunter/_Base/a20151e/48e1753/4abab25/Build/GTest)
-- [hunter] Cache saved: /home/sofia/.hunter/_Base/Cache/raw/14159f4b400991a215b8836a50ea616de9678924.tar.bz2
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (68.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab09/_build
```

```sh
❯ cmake --build _build --target package
[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab09/_build/print-0.1.0.0-Linux.tar.gz generated.
```

```sh
❯ git config --global core.editor "micro"

❯ git tag -s v0.1.0.0 -m "Test new tag"

❯ git tag -v v0.1.0.0 
object 2dfe485a8420e74c35c9d272ee374e3e12f6bef9
type commit
tag v0.1.0.0
tagger SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com> 1716143312 +0300

Test new tag
gpg: Подпись сделана Вс 19 мая 2024 21:28:32 MSK
gpg:                ключом RSA с идентификатором AA637712B2E57F181CE72D9CD9E40212D59F8EB7
gpg: Действительная подпись пользователя "SofiaBachulashvili (test)" [абсолютное]
```

```sh
❯ git show v0.1.0.0
ag v0.1.0.0
Tagger: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Sun May 19 21:28:32 2024 +0300

Test new tag
-----BEGIN PGP SIGNATURE-----

iQIzBAABCAAdFiEEqmN3ErLlfxgc5y2c2eQCEtWfjrcFAmZKRNAACgkQ2eQCEtWf
jrengBAApqe3P6/YlwN/HtLxSdL4DtXY6DESMu1Q/hgRyI5Hzi4Q4PE2npM4O6Kv
AqQe7ANhU5al1emmqBiHTWgAg7lv1CJQ9NtC+aj9rrs/Z/FHAXVKsSnfd6i1m48O
0VvJy96y+Msy+H7FLdgDOUMM6IbX0hd05982DE2szl6vx8cE5Dh2TS+WXFAXQ2Qi
ygkLDXqIcDmcVjwtpJd4p97F91uGpvzrgT01EIALqOihdSk8XEtGmG3GYrVuwtFO
A6Q+p/KbCaHjqqBNNqObAL2PwSQe2RGU5MPiH1aS2ghb0dlmgfpOzT7lO8sFzqtK
4SRTWafHr/eWK4lMutgcERGBzcQCD5rgHaYxJzhtlwa/TJ4dM+fLTDfs7fYZmx0l
dubdHwEiIrSAoch+XakI9/RyM7HMGk/dGAoKc7E0dC+EXxjVXjs+qXfQS3E84U+j
PHy/b/syXzMRqNPlPnqTbYqyYRGpYorSzr2JSzylPSXWHwHCvvQdWR2VZaoKWRGO
sGrbggoFAjLe/FGH82gHtFRBCAz142/Rht3r9o/IzMEb0ZfvDWn8lNeyR+LM6lFc
No/y81kqT9qXYHhlSseWscIkJNXZJ2atsATzY1oixepWNrVssEo2BNpxdfKp9aWU
K06mSqJem7eI3leLn1YoE0retF7NEZzS+u+iDP3lvZ28AbMeIF0=
=ivuv
-----END PGP SIGNATURE-----

commit 2dfe485a8420e74c35c9d272ee374e3e12f6bef9 (HEAD -> main, tag: v0.1.0.0, origin/main)
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Sun May 19 00:15:36 2024 +0300

    Update README.md

diff --git a/README.md b/README.md
index 4aa4245..2bd3200 100644
--- a/README.md
+++ b/README.md
@@ -1,1186 +1,300 @@
 [![Build Status](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06.svg?token=QmQqzGNVkZy8A7N9cEfZ&branch=master)](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06)
```

```sh
❯ git push origin main --tags
Перечисление объектов: 101, готово.
Подсчет объектов: 100% (101/101), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (52/52), готово.
Запись объектов: 100% (101/101), 64.21 КиБ | 16.05 МиБ/с, готово.
Total 101 (delta 36), reused 100 (delta 36), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (36/36), done.
To github.com:SofiaBachulashvili/tp-lab09.git
 * [new branch]      main -> main
 * [new tag]         v0.1.0.0 -> v0.1.0.0

❯ github-release --version
bash: github-release: команда не найдена...

❯ ~/go/bin/github-release --version
github-release v0.9.0

❯ ~/go/bin/github-release info -u ${GITHUB_USERNAME} -r lab09         
error: could not fetch tags, invalid response body: {"message":"Not Found","documentation_url":"https://docs.github.com/rest/repos/repos#list-repository-tags"}

❯ ~/go/bin/github-release info -u ${GITHUB_USERNAME} -r tp-lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/SofiaBachulashvili/tp-lab09/commits/2dfe485a8420e74c35c9d272ee374e3e12f6bef9)
releases:
```
# Ему не понравилось --repo...
```sh
❯ ~/go/bin/github-release release \                             
    --user ${GITHUB_USERNAME} \          
    --repo tp-lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"                                      
...
bash: --repo: команда не найдена...
```
# Еще раз вспомним песню кота Леопольда 😺😸

# Ему не понравилось -r...
```sh
❯ ~/go/bin/github-release release \                             
    --user ${GITHUB_USERNAME} \          
    -r tp-lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"                                      
...
bash: -r: команда не найдена...
```
# В который раз вспомним песню кота Леопольда 😺😸

# Попробуем написать в одну строчку только этот кусочек 
```sh                                                                                 
❯ ~/go/bin/github-release release \
    --user ${GITHUB_USERNAME} --repo tp-lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"
```
# ПОМОГЛО!!! УРАААА!!!🎉🥳🎇
```sh
❯ export PACKAGE_OS=`uname -s` PACKAGE_ARCH=`uname -m`

❯ export PACKAGE_FILENAME=print-${PACKAGE_OS}-${PACKAGE_ARCH}.tar.gz
```
# А тут просто сработало, чудеса🫢😲😮
```sh
❯ ~/go/bin/github-release upload \
    --user ${GITHUB_USERNAME} \
    --repo tp-lab09 \
    --tag v0.1.0.0 \
    --name "${PACKAGE_FILENAME}" \
    --file _build/*.tar.gz
```

```sh
❯ ~/go/bin/github-release info -u ${GITHUB_USERNAME} -r tp-lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/SofiaBachulashvili/tp-lab09/commits/2dfe485a8420e74c35c9d272ee374e3e12f6bef9)
releases:
- v0.1.0.0, name: 'libprint', description: 'my first release', id: 156425394, tagged: 19/05/2024 at 18:28, published: 19/05/2024 at 18:44, draft: ✗, prerelease: ✗
  - artifact: print-Linux-x86_64.tar.gz, downloads: 0, state: uploaded, type: application/octet-stream, size: 6.0 kB, id: 168857848
```
```sh
❯ wget https://github.com/$\{GITHUB_USERNAME\}/tp-lab09/releases/download/v0.1.0.0/$\{PACKAGE_FILENAME\}
0 files              100% [=====================================================================================================>]  116.81K  941.58KB/s
                          [Files: 0  Bytes: 116.81K [89.58KB/s] Redirects: 0  Todo: 0  Errors: 1                                 ]

❯ wget https://github.com/SofiaBachulashvili/tp-lab09/releases/download/v0.1.0.0/print-Linux-x86_64.tar.gz
print-Linux-x86_64.t 100% [=====================================================================================================>]    5.87K    --.-KB/s
                          [Files: 1  Bytes: 5.87K [4.40KB/s] Redirects: 1  Todo: 0  Errors: 0                                    ]

❯ tar -ztf ${PACKAGE_FILENAME}
print-0.1.0.0-Linux/bin/
print-0.1.0.0-Linux/bin/demo
print-0.1.0.0-Linux/lib/
print-0.1.0.0-Linux/lib/libprint.a
print-0.1.0.0-Linux/include/
print-0.1.0.0-Linux/include/print.hpp
print-0.1.0.0-Linux/cmake/
print-0.1.0.0-Linux/cmake/print-config.cmake
print-0.1.0.0-Linux/cmake/print-config-noconfig.cmake
```
