FROM node:8
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install --production
COPY . .
EXPOSE 8082
CMD ["node", "server.js"]
