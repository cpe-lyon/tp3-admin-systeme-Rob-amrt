# TP 3 - Gestion des paquets

## Exercice 1. Commandes de base

### 1. Quels sont les 5 derniers paquets installés sur votre machine ?
`grep "installed" /var/log/dpkg.log | tail -5`

### 2. Utiliser dpkg et apt pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !).
Comment explique-t-on la (petite) différence de comptage ?
DPKG : `dpkg -l | grep "^i" | wc -l`
apt : `apt list --installed | wc -l`

### 3. Combien de paquets sont disponibles en téléchargement ?
`apt list | wc -l`

### 4. Créer un alias “maj” qui met à jour le système
Il faut editer dans le .bashrc : `alias maj='sudo apt upgrade && sudo apt update'`

### 5. A quoi sert le paquet fortunes ? Installez-le
A rien. Si allez c'est drôle.

### 6. Quels paquets proposent de jouer au sudoku ?
La commande `apt search "sudoku"`

### 7. Lister les derniers paquets installés explicitement avec la commande apt install
Avec la commande `grep "apt install" /var/log/apt/history.log`

## Exercice 2

A partir de quel paquet est installée la commande ls ? Comment obtenir cette information en une seule
commande, pour n’importe quel programme (indice : la réponse est dans le poly de cours 2, dans la liste des
commandes utiles) ? 

`which -a ls | tail -1 | xargs dpkg -S`

Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension
.sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.

## Exercice 3. Ecrire une commande qui affiche “INSTALLÉ” ou “NON INSTALLÉ” selon le nom et le statut du package spécifié dans cette commande.
`(dpkg -l "fortunes" | grep "^i") && echo "installé" || echo "non installé"`

## Exercice 4. Lister les programmes livrés avec coreutils. A quoi sert la commande ’[’ et comment afficher ce qu’elle
retourne ?
Pour lister les programmes de coreutils `dpkg -L coreutils | grep "bin"`
La commande `[` permet de faire des conditions à l'intérieur de commandes, pour afficher ce qu'elle nous retourne il suffit de respecter la syntaxe référencé dans le manuel `man`

## Exercice 5. Aptitude
Installez le paquet emacs à l’aide de la version graphique d’aptitude
Done
