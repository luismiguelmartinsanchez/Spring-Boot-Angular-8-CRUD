FROM nginx:alpine
 
EXPOSE 80
# EXPOSE 443
 
COPY ./nginx.conf /etc/nginx/nginx.conf
#COPY ./nginx.ssl.conf /etc/nginx/nginx.conf

WORKDIR /usr/share/nginx/html/

RUN mkdir taller

COPY ./dist/frontend-angular/ /usr/share/nginx/html/taller/

# WORKDIR /etc/

# RUN mkdir pki && mkdir pki/nginx && mkdir pki/nginx/private

# COPY ./pki/ /etc/pki/