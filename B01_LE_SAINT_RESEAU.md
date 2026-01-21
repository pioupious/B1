# Le Saint Reseau

## Addressage Reseau 

Prenons un base avec 23.34.56.78/23

---------------------

**1. Le mask de sous reseau :**

 /17 = 1111 1111. 1111 1111 . 1111 11110 . 0000 0000  soit 255.255.254.0 
 
 ou plus simplement
 
 /24 - /23  = 24 - 23 = 1 ==> 2^1 = 2  
 
 256-2= 254   (256 est le nombre de possibilité donc 255 + 1 pour la possibilité du 0)

-----------------------

 **2. Le sous reseau**

Sur le même octet que la délimitation du mask on à 56  ==>  23.34.(56).78

56 = 32 + 16 + 8 = 2^5 + 2^4 + 2^3  Soit  0001 1100

Nous appliquons un **ET** entre le mask et le l'octet correspondant pour déterminer le sous reseaux :

128 ==> 1111 1110

56 ==> 0001 1100

=====> 0001 1100


Le resultat du **ET** est donc : 0001 1100 = 64 DONC le sous Reseau est 23.34.56.0/23

-----------------------

**3. La broadcast :**

Pour caluculer la broadcast nous allons inversé le masque de sous reseau et l'additionner à notre addresse de sous reseau 

255.255.254.0 ==>  0.0.1.255 

Donc la Broadcats est : 23.34.56.0 + 0.0.1.255

Pour un resusltat de 23.34.57.255

Le range d'ip sera donc de 23.34.56.1 a 23.34.57.254


## Le supernetting

------------------------------------
**Type de sous Réseau**

**Classe A  :** 0.0.0.0 ==> 127.255.255.255

**Classe B  :** 128.0.0.0 ==> 191.255.255.255

**Classe C  :** 192.0.0.0 ==> 223.255.255.255

--------------------------------------
**Verifier que sont réseau peut etre fusioner**

- **Etape 1 :** 

Vérifier que les addresses réseaux à fusionner on le même / **ET** le nombre de réseau a fusioner est un multiple de 2

**Exemple :**

X.X.X.X/16 

X.X.X.X/15

X.X.X.X/16

**!! non fusionnable car il y a 3 réseau dont un en /15 !!**

- **Etape 2 :**

Est ce que les adresses sont **contigu** ?

Pour cela calculer le nombre magique :

Pour un /28 ==> /32 - /28 = /4 = 2^4 = 16

Un reseau contigu sera un multiple de 16 : 

X.X.X.0

X.X.X.16 

X.X.X.32

.......

- **Etape 3 :**

**Verifier** que dans le sous réseau le plus bas, le premier octet non commun est un divisible du nombre de réseau à fusionner **uniquement si ce nombre est paire**


--------------------------------------------

**Exemple :**

|List 1  |	List 2 |
|--------|---------
|192.168.0.0/24	| 10.3.0.0/16 |
|192.168.3.0/24 |	10.4.0.0/16|
|               | 	10.5.0.0/16|


- **Etapes 1 :**

List 1 fonctionne car il y a 2 addresse du meme /
list 2 ne fonctionne pas car il y a 3 addresse meme si elle on le meme / et quelle qoit dans la meme catégorie  (a,b,c)

- **Etape 2 :** 

List 1 ne fonctionne pas car le réseau n'est pas contigu ==> /24 - /24 = 0 ==> 2^0 = 1 le sous reseau suivant  192.168.0.0/24 devrais etre 192.168.1.0/24
List 2 fonctionne car il est contigu  ==> /16 - /16 = 0 ==> 2^0 = 1 le pas du sous reseau doit etre de 1 ce qui est le cas.

- **Etapes 3 :**
 
List 1 fonctionne le premier octet non commun est le 3ème 192.168.(0).0 et il est un multiple de 2 le nombre de reseau  
List 2 fonctionne pas car le nombre sous reseau n'est pas paire et le premier octet non commun est le 2 ème 10.(3).0.0 n'est pas un multiple de 2 si un voulais agréger seulement les deux premier réseaux. 

--------------
**SUPERNETTING**

Une fois qu'on à verifier que les réseau étaient fusionable on peux commencer a les agrégeg ou supernetter.

**Pour l'exemple :***
- 212.56.146.0/24
- 212.56.147.0/24
- 212.56.148.0/24
- 212.56.149.0/24

Pour cela on prend le nombre de sous reseau soit 4 ==> 2^2 

On prend la puissance pour la soustraire au /24 du sous reseau nous aurrons donc un reseau en /22

***!!!! MAIS PEUT-ON VRAIMENT AGREGER SE RESEAU, REPONSE EN FIN SI VOUS VOULEZ ESSAYER !!!!**

------ 
**MISE EN PRATIQUE**

Agreger les prefix de 202.1.96.0/24 ==> 202.1.159.0/24 soit 64 reseau 

- **Etape 1 :**

Le nombre de raiseau est-il paire ? **oui**  

Sont-ils de la meme taille ? tous des /24 donc **OUI**

- **Etape 2 :**

Sont il contigu ? 

/24 - /24 = /0 = 2^0 = 1 donc ils doivent avoir un espacement de 1 sur le 3 octet et c'est le cas **donc** contigu

- **Etape 3 :** 

Est ce que le sous reseau de départ est bon  ? 

Nous avons **64 sous reseau** à fusionner et **le plus petit est 96**

96/64 **Rhhhha !! Pas possible ;( !!!**

**On ne peux pas les fusionner en un seul reseau !!**

---- **Reflexion**

**96** qui est le premier plus petit des sous réseau est un multiple de **32**. Nous ne pouvons peux etre pas faire 1 reseau de 64 mais 2 reseau de 32

- **Partons de ce postulat :**

202.1.96.0 ==> 202.1.127.0

ET

202.1.128.0 ==> 202.1.159.0

Le / sera : nombre de reseau 32 = 2^5 ==> /24-5 = /19

**RESULTAT**
On peux avoir 2 reseau  : 202.1.96.0/19 et 202.1.128.0/19

----------------
## Subnetting

**Le subnetting c'est diviser le un reseau en plusieur plus petit, cela est possible uniquement si la divison recherché est paire !!**

- Pour ce faire nous prendrons le nombre de sous réseau voulu et le passeront au format 2^n. n que nous ajouterons au / du reseau qu'on veux diviser.

**Exemple :**

192.168.0.0/24 à diviser en 8 ==> 8 = 2^3 nous aurons donc 8 sous réseau en /24+3 ==> /27

- Nous allons ensuite déterminer les sous réseau de chaques divisions. Pour cela nous prendrons l'octet au dessus auquel nous allons soustraire notre
/26 ==> /32 - /27 = /6 = 2^5 = 32

**FINI  !!!! Nos réseau seront donc :**

192.168.0.0/27

192.168.0.32/27

192.168.0.64/27

192.168.0.96/27

192.168.0.128/27

192.168.0.160/27

192.168.0.192/27

192.168.0.224/27




