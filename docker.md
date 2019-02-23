# Extract using docker


## From a centos vm

```bash
$ sudo yum install docker -y
$ sudo service docker start
$ sudo docker pull docker.io/haskell
$ sudo docker run -it --rm=true --entrypoint="/bin/sh" docker.io/haskell
```

## Inside the docker container

```bash
$ mkdir vagante
$ cd vagante
$ chmod a+wrx .
$ apt update
$ apt install wget
$ wget https://raw.githubusercontent.com/mtolly/vagante-extract/master/Main.hs
$ wget https://raw.githubusercontent.com/mtolly/vagante-extract/master/vagante-extract.cabal
$ stack init
$ stack install
```

## From a centos vm

```bash
$ sudo docker ps
# let's assume container id is 49339421c2d3 for docker.io/haskell
$ sudo docker cp ~/data.vra 49339421c2d3:/vagante/data.vra
```

## Inside the docker container

```bash
$ mkdir /extract
$ /root/.local/bin/vagante-extract extract /vagante/data.vra /extract
$ ls -laR /extract
```

## From a centos vm

```bash
$ cd ~ && mkdir data
$ sudo docker cp 49339421c2d3:/extract ~/data/
$ sudo tar -zcvf data.tar.gz ~/data
```
