FROM node:20-alpine3.21 AS build
WORKDIR /opt/cart
COPY server.js package.json ./
RUN npm install


FROM node:20-alpine3.21
EXPOSE 8080/tcp
WORKDIR /opt/cart
LABEL com.project="roboshop" \
      component="cart" \
      created_by="Dheeraj"
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
COPY --from=build --chown=roboshop:roboshop /opt/cart /opt/cart/
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
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
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# CMD ["node", "server.js"]