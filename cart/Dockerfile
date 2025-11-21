FROM node:20
EXPOSE 8080
RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
USER roboshop
WORKDIR /opt/app
COPY server.js package.json ./
RUN npm install
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
CMD ["node", "server.js"]