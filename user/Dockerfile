FROM node:20
EXPOSE 8080/tcp
RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
USER roboshop
WORKDIR /opt/app
COPY server.js package.json ./
RUN npm install
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
CMD ["node", "server.js"]