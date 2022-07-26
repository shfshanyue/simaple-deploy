# 使用 Docker 部署前端之简单版

+ [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
+ [Compose file Reference](https://docs.docker.com/compose/compose-file/compose-file-v3/)

## 本地版

使用 [serve](https://github.com/vercel/serve) 在本地起一个静态服务器

``` bash
$ npx serve .
```

或者，使用 node.js 直接写一个服务，在本地起一个静态服务器

``` bash
$ node server-fs.js
```

## 琐碎版: docker cli

使用 `docker` 命令行工具去构建及运行容器

``` bash
# 构建一个名为 simple-app 的镜像
$ docker build -f node.Dockerfile -t simple-node-app .

# 根据该镜像运行容器
$ docker run -d --rm -p 3000:3000 simple-node-app
```

## nginx版: docker cli

使用 `docker` 命令行工具去构建及运行容器

``` bash
# 构建一个名为 simple-app 的镜像
$ docker build -f nginx.Dockerfile -t simple-nginx-app .

# 根据该镜像运行容器
$ docker run -d --rm -p 3000:80 simple-nginx-app
```
## 高效版: docker-compose

使用 `docker-compose` 运行容器，同时部署 node 版与 nginx 版

``` bash
$ docker-compose up --build
```

## Nginx 学习版

通过该配置文件可以在容器中学习 nginx，不再受限于宿主环境。

**学习 nginx 请先进入 [learn-nginx](https://github.com/shfshanyue/simple-deploy/tree/master/learn-nginx) 目录。**

API 文档置于 [learn nginx by docker](https://www.apifox.cn/apidoc/project-1264553/api-28699589/shanyue)，可使用 [Apifox](https://www.apifox.cn/a1shanyue) 直接打开。

在学习过程修改了配置文件后，可重启容器进行更新。

### location

``` bash
$ docker-compose up location

$ docker-compose up location2 api
```

### proxy

``` bash
$ docker-compose up proxy
```
