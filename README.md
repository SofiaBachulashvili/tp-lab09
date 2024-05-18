[![Build Status](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06.svg?token=QmQqzGNVkZy8A7N9cEfZ&branch=master)](https://app.travis-ci.com/SofiaBachulashvili/tp-lab06)

# Лабораторная работа 8. ИУ8-24 Бачулашвили София
## tp-lab08
```sh
❯ export GITHUB_USERNAME=SofiaBachulashvili

❯ cd ${GITHUB_USERNAME}/workspace

❯ pushd .
~/SofiaBachulashvili/workspace ~

❯ source scripts/activate
```

```sh
❯ git clone git@github.com:${GITHUB_USERNAME}/tp-lab07.git projects/lab08
Клонирование в «projects/lab08»...
remote: Enumerating objects: 93, done.
remote: Counting objects: 100% (93/93), done.
remote: Compressing objects: 100% (48/48), done.
remote: Total 93 (delta 34), reused 88 (delta 32), pack-reused 0
Получение объектов: 100% (93/93), 57.85 КиБ | 553.00 КиБ/с, готово.
Определение изменений: 100% (34/34), готово.

❯ cd projects/lab08                                                   

❯ git submodule update --init 
Подмодуль «tools/polly» (https://github.com/ruslo/polly) зарегистрирован по пути «tools/polly»
Клонирование в «/home/sofia/SofiaBachulashvili/workspace/projects/lab08/tools/polly»...
Submodule path 'tools/polly': checked out 'ef7e79c2c297d456f2742fd0b976f555d058d4e0'

❯ git remote remove origin

❯ git remote add origin git@github.com:${GITHUB_USERNAME}/tp-lab08.git
```

```sh
❯ cat > Dockerfile <<EOF
FROM ubuntu:22.04
EOF

❯ cat >> Dockerfile <<EOF

RUN apt update
RUN apt install -yy build-essential clang gcc make cmake
EOF

❯ cat >> Dockerfile <<EOF

COPY . print/
WORKDIR print
EOF

❯ cat >> Dockerfile <<EOF

RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF

❯ cat >> Dockerfile <<EOF

ENV LOG_PATH /home/logs/log.txt
EOF

❯ cat >> Dockerfile <<EOF

VOLUME /home/logs
EOF

❯ cat >> Dockerfile <<EOF

WORKDIR _install/bin
EOF

❯ cat >> Dockerfile <<EOF

ENTRYPOINT ./demo
EOF
```

```sh
❯ sudo docker info 
[sudo] пароль для sofia:
Client: Docker Engine - Community
 Version:    26.1.2
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.14.0
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.27.0
    Path:     /usr/libexec/docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 26.1.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: systemd
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 Swarm: inactive
 Runtimes: runc io.containerd.runc.v2
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: e377cd56a71523140ca6ae87e30244719194a521
 runc version: v1.1.12-0-g51d5e94
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.8.7-300.fc40.x86_64
 Operating System: Fedora Linux 40 (Workstation Edition)
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 3.783GiB
 Name: 192.168.227.129
 ID: 5f7ff6f5-a5a2-4378-a669-850fc6b6bad9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
```

# Docker был скачен и настроен заранее, поэтому такой скудный вывод у этой команды)))
```sh
❯ sudo docker build -t logger .
[+] Building 214.7s (14/14) FINISHED                                                                     docker:default
 => [internal] load build definition from Dockerfile                                                               0.1s
 => => transferring dockerfile: 461B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04                                                    3.8s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => [1/9] FROM docker.io/library/ubuntu:22.04@sha256:a6d2b38300ce017add71440577d5b0a90460d0e57fd7aec21dd0d1b0761  11.2s
 => => resolve docker.io/library/ubuntu:22.04@sha256:a6d2b38300ce017add71440577d5b0a90460d0e57fd7aec21dd0d1b0761b  0.0s
 => => sha256:a8b1c5f80c2d2a757adc963e3fe2dad0b4d229f83df3349fbb70e4d12dd48822 29.53MB / 29.53MB                   7.3s
 => => sha256:a6d2b38300ce017add71440577d5b0a90460d0e57fd7aec21dd0d1b0761bbfb2 1.13kB / 1.13kB                     0.0s
 => => sha256:2af372c1e2645779643284c7dc38775e3dbbc417b2d784a27c5a9eb784014fb8 424B / 424B                         0.0s
 => => sha256:52882761a72a60649edff9a2478835325d084fb640ea32a975e29e12a012025f 2.30kB / 2.30kB                     0.0s
 => => extracting sha256:a8b1c5f80c2d2a757adc963e3fe2dad0b4d229f83df3349fbb70e4d12dd48822                          3.3s
 => [internal] load build context                                                                                  0.3s
 => => transferring context: 3.73MB                                                                                0.3s
 => [2/9] RUN apt update                                                                                          31.7s
 => [3/9] RUN apt install -yy build-essential clang gcc make cmake                                                76.9s 
 => [4/9] COPY . print/                                                                                            0.7s 
 => [5/9] WORKDIR print                                                                                            0.1s 
 => [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install                       75.3s 
 => [7/9] RUN cmake --build _build                                                                                 2.5s 
 => [8/9] RUN cmake --build _build --target install                                                                0.9s 
 => [9/9] WORKDIR _install/bin                                                                                     0.1s 
 => exporting to image                                                                                            11.2s 
 => => exporting layers                                                                                           11.2s 
 => => writing image sha256:9653a2a1e9cc19df51ff0bd2dba13307c552f8e3de76c4f5d543dd3892aa5dab                       0.0s 
 => => naming to docker.io/library/logger               
```

```sh
❯ sudo docker images 
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
logger       latest    9653a2a1e9cc   5 minutes ago   1.23GB

❯ sudo docker run -it -v "$(pwd)/logs/:/home/logs/" logger 
text1
text2
text3
^C%  
```

```sh
sudo docker inspect logger
[
    {
        "Id": "sha256:9653a2a1e9cc19df51ff0bd2dba13307c552f8e3de76c4f5d543dd3892aa5dab",
        "RepoTags": [
            "logger:latest"
        ],
        "RepoDigests": [],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2024-05-17T22:34:26.60604484+03:00",
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LOG_PATH=/home/logs/log.txt"
            ],
            "Cmd": null,
            "Image": "",
            "Volumes": {
                "/home/logs": {}
            },
            "WorkingDir": "/print/_install/bin",
            "Entrypoint": [
                "/bin/sh",
                "-c",
                "./demo"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "22.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 1234307530,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/vhawc56j4w5zz2ow8pva1lo5h/diff:/var/lib/docker/overlay2/s79ydpuzk358dfep6tvdwcbfq/diff:/var/lib/docker/overlay2/e7aer8blymmc25hvxtegues1c/diff:/var/lib/docker/overlay2/ricm4q7u76hggbthgpz4eygn5/diff:/var/lib/docker/overlay2/j70d9dxhjmk0mj8ibd7r86eye/diff:/var/lib/docker/overlay2/zl1fwbht067yer2edlp6ts2kv/diff:/var/lib/docker/overlay2/bhojzlpmk720u5vykybkrsvcb/diff:/var/lib/docker/overlay2/0c87d932a038ccfa4d27a56ba34b86fa7e770b72cc33689dd803f559b1ab17b2/diff",
                "MergedDir": "/var/lib/docker/overlay2/u2wro0orbbrunm7jy8zrh86x6/merged",
                "UpperDir": "/var/lib/docker/overlay2/u2wro0orbbrunm7jy8zrh86x6/diff",
                "WorkDir": "/var/lib/docker/overlay2/u2wro0orbbrunm7jy8zrh86x6/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:629ca62fb7c791374ce57626d6b8b62c76378be091a0daf1a60d32700b49add7",
                "sha256:fbcc3de4b98dda3de0c52c6926a0eed34c5a6a313fe83bcb98131385f6bece45",
                "sha256:b068f4fd9690c630568b72a8544a3b78a70730373c3bc6ca5c5a140462f6eb6f",
                "sha256:ead7383a1effd9ad505b75723157de603fde59f0185f1d721e2aa838c41da7b9",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef",
                "sha256:80095eba055ae3309bc3974b048a1b306ccfb643ce0ebbc96e1d9a05ac2a8d71",
                "sha256:5ae95ee46d574c028642ebc6582d32867a5bc44cbe5ab0999b2429fad27ae272",
                "sha256:47675de98a882f300486de3f2b670f467ff9a72bc743f2ae8c1eb22c949545d9",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef"
            ]
        },
        "Metadata": {
            "LastTagTime": "2024-05-17T22:34:37.832290524+03:00"
        }
    }
]
```

```sh
❯ cat logs/log.txt 
text1
text2
text3
```

```sh
 sed -i 's/lab07/lab08/g' README.md 
```

```sh
❯ nvim .travis.yml

❯ git add Dockerfile 

❯ git add .travis.yml 

❯ git commit -m "adding Dockerfile" 
[main e769d73] adding Dockerfile
 2 files changed, 23 insertions(+), 14 deletions(-)
 create mode 100644 Dockerfile

❯ git push origin main
Перечисление объектов: 97, готово.
Подсчет объектов: 100% (97/97), готово.
При сжатии изменений используется до 12 потоков
Сжатие объектов: 100% (50/50), готово.
Запись объектов: 100% (97/97), 58.42 КиБ | 14.60 МиБ/с, готово.
Total 97 (delta 35), reused 92 (delta 34), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (35/35), done.
To github.com:SofiaBachulashvili/tp-lab08.git
 * [new branch]      main -> main
```
