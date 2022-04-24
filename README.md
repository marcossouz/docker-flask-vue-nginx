# Docker (docker-compose) + Flask + VueJs + Nginx

Projeto de Estudos com integração entre as tecnologias Docker, Flask, VueJs e Nginx

## Para rodar todo o projeto no docker
> `docker-compose up -d`

## Api flask
> `localhost:8181`

## App vue (porta 80)
> `localhost`

### ações necessárias para funcionamento da aplicação
- `$ docker exec -it mongodb bash`
- `root@46ae1fe35928:/# mongo -u mongodbuser -p`
  - password: `pass-root`
- `> use flaskdb`
- `> db.createUser({user: 'flaskuser', pwd: 'pass-mongo', roles: [{role: 'readWrite', db: 'flaskdb'}]})`
- `> exit`
- `root@46ae1fe35928:/# mongo -u flaskuser -p pass-mongo --authenticationDatabase flaskdb`
  - Se logou com o novo usuário está funcionando.
- `> exit`
- 

### configurações no banco de dados da aplicacao

`docker exec -it mongodb bash`

### dentro do container mongodb

`mongo -u mongodbuser -p`
`password: pass-root`
`use flaskdb`
`db.createUser({user: 'flaskuser', pwd: 'pass-mongo', roles: [{role: 'readWrite', db: 'flaskdb'}]})`
`exit`
`mongo -u flaskuser -p pass-mongo --authenticationDatabase flaskdb`

# se logou esta ok
exit

#### comandos docker

docker-compose down
docker rm -f $(docker ps -a -q)
docker stop $(docker ps -a -q)
docker volume rm $(docker volume ls -q)
docker rmi $(docker images -q)  
docker-compose up -d

docker logs --tail 50 --follow --timestamps flask
docker logs --tail 50 --follow --timestamps webserver

#### Api urls
`curl -i http://localhost`
`curl -i -H "Content-Type: application/json" -X POST -d '{"todo": "Dockerize Flask application with MongoDB backend"}' http://localhost/todo`
`curl -i http://localhost/todo`
