## Réflexion liminaire

### 2.1 Cohérence concurrente et synchronisation

Il faut trouver un moyen de synchroniser les canaux entre les utilisateurs pour que les messages apparaissent dans le bon ordre.

### 2.2 Modularité et séparation des responsabilités

Responsabilités fonctionnelles:
- accepter plusieurs clients simultanément
- traiter les commandes des utilisateurs
- stocker, d'une manière non spécifiée, les messages et canaux pour assurer une persistance des données

On peut séparer la logique métier et la logique qui s'occupe des entrées et sorties sur le réseau. C'est la couche de logique métier qui s'occupe de gérer les erreurs dans les commandes.

### 2.3 Scalabilité et capacité à évoluer

L'ajout d'une nouvelle commande concerne uniquement la couche logique métier, puisque la couche qui s'occupe du réseau ne fait qu'envoyer les commandes à la couche logique sans les regarder.

Pour que ce serveur fonctionne à grande échelle, il faudrait un moyen de stockage persistant des messages et canaux car on ne pourra pas stocker des centaines de messages et de canaux uniquement dans la mémoire vive, ça ralentirait de plus en plus le serveur jusqu'à le bloquer.

### 2.4 Portabilité de l'architecture

### 2.5 Fiabilité, tolérance aux erreurs, robustesse

### 2.6 Protocole : structuration et évolutivité

Il n'existe pas de réelle documentation du protocole disponible pour les utilisateurs pour 
l'instant. Il faudrait en rédiger une si on veut pouvoir partager notre protocole : personne ne voudrait s'embêter à deviner comment il fonctionne afin de développer un client.

Le protocole n'est pas très robuste, l'implémentation des commandes pourrait être améliorée.


