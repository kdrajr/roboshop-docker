FROM maven:3.9.11 AS build
WORKDIR /opt/shipping
COPY appcode/ ./
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar



FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080/tcp
WORKDIR /opt/shipping
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
COPY --from=build --chown=roboshop:roboshop /opt/shipping/shipping.jar ./
USER roboshop
ENTRYPOINT ["java"]
CMD ["-jar", "shipping.jar"]












# FROM maven:3.9
# EXPOSE 8080/tcp
# RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
# USER roboshop
# WORKDIR /opt/app
# COPY appcode/ ./
# RUN mvn clean package && \
#     mv target/shipping-1.0.jar shipping.jar 
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]
