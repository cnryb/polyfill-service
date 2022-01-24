FROM node:12-alpine as builder
LABEL maintainer="yuebing.ren"

WORKDIR /app
 
ARG POLYFILL_TAG='v4.43.1'
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add git \
    && git clone https://gitee.com/cnryb/polyfill-service.git . \
    && git checkout ${POLYFILL_TAG} \
    && rm -rf .git \
    && rm -rf .github

RUN yarn install --production


FROM node:12-alpine as runtime
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add --no-cache bash

WORKDIR /app
COPY --from=builder /app/ .
EXPOSE 8080
ENV NODE_ENV production
CMD [ "npm", "start" ]
