FROM maven:3.9.11-eclipse-temurin-8-alpine AS build
WORKDIR /opt/shipping
COPY appcode/ ./
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar



FROM maven:3.9.11-eclipse-temurin-8-alpine
EXPOSE 8080/tcp
WORKDIR /opt/shipping
COPY --from=build /opt/shipping /opt/shipping/
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /opt/shipping
USER roboshop
CMD ["java", "-jar", "shipping.jar"]












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
