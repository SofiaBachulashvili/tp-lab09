[![Build Status](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06.svg?token=QmQqzGNVkZy8A7N9cEfZ&branch=master)](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06)

# Лабораторная работа 7. ИУ8-24 Бачулашвили София

## tp-lab07
```sh
❯ export GITHUB_USERNAME=SofiaBachulashvili
                                                                                                          
❯ alias gsed=sed
                                                                                                          
❯ cd ${GITHUB_USERNAME}/workspace
                                                                               
❯ pushd .
~/SofiaBachulashvili/workspace ~
```

```sh
❯ git clone git@github.com:${GITHUB_USERNAME}/tp-lab06.git projects/lab07
Клонирование в «projects/lab07»...
remote: Enumerating objects: 73, done.
remote: Counting objects: 100% (73/73), done.
remote: Compressing objects: 100% (43/43), done.
remote: Total 73 (delta 28), reused 59 (delta 22), pack-reused 0
Получение объектов: 100% (73/73), 41.41 КиБ | 165.00 КиБ/с, готово.
Определение изменений: 100% (28/28), готово.
```

```sh                                              
❯ cd projects/lab07
                                                    
❯ git remote remove origin
                                                      
❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab07.git 


❯ mkdir -p cmake
```

```sh                                               
❯ wget https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake -O cmake/HunterGate.cmake
cmake/HunterGate.cma 100% [=====================================================================>]    4.81K    --.-KB/s
                          [Files: 1  Bytes: 4.81K [1.58KB/s] Redirects: 0  Todo: 0  Errors: 0    ]
```

## Редактируем CMakeLists.txt
```
❯ nvim CMakeLists.txt

❯ git rm -rf third-party/gtest 
rm 'third-party/gtest'

❯ ls    
ChangeLog.md  CMakeLists.txt     DESCRIPTION  include  README.md  TEST.md  third-party
cmake         CPackConfig.cmake  examples     LICENSE  sources    tests

❯ ls tests 
test1.cpp
```

```sh
❯ cmake -H. -B_builds -DBUILD_TESTS=ON
CMake Deprecation Warning at CMakeLists.txt:2 (cmake_minimum_required):
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
CMake Warning at /usr/share/cmake/Modules/CPack.cmake:507 (message):
  CPack.cmake has already been included!!
Call Stack (most recent call first):
  CPackConfig.cmake:24 (include)
  CMakeLists.txt:48 (include)


-- Configuring done (1.4s)
-- Generating done (0.0s)
CMake Warning:
  Manually-specified variables were not used by the project:

    BUILD_TESTS


-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds
```

```sh
❯ cat CMakeLists.txt              

cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)
set(PRINT_VERSION_MAJOR 0)
set(PRINT_VERSION_MINOR 1)
set(PRINT_VERSION_PATCH 0)
set(PRINT_VERSION_TWEAK 0)
set(PRINT_VERSION
  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
set(PRINT_VERSION_STRING "v${PRINT_VERSION}")

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)

include(CPackConfig.cmake)

include(CPackConfig.cmake)
```

```sh
❯ nvim CMakeLists.txt                                                                                       

❯ cmake -H. -B_builds -DBUILD_TESTS=ON
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [hunter] Initializing Hunter workspace (a20151e4c0740ee7d0f9994476856d813cdead29)
-- [hunter]   https://github.com/cpp-pm/hunter/archive/v0.25.5.tar.gz
-- [hunter]   -> /home/sofia/.hunter/_Base/Download/Hunter/0.25.5/a20151e
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 797581c | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Install (ver.: 1.14.0)
-- [hunter] Building GTest
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.0.1
-- The CXX compiler identification is GNU 14.0.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.6s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Build
[  6%] Creating directories for 'GTest-Release'
[ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
-- Downloading...
   dst='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
   timeout='none'
   inactivity timeout='none'
-- Using src='https://github.com/google/googletest/archive/v1.14.0.tar.gz'
-- [download 0% complete]
-- [download 1% complete]
-- [download 2% complete]
-- [download 3% complete]
-- [download 4% complete]
-- [download 5% complete]
-- [download 6% complete]
-- [download 7% complete]
-- [download 8% complete]
-- [download 13% complete]
-- [download 15% complete]
-- [download 16% complete]
-- [download 21% complete]
-- [download 25% complete]
-- [download 33% complete]
-- [download 34% complete]
-- [download 35% complete]
-- [download 44% complete]
-- [download 45% complete]
-- [download 46% complete]
-- [download 47% complete]
-- [download 48% complete]
-- [download 49% complete]
-- [download 50% complete]
-- [download 51% complete]
-- [download 52% complete]
-- [download 53% complete]
-- [download 54% complete]
-- [download 55% complete]
-- [download 56% complete]
-- [download 57% complete]
-- [download 58% complete]
-- [download 59% complete]
-- [download 60% complete]
-- [download 61% complete]
-- [download 62% complete]
-- [download 63% complete]
-- [download 64% complete]
-- [download 65% complete]
-- [download 66% complete]
-- [download 68% complete]
-- [download 69% complete]
-- [download 70% complete]
-- [download 71% complete]
-- [download 72% complete]
-- [download 73% complete]
-- [download 74% complete]
-- [download 75% complete]
-- [download 76% complete]
-- [download 77% complete]
-- [download 78% complete]
-- [download 79% complete]
-- [download 80% complete]
-- [download 81% complete]
-- [download 82% complete]
-- [download 83% complete]
-- [download 84% complete]
-- [download 85% complete]
-- [download 86% complete]
-- [download 87% complete]
-- [download 88% complete]
-- [download 89% complete]
-- [download 90% complete]
-- [download 91% complete]
-- [download 92% complete]
-- [download 93% complete]
-- [download 94% complete]
-- [download 95% complete]
-- [download 96% complete]
-- [download 97% complete]
-- [download 98% complete]
-- [download 99% complete]
-- [download 100% complete]
-- verifying file...
       file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- Downloading... done
-- extracting...
     src='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 18%] No update step for 'GTest-Release'
[ 25%] No patch step for 'GTest-Release'
[ 31%] Performing configure step for 'GTest-Release'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.0.1
-- The CXX compiler identification is GNU 14.0.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.2") found components: Interpreter 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
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
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgmock.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgmock_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-release.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgtest.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgtest_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/args.cmake
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
     dst='/home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 68%] No update step for 'GTest-Debug'
[ 75%] No patch step for 'GTest-Debug'
[ 81%] Performing configure step for 'GTest-Debug'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/args.cmake
-- The C compiler identification is GNU 14.0.1
-- The CXX compiler identification is GNU 14.0.1
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.2") found components: Interpreter 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (1.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
[ 87%] Performing build step for 'GTest-Debug'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtestd.a
[ 25%] Built target gtest
[ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_maind.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmockd.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_maind.a
[100%] Built target gmock_main
[ 93%] Performing install step for 'GTest-Debug'
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgmockd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgmock_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-debug.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgtestd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/libgtest_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest/args.cmake
[100%] Completed 'GTest-Debug'
[100%] Built target GTest-Debug
-- [hunter] Build step successful (dir: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Build/GTest)
-- [hunter] Cache saved: /home/sofia/.hunter/_Base/Cache/raw/c53335953e17fad919e1a49dc85c365a85bb96f7.tar.bz2
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (84.7s)
CMake Error at CMakeLists.txt:54 (add_executable):
  Cannot find source file:

    /home/sofia/SofiaBachulashvili/workspace/projects/lab07/demo/main.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:54 (add_executable):
  No SOURCES given to target: demo
  

CMake Generate step failed.  Build files cannot be regenerated correctly.
```
## Ошибка -> CMakeLists.txt надо отредактировать

```sh
❯ ls      
_builds       cmake           CPackConfig.cmake  examples  LICENSE    sources  tests
ChangeLog.md  CMakeLists.txt  DESCRIPTION        include   README.md  TEST.md  third-party

❯ mkdir demo         

❯ nvim CMakeLists.txt
```

```sh
❯ cmake -H. -B_builds -DBUILD_TESTS=ON
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 797581c | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Install (ver.: 1.14.0)
-- Configuring done (2.2s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds
```

```sh
❯ cmake --build _builds 
[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/check.dir/tests/test1.cpp.o
[100%] Linking CXX executable check
[100%] Built target check

❯ cmake --build _builds --target test
Running tests...
Test project /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds
    Start 1: check
1/1 Test #1: check ............................   Passed    0.01 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec
```

```sh
❯ ls -la $HOME/.hunter
итого 0
drwxr-xr-x. 1 sofia sofia  10 мая 16 18:08 .
drwx------. 1 sofia sofia 836 мая 16 18:13 ..
drwxr-xr-x. 1 sofia sofia  52 мая 16 18:09 _Base

❯ mkdir demo 
mkdir: невозможно создать каталог «demo»: Файл существует
```
## тк файл demo есть -> Идем туда и пишем ✍🏻

```sh
❯ ls demo            

❯ cat > demo/main.cpp <<EOF
#include <print.hpp>

#include <cstdlib>

int main(int argc, char* argv[])
{
  const char* log_path = std::getenv("LOG_PATH");
  if (log_path == nullptr)
  {
    std::cerr << "undefined environment variable: LOG_PATH" << std::endl;
    return 1;
  }
  std::string text;
  while (std::cin >> text)
  {
    std::ofstream out{log_path, std::ios_base::app};
    print(text, out);
    out << std::endl;
  }
}
EOF
```

```sh
❯ nvim CMakeLists.txt

❯ mkdir tools

❯ git submodule add https://github.com/ruslo/polly tools/polly
Клонирование в «/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly»...
remote: Enumerating objects: 6578, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 6578 (delta 21), reused 20 (delta 17), pack-reused 6546
Получение объектов: 100% (6578/6578), 1.68 МиБ | 273.00 КиБ/с, готово.
Определение изменений: 100% (4551/4551), готово.

```sh
❯ tools/polly/bin/polly.py --test
Python version: 3.12
Build dir: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.2

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default`
  `-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake"

CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [polly] Used toolchain: Default
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
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 797581c | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Install (ver.: 1.14.0)
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
CMake Error at CMakeLists.txt:54 (h90add_executable):
  Unknown CMake command "h90add_executable".


-- Configuring incomplete, errors occurred!
Command exit with status "1": [/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake"

Log: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_logs/polly/default/log.txt
*** FAILED ***
```
## Опять лишнее в CMakeLists.txt
## Сейчас уберем

```sh
❯ nvim CMakeLists.txt                                         
```
## Ох polly
```sh
❯ tools/polly/bin/polly.py --test
Python version: 3.12
Build dir: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.2

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default`
  `-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake"

CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [polly] Used toolchain: Default
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
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 797581c | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/797581c/4abab25/Install (ver.: 1.14.0)
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (3.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default
Execute command: [
  `cmake`
  `--build`
  `/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default`
  `--`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--build" "/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "--"

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run tests
Execute command: [
  `ctest`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default]> "ctest"

*********************************
No test configuration file found!
*********************************
Usage

  ctest [options]

-
Log saved: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_logs/polly/default/log.txt
-
Generate: 0:00:04.433655s
Build: 0:00:02.646162s
Test: 0:00:00.027277s
-
Total: 0:00:07.107517s
-
SUCCESS
```
## Не работает insert 😢😭
```sh
❯ tools/polly/bin/polly.py --install 
Python version: 3.12
Build dir: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.2

CMake suite maintained and supported by Kitware (kitware.com/cmake).

== WARNING ==

Looks like cmake arguments changed. You have two options to fix it:
  * Remove build directory completely by adding '--clear' (works 100%)
  * Run configure again by adding '--reconfig' (you must understand how CMake cache variables works/updated)

- "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake"
+ "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/default.cmake" "-DCMAKE_INSTALL_PREFIX=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_install/default"
?                                                                                                                                                                                                     ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```

```sh
❯ tools/polly/bin/polly.py --toolchain clang-cxx14
Python version: 3.12
Build dir: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14
Execute command: [
  `which`
  `cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.2

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14`
  `-GUnix Makefiles`
  `-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/clang-cxx14.cmake`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "-H." "-B/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14" "-GUnix Makefiles" "-DCMAKE_TOOLCHAIN_FILE=/home/sofia/SofiaBachulashvili/workspace/projects/lab07/tools/polly/clang-cxx14.cmake"

CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 18.1.1
-- The CXX compiler identification is Clang 18.1.1
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/sofia/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 9f630b4 | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Install (ver.: 1.14.0)
-- [hunter] Building GTest
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 18.1.1
-- The CXX compiler identification is Clang 18.1.1
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.6s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Build
[  6%] Creating directories for 'GTest-Release'
[ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
-- verifying file...
       file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- File already exists and hash match (skip download):
  file='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
  SHA1='2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c'
-- extracting...
     src='/home/sofia/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 18%] No update step for 'GTest-Release'
[ 25%] No patch step for 'GTest-Release'
[ 31%] Performing configure step for 'GTest-Release'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 18.1.1
-- The CXX compiler identification is Clang 18.1.1
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.2") found components: Interpreter
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
[ 37%] Performing build step for 'GTest-Release'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtest.a
[ 25%] Built target gtest
[ 50%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_main.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmock.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_main.a
[100%] Built target gmock_main
[ 43%] Performing install step for 'GTest-Release'
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgmock.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgmock_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-release.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgtest.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgtest_main.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/args.cmake
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
     dst='/home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 68%] No update step for 'GTest-Debug'
[ 75%] No patch step for 'GTest-Debug'
[ 81%] Performing configure step for 'GTest-Debug'
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/cache.cmake
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 18.1.1
-- The CXX compiler identification is Clang 18.1.1
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.12 (found version "3.12.2") found components: Interpreter
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
[ 87%] Performing build step for 'GTest-Debug'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtestd.a
[ 25%] Built target gtest
[ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_maind.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmockd.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_maind.a
[100%] Built target gmock_main
[ 93%] Performing install step for 'GTest-Debug'
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgmockd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgmock_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gmock_main.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestTargets-debug.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal
-- Up-to-date: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgtestd.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/libgtest_maind.a
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest.pc
-- Installing: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/Install/lib64/pkgconfig/gtest_main.pc
loading initial cache file /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest/args.cmake
[100%] Completed 'GTest-Debug'
[100%] Built target GTest-Debug
-- [hunter] Build step successful (dir: /home/sofia/.hunter/_Base/a20151e/9f630b4/4abab25/Build/GTest)
-- [hunter] Cache saved: /home/sofia/.hunter/_Base/Cache/raw/fe4db8820e8515f2920760605f5d8a0d05d9ced8.tar.bz2
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (55.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14
Execute command: [
  `cmake`
  `--build`
  `/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14`
  `--`
]

[/home/sofia/SofiaBachulashvili/workspace/projects/lab07]> "cmake" "--build" "/home/sofia/SofiaBachulashvili/workspace/projects/lab07/_builds/clang-cxx14" "--"

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
-
Log saved: /home/sofia/SofiaBachulashvili/workspace/projects/lab07/_logs/polly/clang-cxx14/log.txt
-
Generate: 0:00:56.526681s
Build: 0:00:02.848324s
-
Total: 0:00:59.375408s
-
SUCCESS
```

```sh
❯ git add .                                                            

❯ git commit -m "Added and configured Hunter"                            
[main 57f9ef3] Added and configured Hunter
 10 files changed, 1045 insertions(+), 6 deletions(-)
 create mode 100644 _logs/polly/clang-cxx14/log.txt
 create mode 100644 _logs/polly/default/log-0.txt
 create mode 100644 _logs/polly/default/log-1.txt
 create mode 100644 _logs/polly/default/log.txt
 create mode 100644 cmake/HunterGate.cmake
 create mode 100644 demo/main.cpp
 delete mode 160000 third-party/gtest
 create mode 160000 tools/polly
                                                    
❯ git push origin main 
Перечисление объектов: 90, готово.
Подсчет объектов: 100% (90/90), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (49/49), готово.
Запись объектов: 100% (90/90), 50.52 КиБ | 3.61 МиБ/с, готово.
Total 90 (delta 32), reused 71 (delta 28), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (32/32), done.
To github.com:SofiaBachulashvili/tp-lab07.git
 * [new branch]      main -> main
```
