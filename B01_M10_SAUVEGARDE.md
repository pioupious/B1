# Sauvegardes

**Définition :**
**La sauvegarde** (backup) est l'opération qui consiste à **dupliquer** et à **mettre en sécurité** les données contenues
dans un système informatique.

Ce terme est proche de deux notions :
- l'enregistrement des données, qui est l'opération d'écriture des données sur un support d'enregistrement durable, tel qu'un disque magnétique ou SSD, disque optique, une clé USB, des bandes magnétiques, etc. à des fins de sécurité ou d’hébergement de la donnée vivante on parle alors de stockage.
- l'archivage, qui consiste à enregistrer des données sur un support à des fins légales ouhistoriques.

-----------------------

## Pourquoi sauvegarder 

**La sauvegarde des données préserve l'activité de l'entreprise**, notamment en cas de défaillance du système informatique.

L'entreprise peut faire face à plusieurs types de risques qui mettent en danger ses données :
- **Risques humains :** la perte ou le vol d'un appareil dont les données sont liées à celles de l'entreprise, une mauvaise manipulation entraînant l'effacement de données sensibles, piratage des données… ;
- **Risques liés à l'environnement :** perte de données suite à un incendie dans les locaux de l'entreprise, catastrophes (incendies,inondations…)
-  **Risques liés aux dysfonctionnements matériels :** perte d'un serveur par exemple.

-----------------

**Les enjeux de la sauvegarde :**
En cas de pertes de données, l'impact financier peut être notable pour l'entreprise en raison de la disparition de fichiers ou d'applications sensibles (base de données clients, rapports financiers, etc.), ou de la perte de temps engendrée
par la remise en ligne de ces données, l'impact humain psychologique (stress, réecriture des données perdues,
peur de perdre son travail) et l'impact sur l'image de marque ( perte de confiance de la clientèle).

Quels sont les enjeux d'une sauvegarde des données pour l'entreprise ?
- Sauvegarder son image de marque auprès de ses clients ou de ses partenaires 
- Assurer une productivité constante et son chiffre d'affaires 
- Garantir la disponibilité d'informations sensibles : un fichier client en cas de piratage par exemple

----------------------

**Règle de sécurisation**

 La règle dites "3-2-1" pour les sauvegardes. Une méthode fiable et très facile à suivre :
 
- **Conserver 3 copies** de vos fichiers
(les fichiers originaux stockés sur le
disque dur de l’ordinateur et deux
sauvegardes),

- Sauvegarder les fichiers sur **2 types
de supports différents**. Il existe en ef-
fet de nombreux supports différents
pour la sauvegarde de vos données
(NAS, disques durs externes, mé-
moire flash, bandes magnétiques,
DVD, le cloud ...),

- Conserver dans 1 copie de sauvegarde **hors ligne** : Une sauvegarde dite
hors ligne est une sauvegarde sur un support déconnecté de tout SI. La
bande magnétique reste le moyen le plus efficace encore aujourd’hui pour
cet usage..

Et pour plus de sécurité la sauvegarde 3-2-1-1-0

- Externaliser 1 des support hors du site
- 0 avoir aucune erreur lors des test de restauration

## Les paramètres pour la sauvegarde

 - **Rétention des sauvegardes préconnisée :** Désigne la durée pendant laquelle une copie de sauvegarde est conservée avant d’être supprimée ou écrasée.
La stratégie de sauvegarde doit notamment définir les durées de rétention des sauvegardes. Cette stratégie
précise la répartition à long terme : 15 jours de sauvegardes journalières, 1 an de sauvegardes mensuelles,
5 ans de sauvegardes annuelles par exemple.

- **PDMA :** la perte de données maximale admissible se quantifie en heure. Il faut définir la perte de données maximale admissible en cas
d’incident (PDMA=RPO Recorvery point objective) c’est la durée maximale acceptable entre la dernière sau-
vegarde et l’incident survenu quantifiant donc la perte de données acceptée.

- **DIMA :** Le délai d’interruption maximal admissible (ou DMIA) d’une ressource comprends, le temps de la
prise de décision du passage en mode secours après l’incident, le délai de la relance de la ressource et de la
restauration de ses données. DIMA = RTO ( recovery time objective)


## Type de sauvegarde

- Sauvegarde synchrone : Chaque modification de données sur le sys-
tème principal est immédiatement répliquée sur le système de sauvegarde en temps réel, et l’opération
n’est considérée comme terminée qu’une fois la sauvegarde confirmée.


**Avantages :** Aucune perte de données (zéro perte ou très proche) ;Très haute disponibilité.

**Inconvénients :** Ralentit les performances car il faut attendre la validation de la sauvegarde ;Consomme
beaucoup de bande passante ; nécessite une infrastructure très fiable (faible latence).


- **Sauvegarde asynchrone :** Enregistrer d’abord les données localement,
puis à les transférer vers le système de sauvegarde après un délai (quelques secondes, minutes ou plus), sans
bloquer l’activité principale.

**Avantages :** Moins d’impact sur les performances du système source ; Plus souple au niveau réseau (moins
de bande passante instantanée requise).

**Inconvénients :** Risque de perte de données entre deux synchronisations (période de latence); Moins adap-
tée aux systèmes critiques en temps réel.


- **WORM – Write Once Read Many :**WORM (Write Once Read Many) est une technologie de stockage qui per-
met d’écrire des données une seule fois et de les lire autant de fois que nécessaire, sans possibilité de modi-
fication ou suppression.L'objectif est de garantir l’intégrité et la pérennité des données, notamment à des
fins de conformité réglementaire (ex : finance, santé, justice…).


**Avantages :** Empêche toute falsification ou suppression accidentelle ou malveillante ;Conforme aux exigences
de conservation légale (ex : audit, archivage réglementaire).

**Inconvénients :** Pas de mise à jour possible : si des données changent, il faut créer une nouvelle version. Es-
pace potentiellement utilisé inutilement si mal géré.

##  Typologie des Sauvegardes


