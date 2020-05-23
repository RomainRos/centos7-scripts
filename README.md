# Script d'initialisation post-installation pour serveur CentOS 7 

(c) Niki Kovacs, 2020

Ce dépôt contient un script d'initialisation post-installation "automagique" pour
un serveur sous CentOS 7, ainsi qu'une série de scripts utiles et de schémas de
fichier de configuration pour divers services.

## En résumé

Réalisez les étapes suivantes :

  1. Installez un système CentOS 7 minimal.

  2. Créez un utilisateur non-`root` avec des privilèges administrateur.

  3. Installez Git: `sudo yum install git`

  4. Récupérez le script : `git clone https://gitlab.com/kikinovak/centos-7.git`

  5. Déplacez-vous dans le nouveau dossier : `cd centos-7`

  6. Exécutez le script : `sudo ./centos-setup.sh --setup`

  7. Prenez un café pendant que le script fait le travail

  8. Redémarrez.


## Personnaliser un serveur CentOS

Monter un serveur CentOS fonctionnel à partir d'une installation minimale requiert
toujours une série de tâches plus ou moins chronophages. Vos habitudes peuvent varier
bien sûr, mais voilà ce que je fais habituellement sur une installation CentOS :

  * Paramétrage du shell Bash : prompt, alias, etc.

  * Paramétrage de l'éditeur vim.

  * Mise en place des dépôts officiels et tiers.

  * Installation d'une série d'outils Linux utiles.

  * Suppression d'une série de paquets inutiles.

  * Autoriser l'utilisateur administrateur à accéder aux journaux.

  * Désactiver IPv6 et reparamétrer plusieurs services en conséquence.
  
  * Créer un mot de passe permanent pour `sudo`.

  * Etc.

Le script `centos-setup.sh` fait toutes ces opérations.

Paramétrer bash et vim et définit une résolution console plus lisible :

```
# ./centos-setup.sh --shell
```

Mise en place des dépôts officiels et tiers :

```
# ./centos-setup.sh --repos
```

Installation des groupes de paquets `Core` et `Base`, ainsi que quelques outils utiles :

```
# ./centos-setup.sh --extra
```

Suppression d'une série de paquets inutiles.

```
# ./centos-setup.sh --prune
```

Autoriser l'utilisateur administrateur à accéder aux journaux :

```
# ./centos-setup.sh --logs
```

Désactiver IPv6 et reparamétrer plusieurs services en conséquence :

```
# ./centos-setup.sh --ipv4
```

Créer un mot de passe permanent pour `sudo` :

```
# ./centos-setup.sh --sudo
```

Faire tout ci-dessus d'un seul coup :

```
# ./centos-setup.sh --setup
```

Supprimer les paquets et retourner à un système de base :

```
# ./centos-setup.sh --strip
```

Afficher un message d'aide :

```
# ./centos-setup.sh --help
```

Si vous voulez savoir ce qu'il se passe exactement sous le capot, ouverez un
deuxième terminal et regardez les logs :

```
$ tail -f /tmp/centos-setup.log
```

