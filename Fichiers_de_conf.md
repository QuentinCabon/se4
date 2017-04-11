Passer tous les fichiers de conf de SambaEdu et des modules dans un format simple et facile à utiliser

# Structure

Tous les fichiers sont sous la forme `key="value"`, afin d'être lisibles simplement dans tous les langages.

L'arborescence est au standard Debian des fichiers de conf :
```
/etc/se3/+------------se3.conf
         +se3.conf.d/+dhcp.conf
                     +ipxe.conf
                     +xxx.conf
                     ....
```
## bash
On peut directement evaluer les fichiers, à condition qu'il n'y ait pas d'espace autour du = !. Le mieux est d'avoir un script qui lise se3.conf, puis qui boucle sur se3.conf.d/*

```
eval $(sed "s/\s*=\s*/=/" se3.conf*)
```
Doit faire l'affaire

## php
On utilise parse_ini_file()

# ecriture

Différents cas d'utilisation sont possibles : 

## debconf
pour tous les parametrages interactifs ou automatisés lors de l'installation
## Ansible
Configuration à distance des serveurs : on utilise le module Ansible debconf
## page setup.php
conf manuelle  post-installation par l'utilisateur
## pages php diverses
configuration de parametres divers via l'interface






                     
