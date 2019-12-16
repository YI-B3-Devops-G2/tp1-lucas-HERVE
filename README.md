# lucas2101-pixel-yi-b3-devops-tp1
# B3 Devops - TP 1
## Info
mail: lucas.herve@ynov.com 
github_username: lucas2101-pixel

Installation de Vargrant pour windows
Go sur le site https://www.vagrantup.com/downloads.html
Et telecharger l'executable pour windows
Une fois telecharger vous pouvez verifier dans le cmd la version de vagrant installer grace a la commande:
vagrant -v
Apres avoir vérifié la version de vagrant, lancer les deux commandes suivante 
vagrant init hashicorp/bionic64
vagrant up
Une fois ces deux commandes lancée, sur virtualbox nous retrouverons ainsi une nouvelle machine virtuelle

Nous voulons ouvrir au démmarage le port 22,80.
Pour cela nous allons modifier le fichier vagrantfile
Nous rentrerons donc les ligne suivantes
config.vm.network "forwarded_port", guest: 80, host: 8080
config.vm.network "forwarded_port", guest: 22, host: 2520
Ces deux lignes permettront de nous connecter en ssh et en http a notre application
Une fois ces deux ligne renseigner on peut maintenant rennseigner des commandes pour l'installation de nginx.
Il vous faut maintenant créer un ficher bootstrap.sh afin de renvoyer des commandes pour l'installation de nginx.
Dans le fichier boostrap rentrer les comamdnes suivantes:
#!/bin/bash

apt-get update
apt-get install -y nginx

Une fois les commandes rentrer fermer le fichier (attention le fichier boostrapt doit etre dans la meme racine que le fichier vagrantfile)
Dans le fichier vagrantfile mettre la commande "config.vm.provision :shell,path: "bootstrap.sh""
Enregistrer le fichier et lancer la commande vagrant up.
Le lancement de l'installtion de votre Vm va débuté
Une fois celle-ci terminé essayer "vagrant ssh" pour vous connecter en ssh 
Pour tester le http aller dans votre navigateur et rentré 127.0.0.1:porthost
(porthost 8080 dans notre cas)
[...]
