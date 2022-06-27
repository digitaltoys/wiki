### 도커에 node 돌리기
https://withhamit.tistory.com/159
```docker
# install NODE
FROM node:lts-alpine as build-stage
WORKDIR /homepage
COPY package*.json ./
 
ARG script 
RUN npm install
COPY . .
RUN npm run $script
 
FROM nginx:stable-alpine as production-stage
RUN rm /etc/nginx/conf.d/default.conf
COPY  ./nginx/homepage.conf /etc/nginx/conf.d/homepage.conf
 
COPY --from=build-stage ./homepage/dist /usr/share/nginx/html/homepage
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Docker v17.06.0-ce에 도입된 multi-stage 빌드 사용하기
https://blog.outsider.ne.kr/1300
```docker
# bulid stage
FROM golang:1.8.3 AS build
MAINTAINER Outsider

ENV VAULT_VERSION=0.7.3

## clone vault source code
WORKDIR /go/src/github.com/hashicorp
RUN git clone https://github.com/hashicorp/vault.git

## build vault
WORKDIR /go/src/github.com/hashicorp/vault
RUN git checkout v"${VAULT_VERSION}"
RUN make bootstrap
RUN make dev

# final stage
FROM debian:jessie
MAINTAINER Outsider

## copy vault from build
COPY --from=build /go/src/github.com/hashicorp/vault/bin/vault /bin/

CMD ["vault", "server", "-dev"]
```
위 파일에는 기존과 다른 점이 있다.

FROM이 2번 존재한다. 앞에서는 vault를 빌드하는 환경이고 두 번째 FROM이 최종 이미지를 만드는 부분이다.  
첫 FROM에는 FROM golang:1.8.3 AS build처럼 별칭을 지정했다. 이는 나중에 사용하기 위함이다.  
최종 이미지를 만들기 위해서 FROM debian:jessie을 사용했다.  
COPY --from=build /go/src/github.com/hashicorp/vault/bin/vault /bin/처럼 앞에서 build로 지정한 환경에서 파일을 가져와서 최종 이미지에 파일을 추가한다.  
