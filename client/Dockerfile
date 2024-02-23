# Этап 1: сборка приложения
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Этап 2: запуск приложения
FROM node:20-alpine
WORKDIR /app
COPY --from=build /app/dist ./dist
RUN npm install -g http-server
EXPOSE 8080
CMD [ "http-server", "dist" ]
