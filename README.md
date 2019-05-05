# DOCKER-JENKINS TP

- Lancer Jenkins :

``` bash
cd jenkins
docker build -t jenkins-docker .
docker run --name docker-jenkins -p 8085:8080 -d -v /var/run/docker.sock:/var/run/docker.sock jenkins-docker
docker exec --user root docker-jenkins chmod 777 /var/run/docker.sock
```

- Aller sur : localhost:8580

- Pour récupérer le mot de passe de Jenkins :

``` bash
docker logs docker-jenkins
```

- Aller sur Jenkins et lancer un job pour créér une pipeline récupérée depuis un scm

- Renseigner le lien vers un repository

- Déclencher un build

- À la fin du build l'image est push :
https://hub.docker.com/r/chrysplt/docker-jenkins