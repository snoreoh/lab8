[![Build Status](https://travis-ci.com/snoreoh/lab8.svg?branch=master)](https://travis-ci.com/snoreoh/lab8)

# Homework. Lab #8

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
