FROM node:19-alpine3.16 as build

RUN apk update && \
    apk add git && \
    npm i -g vite@latest

WORKDIR /app

RUN npm create vite@latest . -- --template svelte-ts && \
    # sed -i -e 's/Vite + Svelte/Welcome/g' ./src/App.svelte && \
    npm i && \
    vite build --base=/svelte/


# Starting NGINX
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist /usr/share/nginx/html