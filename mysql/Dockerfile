FROM mysql:8.0
LABEL com.project="roboshop" \
      component="mysql" \
      created_by="Dheeraj"
ENV MYSQL_ROOT_PASSWORD="RoboShop@1"
COPY db/ /docker-entrypoint-initdb.d/
#CMD ["sleep", "1000"]

