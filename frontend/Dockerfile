FROM nginx:1.24.0 
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /user/share/nginx/html/*
COPY static /user/share/nginx/html/*
COPY nginx.conf /etc/nginx/nginx.conf
