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

**Verifier que sont réseau peut etre fusionner**
------------------------------------
