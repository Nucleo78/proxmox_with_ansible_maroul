# TP3 - VM Creation with ANSIBLE - MAROUL
## Objectif du projet
L'objectif du projet est d'utiliser ansible pour pouvoir créer des machines virtuelles à distance sur un serveur proxmox

## Structure du projet
Le projet est structuré ainsi :

Le playbook est à la racine du projet.
Ensuite le dossier inventories va contenir les différents fichiers d'environnements pour pouvoir lancer le playbook. On aura deux environnemnt :
- prd (pour production)
- dev (pour le développement local)

![image](assets/structure_projet.jpg)

## Instructions pour utilisation
### Prérequis
- python3 et pip d'installé
- ansible installé
- serveur Proxmox configuré et lancé. Il doit être accessible depuis votre machine qui exécute le code ansible
- le serveur est configuré avec l'ip : 192.168.30.140
- Vous pouvez changer l'ip de configuration dans les fichiers .yml des dossiers /prd et /dev (host.yml)

#### Installation de python et d'ansible
Personnellement, j'ai créer un environnement isolé pour ansible. Voici les commandes à utiliser pour créer l'environnement et installer ansible :
- sudo apt install python3-venv -y
- python3 -m venv ansible-env
- source ansible-env/bin/activate
- pip install --upgrade pip
- pip install ansible
Avec ça vous avez tous ce qu'il faut pour exécuter les commandes ansible.

### Exécution du playbook
Pour exécuter le playbook, placez vous à la racine du projet et tapper la commande :
#### ansible-playbook -i inventories/prd/hosts create-vm.yml --ask-pass
pour exécuter le playbook avec les variables de l'environnement de prod. Remplacer /prd par /dev pour l'exécuter avec les variables de l'environnement de dev.

On vous demandera ensuite le mot de passe que vous avez configuré pour le compte root (dans notre cas). Si vous voulez changer le compte utilisé pour vous connecter, aller dans le fichier all.yaml de l'environnemnt souhaité.

Normalement, la machine virtuelle devrait se créer avec un id de libre, puis se lancer.

### Exemple d'exécution
![image](assets/execution.jpg)
![image](assets/execution2.jpg)
