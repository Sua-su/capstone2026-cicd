# 1. 빌드 단계
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# 2. 실행 단계
FROM nginx:stable-alpine
# 기존 빌드 파일 복사
COPY --from=build /app/build /usr/share/nginx/html
# Nginx 설정 파일 덮어쓰기 (추가된 부분)
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]