FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./

RUN npm install 

COPY . .

RUN npm run build

FROM httpd

COPY --from=build /app/dist/ /usr/local/apache2/htdocs/

EXPOSE 80

CMD ["httpd-foreground"]
