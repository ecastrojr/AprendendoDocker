# Dockerfiles


```bash
- git clone https....
- git add
- git commit
- git push
- git config
- git status
- git log
```


```bash
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80
```

```bash
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_DIR="/var/run/apache2"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]
```

```bash
package main
import "fmt"

func main() {
	fmt.Println("GIROPOPS STRIGUS GIRUS - LINUXTIPS")
}
```

```bash
FROM golang

WORKDIR /app
ADD . /app
RUN go build -o goapp
ENTRYPOINT ./goapp
```

```bash
FROM golang AS buildando

ADD . /src
WORKDIR /src
RUN go build -o goapp


FROM alpine:3.1

WORKDIR /app
COPY --from=buildando /src/goapp /app
ENTRYPOINT ./goapp
```

```bash
ADD => Copia novos arquivos, diretórios, arquivos TAR ou arquivos remotos e os adicionam ao filesystem do container;

CMD => Executa um comando, diferente do RUN que executa o comando no momento em que está "buildando" a imagem, o CMD executa no início da execução do container;

LABEL => Adiciona metadados a imagem como versão, descrição e fabricante;

COPY => Copia novos arquivos e diretórios e os adicionam ao filesystem do container;

ENTRYPOINT => Permite você configurar um container para rodar um executável, e quando esse executável for finalizado, o container também será;

ENV => Informa variáveis de ambiente ao container;

EXPOSE => Informa qual porta o container estará ouvindo;

FROM => Indica qual imagem será utilizada como base, ela precisa ser a primeira linha do Dockerfile;

MAINTAINER => Autor da imagem; 

RUN => Executa qualquer comando em uma nova camada no topo da imagem e "commita" as alterações. Essas alterações você poderá utilizar nas próximas instruções de seu Dockerfile;

USER => Determina qual o usuário será utilizado na imagem. Por default é o root;

VOLUME => Permite a criação de um ponto de montagem no container;

WORKDIR => Responsável por mudar do diretório / (raiz) para o especificado nele;
```

```bash
```
