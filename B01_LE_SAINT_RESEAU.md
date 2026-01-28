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

------

**Correction**

Nous ne pouvons pas les fusionner, il a tout les check au vert sauf le sous reseau de départ. On a 4 sous réseau à fusionner le premier est 212.56.146.0/24 et 146 est pas divisible par 4 malheuresement  ...

#Cisco Paquet Tracer

## Le switch 

Avant de commencer à configurer le switch mettre en place les ip et gateway sur les ordinateur.

Puis set vlan sur un switch :
``` 
switch> en (activer le switch)
switch # conf t (rentrer dans le mode configuration)

switch(config)# hostname nom (attribuer un nom au swith)

switch(config)# vlan 10 (choisire un vlan)
switch(config-vlan)# name VLAN10 (renomer la vlan pour la créer)
switch(config-vlan)# exit

switch(config)# vlan 20 (choisire un vlan)
switch(config-vlan)# name VLAN20 (renomer la vlan pour la créer)
switch(config-vlan)# exit

switch(config)# vlan 99
switch(config-vlan)# name SVI
switch(config-vlan)# exit

switch(config)# vlan 100 
switch(config-vlan)# name VLANDEFAULT
switch(config-vlan)# exit

switch(config)# int fa0/1 (configurer le port fast ethernet 0/1)
switch(config-if)# switchport mode access (passer le port selection en mode access)
switch(config-if)# switchport access vlan 10 (indiquer a ce port qu'il appartient a la vlan10)
switch(config-if)# exit 

switch(config)# int fa0/2 (configurer le port fast ethernet 0/2)
switch(config-if)# switchport mode access (passer le port selection en mode access)
switch(config-if)# switchport access vlan 20 (indiquer a ce port qu'il appartient a la vlan20)
switch(config-if)# exit 

switch(config)# int range fa0/3-fa0/24 (configurer le port fast ethernet 0/1)
switch(config-if)# switchport mode access (passer le port selection en mode access)
switch(config-if)# switchport access vlan 100 (indiquer a ce port qu'il appartient a la vlan99 qui est la vlan par default)
switch(config-if)# exit 

switch(config)# interface vlan 99 
switch(config-vlan)# description Management_SVI
switch(config-vlan)# ip address 192.168.99.2 255.255.255.0 (donner une ip dans pour ce connecter en ssh)
switch(config-vlan)# no shutdown (indiquer que la vlan doit etre allumée)
switch(config-vlan)# exit
switch(config)# ip default-gateway 192.168.99.1 ( configure la gateway)


switch(config)# int gi0/1 (prendre le port de sortie et le configurer)
switch(config-if)# description TRUNK_Vers_SW2 
switch(config-if)# switchport mode trunk (le passer en mode truck = mode filtrage)
switch(config-if)# switchport trunk allowed vlan 10,20 ( indiquer les port que vous autorizer a laisser passer)
switch(config-if)# exit
switch(config)# exit
switch# exit
```

-----------------------------

Pour les Switch de niveau 3 ou switch qui font du rooting 

``` 
switch> en (activer le switch)
switch # conf t (rentrer dans le mode configuration)

switch(config)# hostname nom (attribuer un nom au swith)

switch(config)# ip routing (activer le niveau 3 du routing)


switch(config)# interface vlan 10 (indiquer la vlan a parametrer pour l'inter vlan)
switch(config-vlan)# description GW_USERS
switch(config-vlan)# ip address 192.168.10.1 255.255.255.0 (lui donner la meme address que la gateway du vlan)
switch(config-vlan)# no shutdown (l'allumer)
switch(config-vlan)# exit

switch(config)# interface vlan 20(indiquer la vlan a parametrer pour l'inter vlan)
switch(config-vlan)# description GW_USERS
switch(config-vlan)# ip address 192.168.20.1 255.255.255.0 (lui donner la meme address que la gateway du vlan)
switch(config-vlan)# no shutdown (l'allumer)
switch(config-vlan)# exit
```

Interdire a des message dans un certain sens : 

```
switch(config)# access-list 10 deny 192.168.1.10 0.0.0.255 (créer une règle 10 qui n'autorise pas le .1 a passer)
switch(config)# access-list 20 deny 192.168.1.10 0.0.0.255 19.168.2.10  (créer une règle 20 qui n'autorise pas le .2 a passer a envoyer un message au .1)
access-list 10 permit any ( autorise tout les passage des autre que mentionner dans le deny)
no access-list 10 (suprime l'acces list 10) 

```
---------------------------------

Au niveau d'un routeur

```
router# conf t
router(config)# interface g0/0.10 (diviser le port connecter avec le switch )
router(config-if)# encapsulation dot1Q 10 (permettre une encapsulation et donner le meme nb que la vlan visée)
router(config-if)# ip address 192.168.10.1 255.255.255.0 (indiquer se port comme la gateway de la vlan 10)
router(config-if)# exit
router(config)# interface g0/0.20 (diviser le port connecter avec le switch )
router(config-if)# encapsulation dot1Q 20(permettre une encapsulation et donner le meme nb que la vlan visée)
router(config-if)# ip address 192.168.20.1 255.255.255.0 (indiquer se port comme la gateway de la vlan 10)
router(config-if))# exit
```

--------------------------

Connection entre deux routeur

```
router(config)# interface gigabitEthernet0/0 (designation de l’interface à configurer)
router(config-if)# ip address 10.0.0.1 255.255.255.0 (affectation de l’@IP/mask sur l’interface)
router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2 (config d’une route statique, si tu veux contacter le reseau 192.1268.(2).0 envoye le paquet a 10.0.0.2 )
router(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.254 (config d’une route par défaut (Internet))
```

