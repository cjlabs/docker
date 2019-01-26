FROM nginx:latest
ADD nginx.conf /etc/nginx/
ADD sites.conf /etc/nginx/sites-enabled/default.conf

RUN apt-get update && apt-get install -y apt-utils 
#RUN ln -s /etc/nginx/sites-available/sites.conf /etc/nginx/sites-enable/sites
RUN usermod -u 1000 www-data
CMD ["nginx"]
EXPOSE 80 443
