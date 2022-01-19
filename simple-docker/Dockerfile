FROM node:12-alpine
LABEL maintainer="yuebing.ren"

ENV NODE_ENV production

WORKDIR /app
 
COPY ./ ./
RUN npm i -g npm@7 \
    && npm ci \
    && apk update \
    && apk add bash 
 
#  RUN npm config set registry https://registry.npmmirror.com/ \
#     && npm i -g npm@7 \
#     && npm install \
#     && sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
#     && apk update \
#     && apk add bash 
 
EXPOSE 8080
CMD [ "npm", "start" ]
