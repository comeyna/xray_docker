## docker_reality

### 懒人一键安装

```
EXTERNAL_PORT=2333 && docker run -d --name xray_reality --restart=always --log-opt max-size=100m --log-opt max-file=3 -p $EXTERNAL_PORT:443 -e EXTERNAL_PORT=$EXTERNAL_PORT raye2025/reality:v25.8.3 && sleep 3 && docker exec -it xray_reality cat /config_info.txt
```
