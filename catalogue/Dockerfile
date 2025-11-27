FROM node:20-alpine3.21 AS build
WORKDIR /opt/catalogue
COPY server.js package.json ./
RUN npm install


FROM node:20-alpine3.21
EXPOSE 8080/tcp
WORKDIR /opt/catalogue
LABEL com.project="roboshop" \
      component="catalogue" \
      created_by="Dheeraj"
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
#creating system user and system group to run catalogue application
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
COPY --from=build --chown=roboshop:roboshop /opt/catalogue /opt/catalogue
USER roboshop
ENTRYPOINT ["node"]
CMD ["server.js"]















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