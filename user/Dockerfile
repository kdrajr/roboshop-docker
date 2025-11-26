FROM node:20-alpine3.21 AS build
WORKDIR /opt/user
COPY server.js package.json ./
RUN npm install


FROM node:20-alpine3.21
EXPOSE 8080/tcp
WORKDIR /opt/user
LABEL com.project="roboshop" \
      component="user" \
      created_by="Dheeraj"
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
COPY --from=build --chown=roboshop:roboshop /opt/user /opt/user/
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
#     REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node", "server.js"]