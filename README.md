# docker-flask-vue-nginx

Para rodar todo o projeto no docker
> `docker-compose up -d`

Api flask
> `localhost:8181`

App vue (porta 80)
> `localhost`

ações necessárias para funcionamento da aplicação
  > - `$ docker exec -it mongodb bash`
  > - `root@46ae1fe35928:/# mongo -u mongodbuser -p`
  >   - password: `pass-root`
  > - `> use flaskdb`
  > - `> db.createUser({user: 'flaskuser', pwd: 'pass-mongo', roles: [{role: 'readWrite', db: 'flaskdb'}]})`
  > - `> exit`
  > - `root@46ae1fe35928:/# mongo -u flaskuser -p pass-mongo --authenticationDatabase flaskdb`
  >   - Se logou com o novo usuário está funcionando.
  > - `> exit`