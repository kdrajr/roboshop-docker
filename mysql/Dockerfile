FROM mysql:8
RUN mysql_secure_installation --set-root-pass RoboShop@1
COPY db/ /docker-entrypoint-initdb.d/
