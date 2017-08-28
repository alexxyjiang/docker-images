FROM nginx:stable
MAINTAINER Alex, Jiang <alexxyjiang@gmail.com>

COPY ./SIGIR2017    /usr/share/nginx/html/SIGIR2017
COPY ./default.conf /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
