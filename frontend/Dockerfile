FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm i && touch node_modules/.package-lock.json
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]
