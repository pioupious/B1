# Résumé du document

## 1. DMZ (Zone démilitarisée)

**Définition** : Zone intermédiaire entre le réseau interne sécurisé (LAN) et Internet, ajoutant une couche de sécurité pour isoler les services exposés au public.

### Objectifs :
- Isoler les services accessibles depuis Internet (serveurs web, mail, DNS, etc.).
- Réduire la surface d’attaque du réseau interne.
- Appliquer des règles de filtrage différenciées via des pare-feux.
- Contrôler les flux entrants et sortants (ports nécessaires uniquement).
- Contenir les compromissions en limitant l’impact d’une attaque.

### Architecture typique :
- **Modèle à 2 pare-feux (DMZ à 3 tiers)** : le plus sécurisé.
- **Modèle à 1 pare-feu (DMZ à 2/3 tiers)** : plus simple mais moins robuste.

### Bonnes pratiques :
- Segmentation stricte (VLAN, sous-réseaux dédiés).
- Moindre privilège (accès minimum requis).
- Supervision renforcée (logs, IDS/IPS).
- Durcissement des serveurs (patching, désactivation des services inutiles).

---

## 2. Relais DHCP

**Concept** : Le DHCP attribue automatiquement des paramètres IP aux appareils d’un réseau (IP, masque, passerelle, DNS, etc.).

### Fonctionnement :
**Étapes** : Discover → Offer → Request → Ack.  
Utilisation de relais DHCP pour permettre la communication entre VLANs.

### Bonnes pratiques :
- Activer le DHCP Snooping pour éviter les "rogue DHCP".
- Séparer les VLANs (utilisateurs, serveurs, invités).
- Configurer des baux adaptés (courts pour invités, longs pour LAN).

---

## 3. NAT (Network Address Translation)

**Concept** : Traduction des adresses IP privées en adresses IP publiques pour économiser les adresses IPv4 et masquer le réseau interne.

### Types de NAT :
- **NAT statique** : Association fixe 1:1 entre IP privée et publique.
- **NAT dynamique** : Utilisation d’un pool d’IP publiques pour des associations temporaires.
- **PAT (NAT overload)** : Plusieurs IP privées traduites en une seule IP publique via des ports.

### Configurations courantes :
- **PAT** : Tout le LAN sort sur Internet via une seule IP publique.
- **NAT statique** : Permet d’exposer un serveur interne à Internet.
- **Port Forwarding** : Expose un service précis (ex. HTTP).
- **NAT dynamique** : Utilise un pool d’IP publiques.

### CGN (Carrier Grade NAT) :
Utilisé pour surmonter le manque d’adresses IPv4 en traduisant des adresses privées en publiques.  
**DSLite-CGN** : Transition vers IPv6 en encapsulant le trafic IPv4 dans un tunnel IPv6.

---

Ce document fournit des informations détaillées sur la sécurisation des réseaux via DMZ, DHCP et NAT, ainsi que des exemples de configuration pour chaque concept.
