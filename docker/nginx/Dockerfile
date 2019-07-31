FROM nginx:mainline-alpine
LABEL maintainer="yokotak0527 <454935+yokotak0527@users.noreply.github.com>"

# ユーザー追加
ARG USER_NAME
ARG USER_UID

RUN adduser ${USER_NAME} -u ${USER_UID} -D

# 一時ファイル追加
COPY tmp/* /tmp/

# リモートリポジトリのアップデート
RUN apk update --no-cache

# サーバータイムゾーン変更
RUN apk add --no-cache tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# nginx設定テンプレートを出力して追加
RUN envsubst < /tmp/nginx.conf > /etc/nginx/nginx.conf
