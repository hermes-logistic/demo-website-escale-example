FROM node:20.11.1-alpine3.19 as build
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:1.25.4-alpine3.18
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80