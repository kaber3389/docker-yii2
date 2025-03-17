# Используем официальный образ Nginx
FROM nginx:latest

###COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY ./app /var/www/html

RUN chown -R www-data:www-data /var/www/html && chmod -R 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html/web/assets && chmod -R 777 /var/www/html/web/assets

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
