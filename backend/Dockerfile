FROM node:18

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .

# your server.js uses PORT 4000
ENV PORT=4000
EXPOSE 4000

CMD ["node", "server.js"]
