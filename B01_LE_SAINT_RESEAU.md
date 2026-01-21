# Le Saint Reseau

## Addressage Reseau 

Prenons un base avec 23.34.56.78/23

---------------------

**1. Le mask de sous reseau :**

 /17 = 1111 1111. 1111 1111 . 1111 11110 . 0000 0000  soit 255.255.254.0 
 
 ou plus simplement
 
 /24 - /23  = 24 - 23 = 1 ==> 2^1 = 2   256-2= 254   (256 est le nombre de possibilité donc 255 + 1 pour la possibilité du 0)

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

255.255.254.0 ==>  0.0.1.255 Donc  23.34.56.0 + 0.0.1.255

L'addresse de Broadcast sera donc 23.34.57.255

Le range d'ip sera donc de 23.34.56.1 a 23.34.57.254


## Le supernetting

------------------------------------
**Type de sous Réseau**

**Classe A  (/8) :** 1.0.0.0 ==> 127.255.255.255

**Classe B (/16) :** 128.0.0.0 ==> 172.31.255.255

**Classe C (/24) :** 192.168.0.0 ==> 192.168.255.255

--------------------------------------
**Verifier que sont réseau peut etre fusioner**

**Etape 1 :** 

Vérifier que les addresses réseaux à fusionner on le même / **ET** le nombre de réseau a fusioner est un multiple de 2

**Exemple :**

X.X.X.X/16 

X.X.X.X/15

X.X.X.X/16

!! non fusionnable car il y a 3 réseau dont un en /15 !!

**Etape 2 :**

Est ce que les adresses sont **contigu** ?

Pour cela calculer le nombre magique :

/28 ==> /32 - /28 = 4 ==> 2^4 = 16

Un reseau contigu serai un multiple de 16 : 

X.X.X.0

X.X.X.16 

X.X.X.32

.......

**Etape 3**

**Verifier** que dans le sous réseau le plus bas, le premier octet non commun est un divisible du /n - 1  

==> /16 ==> /16 - (/16 -1) = /1 ==> 2^1 = 2 

==> /14 ==> /16 - (/14-1) = /3 ==> 2^3 = 8

==> /22 ==> /24 - (/22-1) = /3 ==> 2^3 =8  


**Exemple :**

|List 1  |	List 2 |
|--------|---------
|192.168.0.0/24	| 10.3.0.0/16 |
|192.168.3.0/24 |	10.4.0.0/16|
|               | 	10.5.0.0/16|


**Etape 2:** 

List 1 ne fonctionne pas car le réseau n'est pas contigu ==> /24 - /24 = 0 ==> 2^0 = 1 le sous reseau suivant  192.168.0.0/24 devrais etre 192.168.1.0/24
List 2 does pass this rule because each subnet is in sequence
