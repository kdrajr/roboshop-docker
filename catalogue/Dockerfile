FROM node:20-alpine3.21 AS build
EXPOSE 8080/tcp
RUN adduser -D -G roboshop roboshop
RUN addgroup -S roboshop && adduser -S -h /opt/catalogue -G roboshop roboshop
USER roboshop
WORKDIR /opt/catalogue
COPY server.js package.json ./
RUN npm install


FROM node:20-alpine3.21
WORKDIR /opt/catalogue
COPY --from=build /opt/catalogue ./
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]


















# FROM node:20
# EXPOSE 8080/tcp
# RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
# USER roboshop
# WORKDIR /opt/app
# COPY server.js package.json ./
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]