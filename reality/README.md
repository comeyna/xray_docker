## 构建镜像

```
# 查看 xray 版本
curl -s https://api.github.com/repos/XTLS/Xray-core/releases | jq -r '.[0].tag_name'
# 镜像名
echo "raye2025/xray_reality:$(curl -s https://api.github.com/repos/XTLS/Xray-core/releases | jq -r '.[0].tag_name')"

docker build -t xray:reality .
docker tag xray:reality raye2025/xray_reality:v25.8.3

# 登录
docker login -u raye2025 -p passwd
# 上传
docker push raye2025/xray_reality:v25.8.3
```
