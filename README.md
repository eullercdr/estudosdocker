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

## Volumes
docker volume ls (Lista todos os volumes criados) 
docker volume create --driver local --opt type=none --opt device=//d//estudos//docker --opt o=bind nomevolume  
docker volume inspect nomevolume (lista os dados do volume)  
docker create volume nomevolume (cria um volume local)  
docker run -v "pathlocal:pathcontainer" image (Criando um volume)  
docker run -v -p portalocal:portacontainer "pathlocal:pathcontainer" image (Criando um volume) 
docker inspect id-container (mostra as informações do container)  

## Commit and Push Docker
docker commit hashcointainer eullercristian/nginx-commit  
docker commit hashcointainer eullercristian/nginx-commit:v2 (Versiona a imagem)    

## Docker File
docker build -f Dockerfile -t eullercristian/node . (Buildando através de docker file)  

## Docker Hub
docker push eullercristian/node (subindo a imagem)    
docker pull eullercristian/node (baixando a imagem)  

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
