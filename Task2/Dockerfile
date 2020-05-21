FROM ubuntu:18.04
LABEL maintainer="novikov.dima@gmail.com"
RUN apt-get update -y && apt-get upgrade -y \
    && apt-get install nginx -y && apt-get clean -y
COPY default /etc/nginx/sites-available
EXPOSE 8000
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
