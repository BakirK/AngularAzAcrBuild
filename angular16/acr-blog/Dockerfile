FROM node:20-alpine AS build
WORKDIR /app
COPY ["package.json", "./"]
COPY ["package-lock.json", "./"]
RUN npm install
COPY ["./", "./"]
RUN npm run build

FROM nginx:latest
COPY ["nginx.conf", "/etc/nginx/conf.d/default.conf"]
COPY --from=build /app/dist/acr-blog /usr/share/nginx/html
EXPOSE 8080