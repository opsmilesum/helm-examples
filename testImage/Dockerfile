# My test image
# Run docker build -t testimage:V1 testimage
FROM ubuntu

MAINTAINER pony pony@gmail.com

FROM nginx
RUN echo '这是一个本地构建的nginx镜像' > /usr/share/nginx/html/index.html

CMD /usr/sbin/nginx