## Analyse d'un serveur existant

### Analyse du code

Les commandes sont interprétées par la fonction handle de IRCHandler qui appelle ensuite les fonctions qui correspondent à chaque commande.

Presque toutes les fonctions du serveur accèdent à la mémoire partagée.

Toutes les informations sont stockées sur le serveur.

Quand on utilise la commande /msg, le message s'écrit correctement mais le code se bloque : le serveur n'interprète aucune commande ensuite sauf /quit.

### Schéma d'architecture

### Limites



le traitement des cmds manipule à la fois l'état métier, les sockets et la log : par exemple la fonction set_pseudo; dans l'idéal, il faudrait séparer au mieux
en enlevant IRCHandler, on devra changer toutes les fonctions associées aux commandes

il n'y a pas de types d'erreur, le protocole se contente d'envoyer un message d'erreur au client sans syntaxe particulière

le protocole peut être formaliser dans une documentation

Ajouter une rétrocompatibilité et une nouvelle commande serait très couteûx car tout le code est concentré dans le même fichier, ce qui va le complexifier de plus en plus

Il n'y a que les méthodes charger_etat et sauvegarder_etat qui peuvent être testées
autres tests impossibles sans simuler un client

L'état du serveur est global et, actuellement, il peut devenir bloqué constamment à cause de l'utilisation d'un lock; il ne peut donc être utilisé que par un nombre limité d'utilisateurs

On pourrait ajouter une base de données pour mieux gérer le stockage des données, plutôt qu'un fichier json

