# builder
FROM golang:alpine AS builder
LABEL version="25.8.3"

WORKDIR /app

RUN apk add --no-cache git curl jq && \ 
    LATEST_VERSION_TAG=$(curl -s https://api.github.com/repos/XTLS/Xray-core/releases | jq -r '.[0].tag_name') && \
    git clone https://github.com/XTLS/Xray-core.git . && \
    git checkout $LATEST_VERSION_TAG && \
    go mod download -x && \
    go build -v -o xray /app/main/

# runner
FROM alpine:latest AS runner


ENV UUID=""
ENV DEST=""
ENV SERVERNAMES=""
ENV PRIVATEKEY=""
ENV SHORTIDS=""
ENV NETWORK=""
ENV INTERNAL_PORT=""
ENV HOSTMODE_PORT=""
ENV TZ=Asia/Shanghai

WORKDIR /

COPY ./entrypoint.sh /
COPY ./config.json /

COPY --from=builder /app/xray /

# dlc.dat 是一个域名分类数据库，在 V2Ray/Xray 中用于实现 按域名分组的智能路由，如：访问国内网站直连，访问国外服务走代理。
# geoip.dat 是 V2Ray/Xray 用来判断一个 IP 是哪个国家的工具，配合路由规则，实现“国外走代理，国内直连”的智能分流。
# wget -O /geosite.dat https://github.com/v2fly/domain-list-community/releases/latest/download/dlc.dat && \
# wget -O /geoip.dat https://github.com/v2fly/geoip/releases/latest/download/geoip.dat && \

RUN apk add --no-cache tzdata ca-certificates jq curl libqrencode-tools && \
    mkdir -p /var/log/xray && \
    chmod +x /entrypoint.sh

ENTRYPOINT ["./entrypoint.sh"]
EXPOSE 443
