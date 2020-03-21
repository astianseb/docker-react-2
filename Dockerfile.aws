FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
#EXPOSE is required for ElasticBeanstalk to know the port
EXPOSE 80
COPY --from=builder /app/build /usr/share/nginx/html
#ngnix will start automatically