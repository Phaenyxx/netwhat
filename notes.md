Netwhat
========

## Adresse IP
Une adresse IP ( **I**nternet **P**rotocol) est un numéro d'identification attaché à un périphérique relié à un réseau informatique.
Deux versions : IPv4 (32 bits) & IPv6.  
Structure pour IPv4 : Quatre nombres compris entre 0 et 255, séparés par des points.
    **Exemple :** ``172.16.254.1``

### Classes
| Classe | Plages correspondantes |
| :--------: | :------------------------------: | 
| Classe A | de ``0.0.0.0``. à ``127.255.255.255`` |
| Classe B | de ``128.0.0.0`` à ``191.255.255.255`` |
| Classe C | de ``192.0.0.0`` à ``223.255.255.255`` |
| Classe D | de ``224.0.0.0`` à ``239.255.255.255`` |
| Classe E | de ``240.0.0.0`` à ``255.255.255.255`` |
>Obsolète depuis l'avènement du routage sans classe.

##### Plages privées réservées à des adresses locales :
- De ``10.0.0.0`` à ``10.255.255.255``
- De ``172.16.0.0`` à ``172.31.255.255``
- De ``192.168.0.0`` à ``192.168.255.255``

## Sous-réseau 
Une adresse est composée de deux parties : Sous-réseau et hôte.  
Le masque de sous réseau sépare les bits d'une adresse utilisés pour identifier le réseau de ceux de l'hôte. Deux adresses IP appartiennent à un même sous-réseau si elles ont en commun le masque de sous-réseau.
Il y a deux adresses particuliéres propres à chaque sous-réseau: 
- L'adresse de sous réseau à proprement parler : Obtenue avec l'opérateur binaire ET entre une adresse IPv4 et le masque de sous réseau
- L'adresse de broadcast : Obtenue avec l'opérateur binaire OU entre une adresse IPv4 et le complément à 1 masque de sous réseau _(elle sert à envoyer un message à tous les périphériques connectés au sous-réseau)_

**Exemple avec adresse ``192.168.1.2`` et masque ``255.255.255.0``:**

    192.168.1.2 & 255.255.255.0 = 192.168.1.0 (adresse de sous-réseau)
    192.168.1.2 & 0.0.0.255     = 0.0.0.2 (adresse hôte)
    192.186.1.2 | 0.0.0.255     = 192.168.1.255 (broadcast)

##### CIDR
Une notation courante est la notation CIDR ( **C**lassless **I**nter-**D**omain **R**outing). Le numéro du réseau est suivi d'un slash et d'un numéro indiquant le nombre de bits à un du masque.
**Example :**``91.198.174.2/19`` désigne donc l'adresse IP ``91.198.174.2`` avec le masque ``255.255.224.0``

## Modèle OSI
> **O**pen **S**ystems **I**nterconnection

Norme de communication des systèmes informatiques, organisée en couches :
|   | Couche | Fonction |
|:---------------------:|:-------------:|:----------------------------------------------------------------------:|
| Couches hautes | Application | Point d'accès aux services réseau |
|  |  Présentation | Chiffrement et déchiffrement des données |
|  | Session | Communication entre les différentes applications |
| --- | Transport | Connexion entre différents port ( TCP & UDP) |
| Couches matérielles | Réseau |  Détermine le parcours des données et adressage logique ( Adresse IP ) |
|  | Liaison | Adressage Physique ( Adresse MAC ) |
|  | Physique | Transmision des signaux sous forme numérique ou analogique |

## TCP & UDP
>**T**ransmission **C**ontrol **P**rotocol  & **U**ser **D**atagram **P**rotocol

Protocoles de la couche transport du modèle OSI.

UDP
: Protocole orienté ''Sans connexion'' : Transmission sans avertissement / sans accusé de réception de l'émetteur au destinataire. Seul l'IP de l'émetteur est connue du destinataire.

TCP
: Protocole orienté ''Connexion'' : L'émetteur et le destinataire communique (avertissement avant transmission, accusé de réception). Les données reçues sont vérifiées et le destinataire peut demander un renvoi des données.

##### Avantages: 
| TCP | UDP |
|:-------------------------------:|:---------------------------------------------------------:|
| Transport fiable et sans pertes | Transport rapide |
|  | Communications avec plusieurs utilisateurs simultanément. |