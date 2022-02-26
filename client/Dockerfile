FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package*.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx
# if the port is other than 80, we have to expose it manually
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
