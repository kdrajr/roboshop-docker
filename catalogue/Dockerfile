FROM node:20
RUN useradd roboshop
USER roboshop
WORKDIR /opt/app
COPY *.js *.json ./
RUN npm install
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]