FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000 
#ora ho due container nginx uno fa da router l'altro con porta 3000 da server che qui sto configurando
 
COPY ./nginx/default.conf  /etc/nginx/conf.d/default.conf 
COPY --from=builder /app/build /user/share/nginx/html