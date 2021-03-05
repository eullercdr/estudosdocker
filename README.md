## Comandos DOCKER
docker ps (Verifica cointainers ativos)    
docker ps -a (Verifica containers não ativos)    
docker start id-container (Starta o container)   
docker stop id-container (Para o container)   
docker start -a -i id-container (Startar e entrar no modo bash)    
docker container prune (Remove todos os containers inativos)  
docker rm hashcontainer (Remove o container pelo hash)  
docker rm hashcointainer -f (Para e remove o container)  
docker rmi nomeimagem (Remove a imagem do container)  
docker run -d -P nomeimagem (Atrela as portas do container as portas do computador local)  
docker run -d -P --name [nome] imagedocker (Atribuir um nome ao container e atrelar as portas)    
docker run -d -p portlocal:portacontainer --name [nome] imagedocker   
docker run -d -P -e AUTHOR="BLABLA" imagedocker (Seta uma variavel de ambiente no docker)      
docker port id-container (Lista as portas utilizadas pelo container)  
docker ps -q (Retorna o hash dos containers)  
docker stop -t 0 $(docker ps -q) (Para todos os containers)    

## Mão na Massa
docker run -d nginx:latest  
docker run -d nginx:tag  
docker run -d --name my_nginx nginx:alpine  
docker run -d --name nginx_porta -p 8082:80 nginx:alpine  

## Mão na Massa Volumes
docker run -d --name my_nginx -p 8082:80 -v $(pwd):/usr/share/nginx/html nginx:alpine  

## Volumes
docker volume ls (Lista todos os volumes criados)   
docker volume inspect nomevolume (lista os dados do volume)  
docker create volume meuvolume (cria um volume local)  
docker run --name nginx -d --mount type=volume,source=meuvolume,target=/pasta nginx (cria um container nginx e usa um volume já criado anteriormente)
docker run --name nginx3 -d -v meuvolume:/app nginx (outra forma de atachar o volume)
docker volume prune (limpa dados que não estão sendo utilizados no volume)

## Acessar o container
docker exec -it my_nginx bash  
docker exec -it laravel apk add bash (add bash in cointainer alpines)  
docker exec -it my_nginx /bin/sh (windows)  

## Commit and Push Docker
docker commit hashcointainer eullercristian/nginx-commit  
docker commit hashcointainer eullercristian/nginx-commit:v2 (Versiona a imagem)    

## Docker File
docker build -f Dockerfile -t eullercristian/node . (Buildando através de docker file)  

## Docker Hub
docker push eullercristian/node (subindo a imagem)    
docker pull eullercristian/node (baixando a imagem)  

## Tipos de rede
**Bridge ** Rede default do docker, utilizada para que os containers se comuniquem  
**Host**  Mescla a network do docker com a network do host.  Possibilita que o container acesse portas do host e vice versa, sem a necessidade de expor portas.  
**Overlay** Permite que containers de maquinas diferentes se comuniquem, como se fosse a mesma rede.  
**NONE** Sem rede, container rodando de forma isolada   

## Criando redes
 docker network create --driver bridge minha-rede (criando uma rede no docker)  
 docker run -it --name ubuntu1 --network minha-rede ubuntu2 (colocando o container criado na rede)  
 docker network inspect minha-rede (inspecionando os containers conectados a rede) 
 docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM  
 
 ## Docker compose
  docker-compose build (Builda as imagens)  
  docker-compose up (Levanta as imagens)  
  
  ## Limpeza Docker
   docker rm -v $(docker ps -a -q -f status=exited) (Apagando containers que ja morreram)  
   docker rmi $(docker images -f dangling=true -q) (Apagando imagens soltas)  
   docker rmi $(docker images -q) (deletando todas as imagens)  
