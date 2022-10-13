# 常见的多阶段组合的镜像

初始镜像主要用于中间过渡的build。

### Maven+Java Apps
```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps
```
### Java Compile
```
FROM openjdk:8-jre-alpine

# JAR_FILE is an argument value from the maven representation.
ARG JAR_FILE
# copy JAR into image
COPY target/${JAR_FILE} /app.jar 

EXPOSE 8800
# run application with this command line 
CMD ["/usr/bin/java", "-jar", "-Dspring.profiles.active=default", "/app.jar"]
```
### Go Apps+Alpine
```dockerfile
FROM golang:alpine3.16 as builder

RUN apk git \
&& export GOPROXY=https://proxy.golang.com.cn,direct \
&& GO111MODULE=on go install git@github.com:/jaeles-project/gospider@latest

FROM alpine:3.16
RUN apk --no-cache add bash git openssh-client ca-certificates bind-tools

COPY --from=builder /go/bin/gospider  /usr/local/bin/gospider

ENTRYPOINT ["gospider"]

CMD ["-h"]
```

### React example
```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```
