# 1. RESILIENCE DU SI 

**A FAIRE : https://pix.fr/**

**Une crise cyber** se caractérise par certaines particularités qu’il est important d’appréhender pour être mieux
préparé :
- la mise en péril des objectifs prioritaires de l’organisation ;
- la fulgurance des impacts et le manque de temps pour y répondre ;
- la technicité du sujet, du fait de la complexité des systèmes d’informations et des modes opératoires
utilisés par les attaquants ;
- l’évolutivité de l’évènement, dans la mesure où les attaquants sont susceptibles de réagir aux actions
entreprises par l'organisation ciblée.

**La sortie de crise** peut être longue, puisque la réponse technique, l’investigation numérique et le rétablissement
du fonctionnement des systèmes d’informations sont des actions qui peuvent prendre plusieurs mois.il est nécessaire de se préparer, s’outiller, s’entrainer et de
connaître les bonnes pratiques de gestion de crise. Pour ce faire, il convient de :

- S’assurer de l’existence d’un plan de continuité d’activité
(PCA) robuste aux cyberattaques et d’un plan de reprise
d’activité (PRA) ;
- Préparer les capacités de réponse à incident, y compris en
cas de perte des moyens informatiques et de communication
nominaux ;
- Anticiper les menaces cyber et adapter le dispositif de
crise à ces menaces ;
- Formaliser une stratégie de communication cyber ;
- S’entrainer pour pratiquer et s’améliorer ;
- Contractualiser le cas échéant des prestations de réponse à incident et souscrire une assurance cyber.

**Protection :** **Se prémunir** contre les attaques en rendant le SI et son écosystème les moins vulnérables et exposés possibles
**Défense :** **Détecter** les signaux faibles ou une attaque avérée et **réagir** pour en minimiser les impacts
**Résilience :** Assurer la **continuité** d'activité avec un niveau de dégradation tolérable, puis la **reprise** nominale progressive 
**Gouvernance :** **Anticiper** la menace, suivre le niveau de sécurité et **renforcer** en continu le dipositif

## **Notion importante**

**La résilience d’un Système** d’Information (SI) désigne sa capacitéà continuer de fonctionner face aux aléas, incidents ou attaques,et à revenir rapidement à un état stable.
**Elle se construit autour de trois notions fondamentales, qui ensembletraduisent la robustesse d’un système face aux aléas** :
- **La disponibilité** : c’est la capacité du système à assurer le service
attendu, en temps réel, pour les utilisateurs, sans interruption.
- **La tolérance aux pannes** : c’est la capacité du système à continuer de fonctionner même lorsqu’une partie de ses
composants est défaillante, en absorbant les erreurs ou en basculant sur des alternatives.
- **La continuité d’activité** : c’est la capacité de l’organisation à maintenir ou rétablir son fonctionnement en cas de
crise majeure, en s’appuyant sur des plans prévus à l’avance.
Ces trois notions sont les briques concrètes de la résilience.

**Assurer une resiliance !! = les Sauvegardes**

## Disponibilité  

**La Disponibilté** est la capacité d’un système à être accessible et opérationnel lorsque l'utilisateur ou le métier
en a besoin.

**Solutions :**
- Répartition de charge (Load Balancer)
- Mécanismes anti-DDoS (Cloudflare, Arbor, Akamai)
- Redondance de serveurs
- Sauvegardes

**Cas concret :** Un site e-commerce doit rester accessible pendant le Black Friday. Une attaque DDoS (déni de
service) tente de saturer le serveur pour le rendre indisponible.

## Tolérance aux Pannes 

**La Tolérance aux pannes** est la capacité d’un système à continuer de fonctionner malgré une panne partielle.

**Solutions :**
- Virtualisation (VMWare, Hyper-V)
- Réplication des données (RAID, SAN)
- Clustering / Haute Disponibilité (HA).

**Cas concret :** Un disque d'un serveur tombe en panne, mais le serveur continue à fonctionner en annonçant
son mode dégradé.

## **Continuité d’Activité**

**La continuité d’Activité** est l'organisation permettant de maintenir un service minimum en cas d’incident
majeur.

**Solutions :**
- Plan de Continuité d'Activité (PCA)
- Sites secondaires / PRA.
- Tests de bascule réguliers.

**Cas concret :** Un centre de traitement des paiements est compromis. Les opérations sensibles sont basculées
sur un site de secours.

## **Identification des Risques**

Processus permettant d’analyser et classer les menaces potentielles.

**Solutions :**
- Méthode **EBIOS Risk Manager**
- Cartographie du SI.
- Simulations de crises (table-top, Red Team).

**Cas concret :** Cartographie des risques internes et externes avant la mise en production d’un système.

## **Défense en Profondeur**

**La défense en profondeur** est une approche de sécurité consistant à multiplier les couches de protection.

**Solutions :**
- Segmentation réseau.
- Authentification forte (MFA).
- Supervision et détection des incidents (SIEM).

**Cas concret :** Même si un pirate passe le pare-feu, l’authentification MFA empêche l’accès aux données.

## PCA (Plan de Continuité) / PRA (Plan de Reprise)

**Définitions :**
- **PCA :** garantir une activité minimale en temps de crise.
- **PRA :** restaurer les systèmes et les données après une panne ou attaque

**Solutions :**
- Backups hors-ligne.
- Sites de secours géographiques.
- Exercice de crise.

**Cas concret :** Suite à une attaque par ransomware, un PRA permet de restaurer les serveurs à partir des
sauvegardes non chiffrées.

# **Conclusion**
- La résilience est une combinaison de prévention, d'entraînement, de détection et de réaction.
- Elle s’appuie sur des pratiques normées : ANSSI, ISO, NIS2.
- Les incidents réels montrent que les systèmes non préparés sont vulnérables
