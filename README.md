# Лабораторная работа 4. ИУ8-24 Бачулашвили София

# tp-lab04

```sh                                                                                                                                         
❯ export GITHUB_USERNAME=SofiaBachulashvili 
                                                                                                                                         
❯ export GITHUB_TOKEN=a85huhig884jhh84h4g69mf0lkjijf76fgjoh984ihh988jihhhu5908
                                                                                                                                    
❯ cd ${GITHUB_USERNAME}/workspace
                                                                                                               
❯ pushd .
~/SofiaBachulashvili/workspace ~
                                                                                                                 
❯ source scripts/activate
```

```sh
git clone git@github.com:${GITHUB_USERNAME}/tp-lab03.git projects/lab04
Клонирование в «projects/lab04»...
remote: Enumerating objects: 25, done.
remote: Counting objects: 100% (25/25), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 25 (delta 3), reused 25 (delta 3), pack-reused 0
Получение объектов: 100% (25/25), 8.28 КиБ | 4.14 МиБ/с, готово.
Определение изменений: 100% (3/3), готово.
```

```sh
❯ cd projects/lab04
 git remote remove origin
                                                                                     
❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab04.git
```

```sh
❯ cat > .travis.yml <<EOF
language: cpp
EOF
                                                                              
❯ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
                                                                            
❯ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
```

```sh
❯ git add .travis.yml
[main 8779727] added CI
 1 file changed, 14 insertions(+)
 create mode 100644 .travis.yml

❯ git push origin main
Перечисление объектов: 28, готово.
Подсчет объектов: 100% (28/28), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (19/19), готово.
Запись объектов: 100% (28/28), 8.71 КиБ | 4.35 МиБ/с, готово.
Total 28 (delta 4), reused 24 (delta 3), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (4/4), done.
To github.com:SofiaBachulashvili/tp-lab04.git
 * [new branch]      main -> main
```
