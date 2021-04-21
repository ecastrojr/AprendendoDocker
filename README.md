# AprendendoDocker

Anotações e arquivos sobre Docker

Adicionado Vagrantfile para criar ambiente docker em uma VM Alpine Linux


Comandos Utilizados:

# curl -fsSL https://get.docker.com/ | bash
    Instalação Automatizada
# docker version
    Testar e verificar a versão
# docker container ls
    Lista os containers em execução
# docker container run hello-world
    Inicia um container de teste
# docker image ls
    Lista as imagens
# docker ps
    Comando antigo para listar os containers
# docker container ls -a
    Lista todos os containers
# docker container run -ti centos:7
    Inicia um container centos 7 em modo interativo e TTY
# docker container run -ti ubuntu
    Inicia um container centos 7 em modo interativo e TTY
# docker container -d nginx
    Inicia um container nginx em modo deamon
# docker container attach [CONTAINER ID]
    Reconecta em um container em execução
# docker container exec -ti [CONTAINER ID] [COMANDO]
    Executa um comando em um containet em modo interativo
# docker container start [CONTAINER ID]
    Inicia um container
# docker container stop [CONTAINER ID]
    Para um container
# docker container restart [CONTAINER ID]
    Reinicia um container
# docker container pause [CONTAINER ID]
    Pausa um container
# docker container unpause [CONTAINER ID]
    Despausa um container
# docker container inspect [CONTAINER ID]
    Mostra todas as especificações e detalhes do container
# docker container logs -f [CONTAINER ID]
    Vizualiza os logs, funcionam parecido com o tail -f
# docker container rm [CONTAINER ID]
    Deleta um container parado
# docker container rm -f [CONTAINER ID]
    Força o delete de um container, em execução ou não.
# CTRL + P + Q
    Sai de um TTY interativo sem parar o container
# docker container attach [CONTAINER ID]
    Reconecta em um determenidado container em execução
# docker container stats [CONTAINER ID]
    Exibe informações de desempenho do container
# docker container top [CONTAINER ID]
    Exibe os processos do container
# docker container run -d -m 128M --cpus 0.5 nginx
    Inicia um container nginx como deamon e limite de uso de memória e cpu
# docker container update --memory 64M --cpus 0.4 nginx
    Atualiza as especificações de limites de memória e cpus

Comando executados dentro do container para testar os limites e monitoramento da CPU e MEM:
# apt-get update
# apt-get install stress
# stress --cpu 1 --vm-bytes 128M --vm 1

Contruindo o primeiro DockerFile

No Dockerfile:

FROM debian 
LABEL app="Giropops" 
ENV JEFERSON="LINDO" 
RUN apt-get update && apt-get install -y stress && apt-get clean 

CMD stress --cpu 1 --vm-bytes 64M --vm1

dentro do diretório onde está o dockerfile: 

# docker image build -t toskeira:1.0 .
Cria a imagem do container baseada no dockerfile

# docker image ls
Lista todas as imagens do servidor
# docker container run -d toskeira:1.0
Inicia a imagem criada como deamon 
