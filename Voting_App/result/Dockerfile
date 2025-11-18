FROM node:18-slim

RUN useradd -m toka

WORKDIR /app

COPY package.json package-lock.json* ./
RUN npm install

COPY . .

RUN chown -R toka:toka /app
USER toka

ENV PORT=8081

EXPOSE 8081

CMD ["node", "server.js"]
