FROM node:14-bullseye-slim

ENV LANG zh_CN.UTF-8

RUN ln -sf /usr/share/zoneinfo/PRC /etc/localtime \
  && apt-get -y update \
  && apt-get install -y curl gnupg2 libxss1 locales \
  && sed -ie 's/# zh_CN.UTF-8 UTF-8/zh_CN.UTF-8 UTF-8/g' /etc/locale.gen \
  && locale-gen \
  && mkdir -p /usr/share/fonts/truetype/SourceHanSerifCN/ \
  && curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
  && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
  && apt-get -y update \
  && apt-get install -y google-chrome-stable \
  && rm -rf /var/lib/apt/lists/*

COPY SourceHanSerifCN*.otf /usr/share/fonts/truetype/SourceHanSerifCN/

CMD [ "node" ]
