[![Build Status](https://travis-ci.com/Berendei-Jr/lab08.svg?branch=main)](https://travis-ci.com/Berendei-Jr/lab08)

# Лабораторная работа №08 Лагов Сергей ИУ8-22

1. Указываем операционную систему

```
$ cat > Dockerfile <<EOF
FROM ubuntu:18.04
EOF
```

2. Просим *Docker* обновить систему и установить пакеты

```
$ cat >> Dockerfile <<EOF
RUN apt update
RUN apt install -yy gcc g++ cmake
EOF
```

3. Указываем на текущий каталог

```
$ cat >> Dockerfile <<EOF
COPY . print/
WORKDIR print
EOF
```

4. Собираем *CMake*

```
$ cat >> Dockerfile <<EOF
RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF
```


