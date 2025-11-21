FROM maven:3.9
EXPOSE 8080/tcp
RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
USER roboshop
WORKDIR /opt/app
COPY static/ ./
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar 
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD ["java", "-jar", "shipping.jar"]
