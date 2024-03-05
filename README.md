EXERCICE 2
Creez un repo github nommé docker-exe2
il doit etre public, avec un fichier README.md , un fichier .gitignore valable pour le langage Python, une License MIT
Faites un git clone dans votre directory project local
mettre en place dans rubymine la connexion ssh vers votre VM
attention a ne pas oublier le mapping sur le deployment path sur /home//docker-exe2
Mettre les commandes de l'exercice suivant dans le fichier README.md

Creez un Dockerfile file dans votre projet sous Rubymine , qui contient
comme image de base fabric8/tomcat-9 de tomcat 9
copier le fichier webapp.war dans la directory de tomcat /opt/tomcat/webapps
faire un build d'image avec ce Dockerfile, l'image est nommée tomcat:v1
Faire des recherches ( docker history, docker inspect) pour trouver le port utilisé par tomcat dans cette image Faire un docker run pour creer un container a partir de l'image tomcat:v1, en background, avec le mapping de port
30200: et le port de tomcat dans le container que vous avez trouvé
Ouvrir votre navigateur et affiche la page d'accueil de l'application , copiez et collez le texte de cette page dans le fichier result.txt
En utilisant portainer , allez a l'interieur du container et creer un utilisateur tomcat nommé logwire et password: docker
mettez cette image dans docker hub sous votre compte docker hub

-- CMD --

```shell
docker build -t tomcat:v1 .
docker run -d -p 30200:8080 --name tomcat_container tomcat:v1
docker exec -it tomcat_container /bin/bash

root cmd
cd /opt/tomcat/conf
vi tomcat-users.xml
<user username="logwire" password="docker" roles="admin-gui,admin-script,manager-gui,manager-status,manager-script,manager-jmx"/>

docker login -u brian45000
docker image tag tomcat:v1 brian45000/tomcat:v1
docker push brian45000/tomcat:v1
```