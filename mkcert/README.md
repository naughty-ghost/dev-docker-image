# mkcert docker image
mkcertを実行するイメージ  
https://github.com/FiloSottile/mkcert  


# pull
[repository](https://github.com/naughty-ghost/mkcert/pkgs/container/mkcert)  
Pull image from the command line:
```
docker pull ghcr.io/naughty-ghost/mkcert:0.1.0
```
Use as base image in Dockerfile:
```
FROM ghcr.io/naughty-ghost/mkcert:0.1.0
```
# usage
`/home/user/mkcert-tool/Cert`は、保存したいパスに置き換える。`localhost`は発行したいドメインに置き換える。
```
docker run -it -v /home/user/mkcert-tool/Cert:/Cert $(IMAGE_NAME):latest /bin/bash -c "mkcert localhost"
```