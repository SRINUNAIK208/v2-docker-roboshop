FROM node:20-alpine3.22 as builder
WORKDIR /opt/app
COPY package.json .
COPY server.js .
RUN npm install

FROM node:20-alpine3.22
WORKDIR /opt/app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder --chown=roboshop:roboshop /opt/app .
USER roboshop
CMD ["node", "server.js"]
