FROM node:16-alpine AS build-angular
WORKDIR /app
COPY ./package.json /app
RUN npm install
COPY ./ /app
RUN npm run build --prod

# Direcciones de angular y nodejs en los files de la imagen
FROM nginx:1.17.1-alpine
WORKDIR /usr/share/nginx/html
#Direccion de archivos
COPY --from=build-angular dist/front64 .
# Puertos
EXPOSE 80

# Comando que inicia ambos servidores
CMD ["nginx", "-g", "daemon off;"]
