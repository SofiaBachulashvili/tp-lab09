# tp-lab02

```sh
❯ export GITHUB_USERNAME=SofiaBachulashvili                                                                                                     
❯ export GITHUB_EMAIL=airllll301@wave.com
❯ export GITHUB_TOKEN=8458b1d651d9faf2691730497b34526730947b758078610ec3a56ebe844fd1a3                                                                                                 
❯ alias edit=micro    
```
 
```sh                                                                                        
❯ cd ${GITHUB_USERNAME}/workspace
❯ source scripts/activate   
```

```sh
❯ mkdir ~/.config
❯ cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: ssh
EOF                                                                   
❯ git config --global hub.protocol ssh
```

```sh                                                                 
❯ mkdir projects/lab02 && cd projects/lab02                                                         
❯ git init
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
Инициализирован пустой репозиторий Git в /home/sofia/SofiaBachulashvili/workspace/projects/lab02/.git/
```

```sh                                      
❯ git config --global user.name ${GITHUB_USERNAME}                                      
❯ git config --global user.email ${GITHUB_EMAIL}                                          
❯ git config -e --global                                                                 
❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab02.git                                           
❯ git pull origin main  
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), 869 байтов | 289.00 КиБ/с, готово.
Из github.com:SofiaBachulashvili/tp-lab02
 * branch            main       -> FETCH_HEAD
 * [новая ветка]     main       -> origin/main
```

```sh                                             
❯ touch TEST.md                                     
❯ git status 
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	TEST.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
```

```sh                                       
❯ git add TEST.md                                        
❯ git commit -m "added TEST.md"
[master 629b340] added TEST.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 TEST.md
```

```sh                                        
❯ git push origin master
Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 300 байтов | 300.00 КиБ/с, готово.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/SofiaBachulashvili/tp-lab02/pull/new/master
remote: 
To github.com:SofiaBachulashvili/tp-lab02.git
 * [new branch]      master -> master
 ```

```sh
❯ git pull origin main
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (4/4), done.
Распаковка объектов: 100% (5/5), 2.71 КиБ | 693.00 КиБ/с, готово.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Из github.com:SofiaBachulashvili/tp-lab02
 * branch            main       -> FETCH_HEAD
   86b8ca2..81b073d  main       -> origin/main
Обновление 629b340..81b073d
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
```

```sh                                        
❯ git log
commit 81b073d26ff1f3dbf4c82026b187e5d3064a81cc (HEAD -> master, origin/main)
Merge: 4e71475 cc0fc03
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Mon Apr 29 19:15:07 2024 +0300

    Merge pull request #2 from SofiaBachulashvili/master
    
    Create .gitignore

commit cc0fc03854f1efee326ea865ee66706fc31c1662
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Mon Apr 29 19:13:36 2024 +0300

    Create .gitignore

commit 4e71475b13afe3afb6fbe758a2f48a8054473974
Merge: 86b8ca2 629b340
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Mon Apr 29 19:11:54 2024 +0300

    Merge pull request #1 from SofiaBachulashvili/master
    
    added TEST.md

commit 629b3406e3c82929eae156ab55cc4f03e57bd4b5 (origin/master)
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Mon Apr 29 19:07:23 2024 +0300

    added TEST.md

commit 86b8ca23462a00d1ddb7fcdb53e03fda57e9ace0
Author: SofiaBachulashvili <148392385+SofiaBachulashvili@users.noreply.github.com>
Date:   Mon Apr 29 19:02:23 2024 +0300

    Initial commit
```

```sh
❯ mkdir sources && mkdir include && mkdir examples
                                            
❯ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
```

```sh                                       
❯ cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
```

```sh                            
❯ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
                                 
❯ cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
``` 
