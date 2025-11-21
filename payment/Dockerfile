FROM python:3.14
EXPOSE 8080/tcp
RUN useradd --system --home /opt/app --shell /sbin/nologin --comment "roboshop system user" roboshop
USER roboshop
WORKDIR /opt/app
COPY static/ ./
RUN pip3 install -r requirements.txt
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
CMD ["/usr/local/bin/uwsgi", "--ini", "payment.ini"]
