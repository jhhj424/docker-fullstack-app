FROM node:alpine as builder
WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx
EXPOSE 3000
# 컨테이너 안에 위치한 /etc/nginx/conf.d/default.conf 파일을 지정한 ./nginx/default.conf 파일로 대체
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html