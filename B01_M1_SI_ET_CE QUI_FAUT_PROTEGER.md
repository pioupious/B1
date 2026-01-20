# SI

## ENJEUX DE LA SECURITE ET TRIADE DIC

**D :** Disponibilté
**I :** Intégrité
**C :** Confidentialité 

**La sécurité d'un SI**
--------------------------------

**définition :** l'ensemble des meusure techniques, organisationnelles et humaines visant à protéger le système d'information contre les risque susceptibles d'affecter la disponnibilité, l'intégriter, et la confidentialité des information.

**Points clés**:
- La sécu n'est pas uniquement technique
- Elle concerne tout les SI pas seulement les serveur ou les données
- Elle vise a réduire les risque, pas a les supprimer totalement

**Pourquoi la sécu est indispensable ?**
- des interruption d'activité
- des pertes financières
- des sanctions juridiques
- une dégradation de l'image
- une perte de confiance( client, partenaire, salariés )
  
**Biens supports** 
--------------------------------
Les biens supports sont les ressources matérielles, logicielles ou humaines qui permettent le fonctionnement du
Système d’Information. Ils ne représentent pas directement la valeur stratégique pour l’organisation, mais sont
indispensables pour que les biens essentiels soient disponibles, accessibles et exploitables.

Un bien support est remplaçable ou réparable. Sa perte ou son indisponibilité entraîne une dégradation du
service mais ce n'est pas une perte définitive de valeur stratégique (tant que les biens essentiels ne sont pas
altérés).

**Exemples**
- Matériels : serveurs, postes de travail, équipements réseau, périphériques
- Logiciels : systèmes d’exploitation, logiciels de sauvegarde, outils de virtualisation
- Infrastructures réseau : câblage, routeurs, switchs
- Prestations : services de maintenance, infogérance, fournisseurs d’accès internet

**Biens essentiels**
------------------------------------
Les biens essentiels sont les informations, services ou ressources stratégiques qui ont une valeur directe pour
l’organisation. Ils représentent le coeur de l'activité et leur compromission peut impacter lourdement
l’entreprise (perte financière, perte d’image, arrêt de production, ...).

Ces biens doivent être protégés en priorité : **disponibilité, intégrité et confidentialité** sont essentielles. Leur
compromission a des conséquences directes sur l’activité, parfois même vitales pour l’organisation.

**Exemples**

- Données sensibles : données clients, données financières, informations stratégiques
- Services métiers critiques : site e-commerce, outil de facturation, service de messagerie professionnel
- Applications métiers stratégiques : ERP, CRM, bases de données clients
- Documents juridiques et confidentiels

-------------------------------------

**Pourquoi ?**

Cette classification est utilisée dans les démarches d'analyse de risques pour :
- identifier les priorités de sécurisation
- définir les plans de continuité et de reprise d'activité
- affecter les ressources en fonction de la criticité

--------------------------------------

## LE D.I.C

La triade DIC (Disponibilité, Intégrité, Confidentialité) est un modèle de référence permettant de définir les
objectifs de sécurité applicables aux informations et aux systèmes.
Disponibilité, Intégrité et Confidentialité sont trois notions fondamentales lorsque l’on évoque la sécurité des
systèmes d’information car elles définissent les principes fondamentaux de la protection des informations.
Chaque critère DIC apporte son niveau de sécurité à un actif du SI.


**D = Disponibilitée (Avalability)**
------------------------------------------
La disponibilité signifie que l’information ou le service est **accessible et utilisable** par les personnes autorisées, **au
moment où elles en ont besoin.**

**Exemples :**
- Un logiciel métier indisponible
- Un serveur en panne
- Une coupure Internet
- Un ransomware bloquant les systèmes

| Impacts     | Menaces        | Moyens de protection          |Points clés |                              
|---------------|--------------|-------------------------------|------------|
|Arrêt ou ralentissement de l’activité / Perte de productivité / Retards de livraison / Insatisfaction clients / Perte de chiffre d’affaires  | Panne matérielle / Attaque par déni de service (DDoS) / Erreurs humaines | Redondance des systèmes (cluster, backup, RAID, alimentation électrique de secours) / Plan de reprise d’activité (PRA) et Plan de continuité d’activité (PCA) / Surveillance et supervision du SI (monitoring, alertes) | La disponibilité est souvent la priorité numéro 1 pour les métiers / Elle dépend autant du matériel que de l’organisation (sauvegardes, procédures) / Un système très sécurisé mais inutilisable n’a aucun intérêt |

**I = Intégritéer (integrity)**
--------------------------------

L’intégrité signifie que l’information est **exacte, complète, cohérente** et n’a pas été modifiée de manière non
autorisée.

**Exemples**
- Modification involontaire d’une facture
- Altération d’une base de données
- Erreur de saisie non détectée
- Code source modifié sans contrôle

| Impacts     | Menaces        | Moyens de protection          |Points clés |                              
|---------------|--------------|-------------------------------|------------|
|Impacts d’un défaut d’intégrité / Décisions erronées / Problèmes comptables / Litiges clients ou fournisseurs / Perte de confiance interne / Risques juridiques | Modifications non autorisées (piratage, virus, ransomware) / Erreurs humaines (saisie incorrecte, suppression accidentelle) / Corruption des fichiers (problèmes matériels ou logiciels) | Contrôle d’accès rigoureux (droits d’administration restreints) / Signature numérique et hachage (MD5, SHA-256 pour vérifier l’intégrité) / Journaux d’audit (logs pour tracer les modifications) | L’intégrité est essentielle pour la fiabilité du SI / Elle concerne autant les erreurs humaines que les attaques / Les mécanismes de validation et de contrôle sont essentiels 


**C = Confidentialité (confidentiality)**
-----------------------------
La confidentialité signifie que l’information n’est **accessible qu’aux** personnes, systèmes ou entités **autorisés**

**Exemples**
- Fuite de données clients
- Accès non autorisé aux salaires
- Vol de fichiers confidentiels
- Envoi d’un email à un mauvais destinataire

| Impacts     | Menaces        | Moyens de protection          |Points clés |                              
|---------------|--------------|-------------------------------|------------|
|Atteinte à la vie privée / Sanctions réglementaires (RGPD) / Perte de confiance des clients / Atteinte à l’image de l’entreprise/ Avantage concurrentiel perdu | Fuites de données (vol d’informations sensibles) / Attaques par interception (écoute réseau, phishing) / Mauvaise gestion des accès (mot de passe trop simple, partage involontaire d’informations) | Chiffrement des données (AES, RSA, TLS pour sécuriser les communications) / Gestion stricte des accès (authentification forte, 2FA, contrôle des permissions) / Sensibilisation des utilisateurs (formations sur la cybersécurité) | La confidentialité est souvent l’enjeu le plus médiatisé / Elle concerne autant les données numériques que les documents papier
/ Le contrôle des accès est fondamental |


## La quatrième notion
