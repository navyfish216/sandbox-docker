FROM paketobuildpacks/ubuntu-noble-run:latest

USER root

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    locales \
    subversion \
    unzip \
    curl zip unzip

ARG JAVA25_VERSION=25-open

# SDKMANをインストールして、sdkコマンドでjavaをインストールする
RUN curl -s "https://get.sdkman.io" | bash && \
    bash -c "source ${HOME}/.sdkman/bin/sdkman-init.sh && sdk install java ${JAVA25_VERSION}" && \
    cp -rp ${HOME}/.sdkman/candidates/java /

USER cnb

ENV JAVA_HOME=/java/${JAVA25_VERSION}
ENV PATH=${JAVA_HOME}/bin:${PATH}

# 動作確認用のコマンド実行
#CMD ["whoami"]
#CMD ["find", "/", "-name", "java"]
#CMD ["env"]
#CMD ["java", "-version"]
