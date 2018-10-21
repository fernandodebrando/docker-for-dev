Demonstrações da apresentação Docker para desenvolvedores


Passo a passo:

1 - CRIAR DOCKERFILE, CRIAR IMAGEM, PUBLICAR IMAGEM E SUBIR UM CONTAINER

- Cria Dockerfile
.php/Dockerfile

- Executa comando para criar imagem
$ docker build -t minhaimagemsenac . 

- Listar Docker images 
$ docker images

- Publicar imagem no docker hub
$ docker tag minhaimagemsenac fernandosilva/minhaimagemsenac

$ docker push fernandosilva/minhaimagemsenac

- Executa container com base na imagem criada
$ docker run -d -p 8081:80 -v /home/fsilva/Documents/dev/demo/docker_developer/php/www:/var/www/html minhaimagemsenac
localhost:8081

2 - CRIAR DOCKER-COMPOSE E SUBIR CONTAINERS DE SERVIÇO WEB E DB

- WordPress, PHP, MySQL
$ docker-compose up -d
Acessar localhost:8000

3 - DOCKER SWARM - https://labs.play-with-docker.com/

O comando para inicializar o cluster:
$ docker swarm init --advertise-addr “ip_da_instância”

O comando para adiconar um worker ao cluster:
$ docker swarm join --token ****

O comando para pegar o Token para adicionar outro manager:
$ docker swarm join-token manager

O comando para pegar o Token para adicionar outro worker:
$ docker swarm join-token worker

O comando para listar os nodes:
$ docker node ls

4 - DOCKER STACK COM UMA APLICAÇÃO WORDPRESS
Inicio o Docker Swarm
docker swarm init

Faz deploy da stack conforme yml
docker stack deploy -c docker-compose.yml wordpress

Exibe os serviços da stack criada
docker stack services wordpress
docker stack ls

Acessa o sistema WordPress
http://127.0.0.1:8000/

Acessa o visualizador do cluster
http://127.0.0.1:8001/
