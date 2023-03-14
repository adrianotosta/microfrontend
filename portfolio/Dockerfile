FROM node:19-alpine3.16 as build

RUN apk update && \
    apk add git && \
    npm i -g vite@latest

WORKDIR /app

RUN git clone --branch feature/vuejs https://github.com/adrianotosta/portfolio.git . && \
    npm i && \
    vite build


# Starting NGINX
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/docs /usr/share/nginx/html