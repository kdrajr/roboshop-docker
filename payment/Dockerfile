FROM python:3.9.25-alpine3.22 AS build
WORKDIR /opt/payment
# uWSGI build prerequisites
RUN apk add --no-cache \
    build-base \
    linux-headers \
    pcre-dev 
COPY appcode/requirements.txt ./
RUN pip3 install --no-cache-dir -r requirements.txt



FROM python:3.9.25-alpine3.22
EXPOSE 8080/tcp
WORKDIR /opt/payment
LABEL com.project="roboshop" \
      component="payment" \
      created_by="Dheeraj"
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
COPY --from=build /usr/local /usr/local
# Runtime deps only
RUN apk add --no-cache pcre
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
COPY --chown=roboshop:roboshop appcode/ /opt/payment/
USER roboshop
ENTRYPOINT ["uwsgi"]
CMD ["--ini", "payment.ini"]











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
