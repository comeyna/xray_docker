## xray_docker

使用一键脚本安装.



## 一键安装 xray_reality

```
EXTERNAL_PORT=2333 && docker run -d --name xray_reality --restart=always --log-opt max-size=100m --log-opt max-file=3 -p $EXTERNAL_PORT:443 -e EXTERNAL_PORT=$EXTERNAL_PORT raye2025/reality:v25.8.3 && sleep 3 && docker exec -it xray_reality cat /config_info.txt
```



## 一键安装 xray_xhttp_reality




## 基础使用方法

安装 docker 与 docker compose

```
curl -fsSL https://get.docker.com | bash -s docker
curl -L "https://github.com/docker/compose/releases/download/v2.39.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker -v
docker-compose --version
```


