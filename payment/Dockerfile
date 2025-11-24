FROM python:3.11-slim AS build
WORKDIR /opt/payment
COPY appcode/ ./
RUN pip3 install -r requirements.txt



FROM python:3.11-slim
EXPOSE 8080/tcp
WORKDIR /opt/payment
COPY --from=build /opt/payment /opt/payment/
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /opt/payment
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]











# FROM python:3.14
# EXPOSE 8080/tcp
# # RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
# # USER roboshop
# WORKDIR /opt/app
# COPY appcode/ ./
# RUN pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# CMD ["uwsgi", "--ini", "payment.ini"]
# # CMD ["sleep", "1000"]
