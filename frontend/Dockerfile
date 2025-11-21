FROM nginx:1.24
EXPOSE 80/tcp
RUN rm -rf /usr/share/nginx/html/*
RUN rm -rf /etc/nginx/nginx.conf
COPY nginx.conf  /etc/nginx/nginx.conf
COPY static/ /usr/share/nginx/html/
