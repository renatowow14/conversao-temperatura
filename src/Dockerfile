###############################################################
#Initial Image
FROM node:14.17.5 as builder
WORKDIR /APP
LABEL maintainer="Renato Gomes <renatogomessilverio@gmail.com>"
COPY package*.json ./
RUN npm install 
COPY . .
EXPOSE 8080
CMD ["node", "server.js"]
###############################################################
#Final Image
FROM alpine:3.14 as runner 
RUN apk update && apk add --update nodejs
LABEL maintainer="Renato Gomes <renatogomessilverio@gmail.com>"
WORKDIR /APP
COPY --from=builder  /APP /APP
EXPOSE 8080
CMD ["node", "server.js"]
