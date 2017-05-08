# Environnement de développement local sous Docker Toolbox

Projet destiné à installer un environnement de développement local via Docker Toolbox, sous Windows, avec les technologies suivantes :

- Apache
- Php/MySQL
- PhpMyAdmin

## Installation

1. Une fois les fichiers récupéré, créer un répertoire www destiné à contenir les sources des applications au même niveau que le dossier docker. e.g : C:/dev/docker (dossier docker) et C:/dev/www (dossier contenant les sources)

2. Créer dans ce répertoire source un dossier test et y placer un fichier index.php avec une instruction du type `<?php phpinfo(); ?>`

3. Installer Docker toolbox

4. Dans Virtual Box : Configuration de la machine "default" / Dossiers partagés, ajouter la règle suivante :  
Chemin : C:\dev\www (dossier contenant les sources)  
Nom : www

5. Se connecter à la machine virtuelle "default" : 
```
$ docker-machine ssh
```

6. Créer le dossier dans lequel seront placées les sources : 
```
$ mkdir /var/www
```

7. Créer le lien avec le dossier partagé de virtualbox : 
```
$ sudo mount -t vboxsf www /var/www
```

8. Créer un fichier pour y mettre la configuration initiale de la machine :
```
$ sudo vi /var/lib/boot2docker/bootlocal.sh
```

9. Inscrire dans ce fichier :
```
mkdir /var/www
mount -t vboxsf www /var/www
```

10. Rendre le fichier exécutable :
```
$ sudo chmod +x /var/lib/boot2docker/bootlocal.sh
```

11. Quitter la machine:
```
$ exit
```

12. Par défaut, un hôte virtuel test.loc est configuré pour aller chercher les sources dans www/test. Pour que cela fonctionne, ajouter la ligne suivante au fichier host de windows (C:\Windows\System32\drivers\etc) :
```
[ip de la machine virtuelle] test.loc
```

L'adresse IP de la machine peut être obtenue avec la commande suivante : 
```
$ docker-machine ip default
```

13. Renommer le fichier .env.dist en .env et entrer une valeur pour chaque variable

#### Utilisation de l'éditeur vi :
```
i : Entrer dans le mode insertion
:q : quitter
:wq : sauvegarder et quitter
```

## Utilisation

1. Lancer VirtualBox

2. `$ docker-machine start`

3. `$ docker-machine env`

4. copier-coller la commande renvoyée

5. `$ docker-compose up -d` (dans le répertoire ou est le fichier docker-compose.yml)

6. Les URL suivantes sont désormais accessibles :
- http://test.loc
- http://test.loc:8080 (phpmyadmin)

## Ajouter un nouveau vhost

1. Ajouter un nouveau fichier décrivant le vhost dans php-apache/config/vhosts

2. Ajouter la ligne suivante dans le fichier host de windows (C:\Windows\System32\drivers\etc) :
  ```
  [ip de la machine virtuelle] [URL_VHOST]
  ```

## Mettre à jour Docker Toolbox

Télécharger la nouvelle version et l'installer simplement par-dessus l'autre.
