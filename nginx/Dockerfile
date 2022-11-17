FROM nginx:latest

RUN rm /etc/nginx/conf.d/default.conf
COPY default.conf /etc/nginx/conf.d
RUN rm /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx
EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
