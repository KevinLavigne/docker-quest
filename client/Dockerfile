# build environment
FROM node:lts-alpine as builder

RUN mkdir /app
WORKDIR /app
COPY package.json package.json
RUN npm i
COPY public public
COPY src src
RUN npm run build

# production environment
FROM nginx:stable-alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]    
