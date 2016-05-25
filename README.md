# django-postgres-nginx

Para criar as imagens, rodar os comandos:

cd project/postgres
docker build -t postgres:1.0 .

cd project/django
docker build -t django:1.0 .

cd project/nginx
docker build -t django:1.0 .


Para criar os containers rodando o projeto, fazer os seguintes comandos após criar as imagens:

docker create -v /var/lib/postgresql --name dbdados postgres:1.0 /bin/true

docker run -d -p 5432:5432 --volumes-from dbdados --name postgres postgres:1.0

docker run -d --link postgres:db --name django django:1.0

docker run -d -p 80:80 --volumes-from django --link django:django --name nginx nginx:1.0




OU baixando as imagens pelo docker hub.

docker create -v /var/lib/postgresql --name dbdados matheuscampello/postgres:1.0 /bin/true

docker run -d -p 5432:5432 --volumes-from dbdados --name postgres matheuscampello/postgres:1.0

docker run -d --link postgres:db --name django matheuscampello/django:1.0


Com isso, da para abrir o navegador e visualizar a página de boas vindas do django/nginjx http://localhost:80
