# Stage 1. Build Angular app
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2. Use Nginx to serve Angular & proxy APIs
FROM nginx:alpine

# Copy compiled Angular dist files
COPY --from=build /usr/src/app/dist/angular-15-crud /usr/share/nginx/html

# Add reverse proxy config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
