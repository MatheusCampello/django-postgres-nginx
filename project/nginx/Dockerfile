FROM centos:6.7

ENV nginx_centos-2 1.0

ADD nginx.repo /etc/yum.repos.d/

RUN yum install -y nginx

ADD nginx.conf /etc/nginx

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
