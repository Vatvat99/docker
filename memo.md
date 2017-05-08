# Memo des commandes Docker

## Docker-machine

Permet de communiquer avec la machine virtuelle installée sous virtualbox.


Lister les machines virtuelles :
```
$ docker-machine ls
```

Démarrer la machine virtuelle "default" :
```
$ docker-machine start default
```

Arrêter la machine virtuelle "default" :
```
$ docker-machine stop default
```

Récupèrer l'adresse IP de la machine "default" :
```
$ docker-machine ip default
```

Indiquer aux commandes docker de travailler avec la machine "default" (la dernière ligne que renvoie cette commande est à recopier pour permettre à la console de dialoguer avec la bonne machine.) :
```
$ docker-machine env default
```

Se connecter à la machine virtuelle : 
```
$ docker-machine ssh
```

# Docker

Lister les images :
```
$ docker images
```

Supprimer une image : 
```
$ docker rmi [IMAGE_NAME]
```

Arrêter un container :
```
$ docker stop [CONTAINER_NAME]
```

Supprimer un container :
```
$ docker rm [CONTAINER_NAME]
```

## Docker Compose

Permet d'interagir avec les containers.

Lister les containers :
```
$ docker-compose ps
```

Créer et démarrer les containers (-d pour le mode détaché : console libérée) :
```
$ docker-compose up -d
```

Créer et démarrer les containers en reconstruisant les images avant :
```
$ docker-compose up --build
```

Arrêter et supprimer les containers :
```
$ docker-compose down
```