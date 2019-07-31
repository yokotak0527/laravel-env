FROM  mysql:8.0.15
LABEL maintainer="yokotak0527 <454935+yokotak0527@users.noreply.github.com>"

# conf.d/以下の設定ファイルを全て追加
COPY conf.d/* /etc/mysql/conf.d/

# サーバーのタイムゾーンをJSTに変更
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
