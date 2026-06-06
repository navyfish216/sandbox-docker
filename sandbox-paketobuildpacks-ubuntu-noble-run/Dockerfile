FROM paketobuildpacks/ubuntu-noble-run:latest

USER root

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y wget

# JREのインストールバージョンを指定
ARG JRE_FULL_VERSION=25.0.3+11
ARG JRE_VERSION=${JRE_FULL_VERSION%+*}

# JREインストール(GitHubのLibericaからダウンロードして解凍)
RUN wget https://github.com/bell-sw/Liberica/releases/download/${JRE_FULL_VERSION}/bellsoft-jre${JRE_FULL_VERSION}-linux-amd64.tar.gz && \
    tar -zxvf bellsoft-jre${JRE_FULL_VERSION}-linux-amd64.tar.gz

USER cnb

ENV JAVA_HOME=/jre-${JRE_VERSION}
ENV PATH=${JAVA_HOME}/bin:${PATH}

# 動作確認用のコマンド実行
#CMD ["whoami"]
#CMD ["find", "/", "-name", "java"]
#CMD ["env"]
#CMD ["java", "-version"]
