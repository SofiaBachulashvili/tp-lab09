[![Build Status](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06.svg?token=QmQqzGNVkZy8A7N9cEfZ&branch=master)](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06)

# Лабораторная работа 6. ИУ8-24 Бачулашвили София

## tp-lab06

```sh
❯ export GITHUB_USERNAME=SofiaBachulashvili

❯ export GITHUB_EMAIL=airllll301@wave.com

❯ alias edit=micro

❯ alias gsed=sed

❯ cd ${GITHUB_USERNAME}/workspace

❯ pushd . 
~/SofiaBachulashvili/workspace ~

❯ source scripts/activate

❯ cd projects
```

```sh
❯ git clone git@github.com:${GITHUB_USERNAME}/tp-lab05.git lab06
Клонирование в «lab06»...
remote: Enumerating objects: 54, done.
remote: Counting objects: 100% (54/54), done.
remote: Compressing objects: 100% (32/32), done.
remote: Total 54 (delta 19), reused 44 (delta 14), pack-reused 0
Получение объектов: 100% (54/54), 20.85 КиБ | 3.47 МиБ/с, готово.
Определение изменений: 100% (19/19), готово.
```

```sh
❯ cd lab06

❯ git remote remove origin

❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab06.git
```


```sh
❯ sed -i '/project(print)/a\ 
set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")
' CMakeLists.txt

❯ sed -i '/project(print)/a\
set(PRINT_VERSION\
  \${PRINT_VERSION_MAJOR}.\${PRINT_VERSION_MINOR}.\${PRINT_VERSION_PATCH}.\${PRINT_VERSION_TWEAK})
' CMakeLists.txt

❯ sed -i '/project(print)/a\
set(PRINT_VERSION_TWEAK 0)
' CMakeLists.txt

❯ sed -i '/project(print)/a\
set(PRINT_VERSION_PATCH 0)
' CMakeLists.txt

❯ sed -i '/project(print)/a\
set(PRINT_VERSION_MINOR 1)
' CMakeLists.txt

❯ sed -i '/project(print)/a\
set(PRINT_VERSION_MAJOR 0)
' CMakeLists.txt
```


```sh
❯ git diff 
diff --git a/CMakeLists.txt b/CMakeLists.txt
index aa7a323..cf0cf12 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -4,9 +4,15 @@ set(CMAKE_CXX_STANDARD 11)
 set(CMAKE_CXX_STANDARD_REQUIRED ON)
 
 option(BUILD_EXAMPLES "Build examples" OFF)
-option(BUILD_TESTS "Build tests" OFF)
 
 project(print)
+set(PRINT_VERSION_MAJOR 0)
+set(PRINT_VERSION_MINOR 1)
+set(PRINT_VERSION_PATCH 0)
+set(PRINT_VERSION_TWEAK 0)
+set(PRINT_VERSION
+  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
+set(PRINT_VERSION_STRING "v${PRINT_VERSION}")
 
 add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
 
@@ -36,11 +42,4 @@ install(TARGETS print
 install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
 install(EXPORT print-config DESTINATION cmake)
 
-if(BUILD_TESTS)
-  enable_testing()
-  add_subdirectory(third-party/gtest)
-  file(GLOB ${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
-  add_executable(check ${${PROJECT_NAME}_TEST_SOURCES})
-  target_link_libraries(check ${PROJECT_NAME} gtest_main)
-  add_test(NAME check COMMAND check)
-endif()
+include(CPackConfig.cmake)
```

```sh
❯ edit DESCRIPTION  
```
# Пишем в файл:
## DESCRIPTION
## Study of batching tools using CPack as an example.
## Я тучка, тучка, тучка 🌩️🌩️🌩️
## Я вовсе не медведь 🐻
## И как приятно тучке по небу лететь 🌩️🌠
# Выходим из редактирования файла - Жмем Q

```sh
❯ touch ChangeLog.md
                                  
❯ export DATE="`LANG=en_US date +'%a %b %d %Y'`" 
```

```sh
❯ cat > ChangeLog.md <<EOF
* ${DATE} ${GITHUB_USERNAME} <${GITHUB_EMAIL}> 0.1.0.0
- Initial RPM release
EOF                                                     


❯ cat > CPackConfig.cmake <<EOF
include(InstallRequiredSystemLibraries)
EOF                                                     


❯ cat >> CPackConfig.cmake <<EOF
set(CPACK_PACKAGE_CONTACT ${GITHUB_EMAIL})
set(CPACK_PACKAGE_VERSION_MAJOR \${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR \${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH \${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK \${PRINT_VERSION_TWEAK})
set(CPACK_PACKAGE_VERSION \${PRINT_VERSION})
set(CPACK_PACKAGE_DESCRIPTION_FILE \${CMAKE_CURRENT_SOURCE_DIR}/DESCRIPTION)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "static C++ library for printing")
EOF                                                     


❯ cat >> CPackConfig.cmake <<EOF

set(CPACK_RESOURCE_FILE_LICENSE \${CMAKE_CURRENT_SOURCE_DIR}/LICENSE)
set(CPACK_RESOURCE_FILE_README \${CMAKE_CURRENT_SOURCE_DIR}/README.md)
EOF
                                                                          
❯ cat >> CPackConfig.cmake <<EOF

set(CPACK_RPM_PACKAGE_NAME "print-devel")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "print")
set(CPACK_RPM_CHANGELOG_FILE \${CMAKE_CURRENT_SOURCE_DIR}/ChangeLog.md)
set(CPACK_RPM_PACKAGE_RELEASE 1)
EOF
                                                                       
❯ cat >> CPackConfig.cmake <<EOF

set(CPACK_DEBIAN_PACKAGE_NAME "libprint-dev")
set(CPACK_DEBIAN_PACKAGE_PREDEPENDS "cmake >= 3.0")
set(CPACK_DEBIAN_PACKAGE_RELEASE 1)
EOF
                                                                              
❯ cat >> CPackConfig.cmake <<EOF

include(CPack)
EOF
                                                                             
❯ cat >> CMakeLists.txt <<EOF

include(CPackConfig.cmake)
EOF
```

# Меняем в README.md : lab05 -> lab06
```sh
❯ sed -i 's/lab05/lab06/g' README.md
```

```sh
❯ git add .
                                           
❯ git commit -m "added cpack config"
[main f47d4e6] added cpack config
 5 files changed, 64 insertions(+), 34 deletions(-)
 create mode 100644 CPackConfig.cmake
 create mode 100644 ChangeLog.md
 create mode 100644 DESCRIPTION
```

Опция --tags отправляет все созданные локальные теги вместе с другими изменениями на удаленный репозиторий.

## Отправим изменения в main я и добавим тег v0.1.0.0 на удаленный репозиторий.
```sh
❯ git tag v0.1.0.0                                                                                      
❯ git push origin main --tags
Перечисление объектов: 61, готово.
Подсчет объектов: 100% (61/61), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (34/34), готово.
Запись объектов: 100% (61/61), 22.54 КиБ | 2.05 МиБ/с, готово.
Total 61 (delta 22), reused 53 (delta 19), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (22/22), done.
To github.com:SofiaBachulashvili/tp-lab06.git
 * [new branch]      main -> main
 * [new tag]         v0.1.0.0 -> v0.1.0.0
```

```sh                                          
❯ cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 14.0.1
-- The CXX compiler identification is GNU 14.0.1
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
CMake Error at /usr/share/cmake/Modules/CPack.cmake:685 (message):
  CPack license resource file:
  "/home/sofia/SofiaBachulashvili/workspace/projects/lab06/LICENSE" could not
  be found.
Call Stack (most recent call first):
  /usr/share/cmake/Modules/CPack.cmake:690 (cpack_check_file_exists)
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:45 (include)


CMake Warning at /usr/share/cmake/Modules/CPack.cmake:507 (message):
  CPack.cmake has already been included!!
Call Stack (most recent call first):
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:47 (include)


CMake Error at /usr/share/cmake/Modules/CPack.cmake:685 (message):
  CPack license resource file:
  "/home/sofia/SofiaBachulashvili/workspace/projects/lab06/LICENSE" could not
  be found.
Call Stack (most recent call first):
  /usr/share/cmake/Modules/CPack.cmake:690 (cpack_check_file_exists)
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:47 (include)


-- Configuring incomplete, errors occurred!
```

```sh                                                                                     
❯ ls
_build  ChangeLog.md  CMakeLists.txt  CPackConfig.cmake  DESCRIPTION  examples  include  README.md  sources  TEST.md  tests  third-party
```
 ## Лицензии нет, надо добавить
 ```sh
❯ git pull origin main
Из github.com:SofiaBachulashvili/tp-lab06
 * branch            main       -> FETCH_HEAD
Обновление f47d4e6..4aac1db
Fast-forward
 LICENSE | 674 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 674 insertions(+)
 create mode 100644 LICENSE
                                                                                     
❯ ls                  
_build  ChangeLog.md  CMakeLists.txt  CPackConfig.cmake  DESCRIPTION  examples  include  LICENSE  README.md  sources  TEST.md  tests  third-party
```
## Теперь есть 😄🥰

```                                                                                     
❯ cmake -H. -B_build  
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Warning at /usr/share/cmake/Modules/CPack.cmake:507 (message):
  CPack.cmake has already been included!!
Call Stack (most recent call first):
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:47 (include)


-- Configuring done (0.1s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build
```

```sh
❯ cmake --build _build                                
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
                                               
❯ cd _build
```

```sh
❯ cpack -G "TGZ" 
CPack: Create package using TGZ
CPack: Install projects
CPack: - Install directory: /home/sofia/SofiaBachulashvili/workspace/projects/lab06
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build/print-0.1.0.0-Source.tar.gz generated.
                                          
❯ cd ..
```

```sh
❯ cmake -H. -B_build -DCPACK_GENERATOR="TGZ" 
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Warning at /usr/share/cmake/Modules/CPack.cmake:507 (message):
  CPack.cmake has already been included!!
Call Stack (most recent call first):
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:47 (include)


-- Configuring done (0.1s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build
```

```sh
❯ cmake --build _build --target package 
[100%] Built target print
Run CPack packaging tool...
CPack: Create package using TBZ2
CPack: Install projects
CPack: - Install directory: /home/sofia/SofiaBachulashvili/workspace/projects/lab06
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build/print-0.1.0.0-Source.tar.bz2 generated.
CPack: Create package using TGZ
CPack: Install projects
CPack: - Install directory: /home/sofia/SofiaBachulashvili/workspace/projects/lab06
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build/print-0.1.0.0-Source.tar.gz generated.
CPack: Create package using TXZ
CPack: Install projects
CPack: - Install directory: /home/sofia/SofiaBachulashvili/workspace/projects/lab06
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build/print-0.1.0.0-Source.tar.xz generated.
CPack: Create package using TZ
CPack: Install projects
CPack: - Install directory: /home/sofia/SofiaBachulashvili/workspace/projects/lab06
CPack: Create package
CPack: - package: /home/sofia/SofiaBachulashvili/workspace/projects/lab06/_build/print-0.1.0.0-Source.tar.Z generated.
```

```sh                                                   ❯ mkdir artifacts
                                                      
❯ mv _build/*.tar.gz artifacts
                                               
❯ tree artifacts  
artifacts
└── print-0.1.0.0-Source.tar.gz

1 directory, 1 file
```
