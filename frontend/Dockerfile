FROM node:16 as build-stage
WORKDIR /app
ADD . .
RUN yarn install
RUN yarn build

FROM nginx:stable-alpine as production-stage
#컨테이너 안에 nginx.conf를 옆 해당겨로에 옮겨준다.
COPY  ./nginx/nginx.conf /etc/nginx/conf.d/default.conf 

COPY --from=build-stage /app/build /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]