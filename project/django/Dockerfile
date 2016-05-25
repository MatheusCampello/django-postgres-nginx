FROM centos:7

ENV django 1.0

RUN yum -y update \
	&& yum -y install epel-release \
	&& yum -y install python-pip \
	&& yum -y install gcc \
	&& yum -y install python-devel \
	&& yum -y install postgresql-devel \
	&& mkdir -p /opt/src/app \
	&& pip install --upgrade pip \
	&& pip install django==1.9.2 \
	&& pip install gunicorn==19.6.0 \
	&& cd /opt/src/app \
	&& django-admin startproject tsc

RUN pip install psycopg2

WORKDIR /opt/src/app/tsc

ADD settings.py /opt/src/app/tsc/tsc

EXPOSE 8000

RUN python manage.py collectstatic --noinput

VOLUME /opt/src/app/tsc/static

ENTRYPOINT ["gunicorn", "tsc.wsgi:application", "-b"]

CMD ["0.0.0.0:8000"]
