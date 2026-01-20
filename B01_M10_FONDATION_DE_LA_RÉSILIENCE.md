# **FONDATION DE LA RÉSILIENCE**

## A comprendre 
- Comprendre les concepts fondamentaux du stockage et de la redondance.
- Identifier les différents types d'architectures de stockage (DAS, NAS, SAN, Cloud).
- Différencier les architectures locales, distantes et hybrides.
- Comprendre l'intérêt de la redondance physique des systèmes et des données.
- Appréhender les mécanismes RAID et savoir les configurer sous différents systèmes d'exploitation.
- Illustrer par des cas concrets et des exemples d'actualité l'importance du stockage dans la résilience.


## LE STOCKAGE

**Le stockage** fait référence à l'ensemble des méthodes, dispositifs et technologies utilisés pour conserver les
données numériques de façon durable, accessible et sécurisée. Il peut s'agir de supports physiques
(disques durs, SSD, bandes magétiques) ou virtuels (cloud), adaptés aux besoins en performance, capacité,
coût et disponibilité.

**Une stratégie de stockage efficace vise à assurer la conservation intègre des données en toute circons-
tance, y compris lors d'un sinistre ou d'une cyberattaque.**


**DIFFERENT TYPE DE STOCKAGE :**
--------------------------------------------------------
*Peux etre utile : https://www.youtube.com/watch?v=uT7uvxlyxeA*

Il esiste plusieurs **supports de stockages**, associés à des modes de stockage de la données et des utilisations spéci-
fiques :
- **DAS (Direct Attached Storage) :** stockage directement connecté au serveur (ex: disque dur externe)
en mode blocs, pas accessible par le réseau.
- **NAS (Network Attached Storage) :** unité de stockage connectée via réseau, partagée entre plu-
sieurs utilisateurs en mode fichiers.Une PME utilise un NAS pour centraliser les sauvegardes de tous
ses ordinateur.
- **SAN (Storage Area Network) :** réseau spécialisé dédié au stockage, utilisé en entreprise pour per-
formances élevées, en mode blocs.Une multinationale utilise SAN pour ses bases de données cri-
tiques. il sont monté sur un ordi comme un disque réel mais de facon distant, le disque ne sera accessibles que a la machine a laquelle il sera associé (disque delocalisé)
- **Cloud Storage :** stockage mutualisé sur des serveurs distants, administré par un tiers (AWS S3,
Azure Blob, Google Cloud).

**Typologie des Stockages**
----------------------------------------------------
!!!!!  *https://urlr.me/YD-jHBVB*  !!!!!!

Les différents mode de stockage de la donnée :les blocs, les fichiers et les objets. 

**Le stockage en blocs :** Il divise les données en blocs de taille fixe et les stocke individuellement avec une
faible latence, idéal pour les bases de données et les systèmes de fichiers haute performance.

**Le stockage en fichiers :** Il permer d'organiser les données sous forme de fichiers hiérarchisés dans des dos-
siers, comme sur un disque dur classique, adapté au partage de fichiers et aux systèmes NAS.

**Le stockage en objets :** Stocke les données sous forme de données brutes avec métadonnées et identifiants
uniques, optimisé pour l’évolutivité et l’accès via Internet, typique du cloud (comme Amazon S3).

**Les architectures liées au stockage : Locale, Distante, Hybride**
--------------------------------------------------------

- **Locale :** données stockées sur site (serveurs internes), maîtrise de la connaissances du SI.
- **Distante :** données externalisées chez un prestataire ou dans le cloud, perte de la connaissance et
de la maîtrise du SI.
- **Hybride :** combinaison des deux, souvent pour des raisons de performance, coût et sécurité, diffu-
sion de la connaissance du SI.

**Solutions :**
- Veeam, Rubrik, Commvault pour sauvegarde hybride.
- Cloud-native storage (Azure Files, AWS EFS).

**Cas concret :**
- Une startup sauvegarde localement ses données critiques et réplique automatiquement sur AWS
(modèle hybride).
- TV5 qui perd une partie de la maîtrise de son SI en externalisant.

**Redondance Physique**

Duplication des composants critiques pour éviter un point de défaillance unique. Peut s’appliquer aux disques, serveurs, data centers.

**Solutions :**
- Clustering, Load Balancing, Réplication Synchrone/Asynchrone.


**RAID**
------------------------------------------------------------

!!!!!   *https://www.youtube.com/watch?v=WqGeTOt6A0Q*   !!!!!

En informatique, le mot **RAID** désigne les techniques permettant de constituer une unité de stockage à
partir de plusieurs disques durs afin :
- d'améliorer la tolérance aux pannes, la disponibilité ;
- d’améliorer les performances ;
- d’augmenter la capacité des partitions logiques.
**RAID** est l’acronyme de Redundant Array of Independent (or inexpensive) Disks, ce qui signifie « chaîne re-
dondante de disques indépendants »

Il existe le **raid matériel**, géré par une carte contrôleur dédiée et le **raid logiciel** géré par l’OS.

**Visualisation RAID Logiciel :**
- Sur Linux :sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdX /dev/sdY
- Sur Windows : Via Disk Management → Volume Miroir ou Stockage Parité (Storage Spaces).
**Visualisation RAID Matériel :**
- Accès au BIOS/UEFI du contrôleur RAID.
- Outils : MegaRAID Storage Manager / HP SSA / Dell OpenManage.

- **RAID 0 :** Il permet une performance en écriture et en lecture, une grande capacité de stockage,
mais pas de tolérance aux pannes.On parle de "Striping " ou de"volume agrégé par bandes": les
disques physiques sont associés pour ne faire qu'un seul disque logique.
- **RAID 1 :** Il consiste en l'utilisation de n disques redondants (avec n ≥ 2), chaque disque de la grappe
contenant à tout moment exactement les mêmes données, d'où l'utilisation du mot « miroir» (mirroring
en anglais).
- **RAID 5 :** striping + parité, tolérance 1 disque. Il combine la méthode du volume agrégé par bandes
(striping) à une parité répartie. Les données sont entrelacées sur tous les disques de la pile, mais pour
chaque bande de la pile,une unité de bande est réservée pour l’enregistrement de données de parité cal-
culées à partir des autres unités.RAID 5 est devenu la référence pour les environnements de serveurs né-
cessitant une capacité de tolérance aux pannes.
- **RAID 6 :** tolérance aux pannes de 2 disques. Les grappes RAID 6 sont généralement plus lentes que
les RAID 5, car il génère deux jeux d'informations de parité et les stocke sur deux disques différents mais
la probabilité de perte de données est nettement plus faible.
- **RAID 10 :** mirroring + striping (RAID 1 + RAID 0).
- **RAID-Z :** version ZFS, tolérance d'erreurs intégrée. Le chiffre suivant le Z indique le nombre de disque
de tolérance aux pannes. (Z, Z1, 2 et 3).


**Choix du RAID :**
- la sécurité : RAID 1 ou 1+0 et 5 offrent tousles deux un niveau de sécurité élevé ;
- les performances : RAID 1 offre de meilleures performances que RAID 5 en lecture, mais
souffre lors d'importantes opérations d'écriture.
- le coût : le coût est directement lié à la capacité de stockage de la grappe.

**Cas concret :** Un NAS domestique utilise RAID 1 pour assurer la disponibilité des données
en cas de panne d’un disque.

# CONCLUSION

Dans une démarche de résilience, le stockage des données et la redondance sont des piliers fondamen-
taux. La pérennité des services, la récupération après incident et la continuité d'activité dépendent directe-
ment de la manière dont les données sont stockées, répliquées et sécurisées.
Les incidents techniques, les cyberattaques, les erreurs humaines ou encore les catastrophes naturelles
peuvent endommager des systèmes d'information. Une architecture bien pensée de stockage et de redon-
dance limite ces risques et permet une reprise rapide, tout en garantissant l'intégrité des données.

