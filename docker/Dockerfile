### STAGE 1: Build ###
FROM node:latest AS build
WORKDIR /pblog
COPY ../pblog/package.json ../pblog/package-lock.json ./
RUN npm install
COPY ../pblog .
RUN npm run build


### STAGE 2: Run ###
FROM nginx:latest
COPY ./docker/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build ./pblog/dist/pblog/browser /usr/share/nginx/html
