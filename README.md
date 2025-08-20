## 介绍

修改 wulabing 代码后的产物.

## 懒人一键安装（reality） 

```
EXTERNAL_PORT=23500 && docker run -d --name reality_xtls --restart=always --log-opt max-size=100m --log-opt max-file=3 -p $EXTERNAL_PORT:443 -e EXTERNAL_PORT=$EXTERNAL_PORT raye2025/xray_reality:v25.8.3 && sleep 3 && docker exec -it reality_xtls cat /config_info.txt
```

## 停止并删除名为 reality_xtls 的 Docker 容器

```
docker stop reality_xtls && docker rm reality_xtls
```

## 安装 docker 与 docker compose

```
curl -fsSL https://get.docker.com | bash -s docker
curl -L "https://github.com/docker/compose/releases/download/v2.39.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker -v
docker-compose --version
```

## 参考

https://github.com/wulabing/xray_docker
