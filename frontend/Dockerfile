FROM nginx:1.29-alpine
EXPOSE 80/tcp
LABEL com.project="roboshop" \
      component="frontend" \
      created_by="Dheeraj"
RUN rm -rf /usr/share/nginx/html/* && \
    rm -rf /etc/nginx/nginx.conf && \
    rm -rf /etc/nginx/conf.d/default.conf
COPY nginx.conf  /etc/nginx/nginx.conf \
     static/ /usr/share/nginx/html/














# FROM nginx:1.24

