# Sécuriser le saint réseau

**Objectif**

- Empêcher des connexions non autorisées sur les ports des commutateurs.
- Limiter les risques d'intrusion physique (e.g.: quelqu'un qui branche son laptop).

## Outils

**Le Port Security** sur un switch Cisco a pour objectif principal de sécuriser un port d’accès
(souvent relié à un PC, une imprimante, un téléphone IP…) en contrôlant quelles adresses MAC
ont le droit de l’utiliser;

Objectifs principaux:
- Limiter le nombre d’équipements connectés sur un port; e.g. empêcher qu’un utilisateur
branche un switch/hub et connecte plusieurs machines
- Empêcher les connexions non autorisées; Uniq. Les @MAC autorisées (statiques ou apprises)
peuvent accéder au réseau
- Protéger contre le MAC flooding (CAM* table overflow); Port-security limite les @MAC
apprises → réduit le risque d’attaque visant à forcer le switch à diffuser comme un hub
- Détecter et bloquer les changements suspects de machines; Si quelqu’un débranche un PC et
branche un autre appareil, le switch peut déclencher une action
- Appliquer une réaction automatique en cas de violation; Selon le mode choisi, le switch peut
juste bloquer les nouvelles MAC (protect),bloquer et logguer (restrict) ou mettre le port en errdisable
(shutdown)

**En résumé** : Port Security sert à contrôler l’accès au réseau au niveau du port en se basant sur les
@MAC, pour éviter les connexions non prévues et limiter les attaques de couche 2.

## Mise en place 

On va **utiliser le port-security** pour contrôler les adresses MAC sur les ports et utiliser l’option **sticky** pour apprendre dynamiquement @MAC et les rendre persistantes.

```
switch(config)# interface FastEthernet0/2
switch(config-vlan)# switchport port-security
switch(config-vlan)# switchport port-security maximum 1 "1 seule (*) @MAC autorisée!"
switch(config-vlan)# switchport port-security violation shutdown
```
*Resume: On transforme le port fa0/2 en port secure et on autorise un max d'address max a 1. Si le nombre d'address mac est dif le port se shutdown*

-----------------------------------------

Option **sticky** permet apprendre dynamiquement les @MAC et les rendre persistantes !!! c'est beaucoups plus simple !!!

```
switch(config)# interface fa0/1
switch(config-if)# switchport mode access
switch(config-if)# switchport access vlan 10
switch(config-if)# switchport port-security
switch(config-if)# switchport port-security maximum 1
switch(config-if)# switchport port-security mac-address sticky
switch(config-if)# switchport port-security violation shutdown
end
```


**Bonne Pratiques :** Appliquer Port-Security uniquement sur les ports de type access.

## Les différents ports

**Principe :** Le switch va surveiller les échanges DHCP et différencier 2 types de ports:

- **Trusted (de confiance):** port où le DHCP est autorisé
typiquement le port vers le serveur DHCP, vers le routeur
(DHCP relay / ip helper-address)

- **Untrusted (non fiable) :** ports utilisateurs (PC)
par défaut, tous les ports sont untrusted

**Le switch bloque surtout :** DHCP Offer / DHCP Ack venant d’un port untrusted (potentiellement
un faux serveur DHCP) limite le débit DHCP pour éviter les floods.

**Étape 1 :** Activer DHCP Snooping globalement

```
switch#conf t
switch(config)# ip dhcp snooping
```
**Étape 2 :** Activer DHCP Snooping sur les VLANs concernés

```
switch#conf t
switch(config)# ip dhcp snooping vlan 10,20
```

**Étape 3 :** Déclarer le port “trusted” sur le port vers le serveur DHCP ou le routeur;

```
switch#conf t
switch(config)# interface gi0/1
switch(config-if)# ip dhcp snooping trust
```

**Étape 4 (recommandé):** Limiter le débit DHCP sur ports users éviter qu’un PC flood le switch avec des requêtes DHCP

```
switch#conf t
switch(config)# interface fa0/1
switch(config-if)# ip dhcp snooping limit rate 10
switch(config-if)# end
```

**Étape 5 Contrôle :** Si un switch est connecté à un autre switch (trunk), le port trunk vers l’amont doit être trusted, sinon les réponses DHCP risquent être bloquées!!

```
switch#conf t
switch(config)# interface gi0/2
switch(config-if)# switchport mode trunk
switch(config-if)# ip dhcp snooping trust
```

**Trust** uniquement les ports du switch ou l’on est sûr!

*Exemple :*

```
Switch(config)# ip dhcp snooping
Switch(config)# ip dhcp snooping vlan 10
Switch(config)# interface FastEthernet0/24
Switch(config-if)# ip dhcp snooping trust
Switch(config)# interface range FastEthernet0/1 – 23
Switch(config-if)# ip dhcp snooping limit rate 15
```
**!!!! EVITER LES BOUCLES !!!!**

```
switch(config-if)# spanning-tree portfast
switch(config-if)# spanning-tree bpduguard enable
switch(config-if)#
```

## Le DAI

**Principe du DAI :** Vérification des paquets ARP qui circulent sur le switch
**But :** Empêcher qu’un hôte envoie des réponses ARP mensongères du type

!! **Comment le switch décide si un ARP est “vrai” ?** !!
DAI compare les infos ARP avec une base de confiance :
- DHCP Snooping Binding Table (le plus courant)
- DHCP Snooping doit être activé avant DAI (sinon DAI ne sait pas quoi vérifier)

**Trusted :** ports où on accepte les ARP sans contrôle strict
uplink vers routeur, serveur, switch distribution
**Untrusted :** ports utilisateurs (PC)
DAI inspecte et bloque si incoherent
!!!!!**Par défaut : tous les ports sont untrust**!!!!!

```
switch#conf t
switch(config)# ip arp inspection vlan 10,20
switch(config)# interface gi0/1 
switch(config-if)# ip arp inspection trust
switch(config)# interface fa0/1 
switch(config-if)# ip arp inspection limit rate 15
switch(config)# end
```

## Autre Aspect important 

Regrouper tiout les ports non utiliser dans un vlan Poubelle ne surtout pas les laisser dans leur vlan native.

**Exemple :**
```
switch# conf t
switch(config)# vlan 999
switch(config-vlan)# name PARKING_UNUSED
switch(config-vlan)# exit
switch(config)# interface range fa0/10 - 24
switch(config-if)# switchport mode access
switch(config-if)# switchport access vlan 999
switch(config-if)# shutdown
switch(config-if)# end
```

Configurer routeur ou switch en DHCP :

```
ip dhcp excluded-address 192.168.10.1 192.168.10.20 # On exclude 2 address
ip dhcp excluded-address 192.168.20.1 192.168.20.20 # On exclude 2 address
ip dhcp pool VLAN10_USERS 
network 192.168.10.0 255.255.255.0 
default-router 192.168.10.1 # Le plus important pour indique la vlan
(router(config-vlan)#iphelper-address 10.0.0.10 #faire un relay vers 10.0.0.10)
dns-server 8.8.8.8
exit
```

Pool DHCP :

```
router(config)# ipdhcppool LAN10
router(dhcp-config)#network 192.168.10.0 255.255.255.0
router(dhcp-config)#default-router 192.168.10.254
router(dhcp-config)#dns-server 1.1.1.1 8.8.8.8
router(dhcp-config)#domain-name entreprise.local (optionnel)
router(config)#lease 7 # bail de 7 jours
```

## Acces list (ACL)

**ACL Standard**

```
access-list standard [numéro]
access-list# [numéro] {permit | deny} [source] [wildcard]

access-list standard 1
access-list# 10 permit tcp 192.168.1.0 0.0.0.255 eq 80
access-list# 20 deny any 'or' access-list 1 permit any
```

**ACL Étendue**

```
access-list range [numéro]
{permit | deny} [protocole] [source] [wildcard] [destination] [wildcard] [eq numéro_port]

access-list range 2
access-list# 10 permit tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.255.255.255 eq 80
access-list# 20 deny any 'or' access-list 100 permit any
```

**Appliquer l'ACL à une Interface**

```
interface [interface]
ip access-group [numéro] {in | out}

interface GigabitEthernet0/0
ip access-group 100 in

```

**in vs out**
**in :**
- Indique que l'ACL est appliquée au trafic entrant sur l'interface.
- Cela signifie que tous les paquets qui entrent dans l'interface seront filtrés par l'ACL.ex
- Utilisé pour contrôler qui peut accéder à des services ou des ressources sur le réseau interne.
**out :**
- Indique que l'ACL est appliquée au trafic sortant de l'interface.
- Cela concerne tous les paquets qui quittent l'interface et vont vers un réseau externe.
- Utilisé pour contrôler quel trafic est autorisé à sortir de votre réseau vers l'extérieur.
