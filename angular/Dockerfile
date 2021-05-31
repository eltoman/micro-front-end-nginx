FROM node:16.2.0 as build

WORKDIR /app

COPY . .

RUN npm ci --silent
RUN npm run build -- --deployUrl /angular/

# Starting NGINX
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/angular /usr/share/nginx/html