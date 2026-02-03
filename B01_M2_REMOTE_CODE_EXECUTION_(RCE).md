# REMOTE CODE EXECUTION (RCE)

**Qu'est ce que c'est ?**

Une Remote Code Execution (RCE) est une vulnérabilité qui permet à un attaquant de provoquer l’exécution de
code choisi par lui sur un système distant, en fournissant des données spécialement construites qu’un
programme va interpréter comme des instructions.
 
 -------------------
 
**Points clés**

1. L’attaquant n’exécute pas directement du code :
  - Il n’a pas accès au shell ou au binaire  
  - Il ne peut envoyer que des données (requête HTTP, fichier, paramètre, message réseau)
**Le code exécuté l’est par l’application vulnérable elle-même**

2 Il influence un algorithme qui va interpréter sa donnée
Le programme :
  - parse → transforme des données en vrac et non structurées en un format structuré et exploitable
  - évalue
  - compile
  - désérialise
  - ou exécute
une donnée non prévue pour contenir du code
**La frontière donnée / code est brisée***


**Exemple :**
Ce que le développeur pense :
  - L’utilisateur fournit une adresse, je fais un ping
Ce que fait l’attaquant
  - Il envoie comme entrée : 8.8.8.8 ; supprimer_fichiers()

Entrée contrôlée par l’attaquant ✅
Interprétation comme instructions ✅
Exécution sur la machine distante ✅
Contrôle du comportement ✅


Entrée utilisateur
↓
Traitement insuffisant
↓
Interprétation
↓
Exécution

## Distinguer données et commandes

Une donnée décrit quelque chose. Une commande demande de faire quelque chose. **Le problème de sécurité apparaît quand une donnée est interprétée comme une commande.**


**Nom de fichier vs commande système**

Si un programme attend un nom de fichier mais le transmet directement à un mécanisme qui exécute des
commandes alors une donnée peut devenir une instruction cachée. **Ce qui devait désigner une chose devient une action exécutée par le système**
Exemple : nom de fichier qui est du code

**Paramètre attendu vs instruction**

Si un paramètre est interprété dynamiquement ou injecté dans un contexte d’exécution, il peut changer la
logique du programme. **Un paramètre doit influencer des données, pas piloter le comportement du moteur d’exécution**

**Exécution de commandes externes**

**Le programme délègue une action au système d’exploitation**
- Il sort de son environnement
- Il demande au système d’exécuter quelque chose
- Il fait confiance à la commande fournie

Pourquoi c’est sensible :
- Le système a beaucoup de privilèges
- Toute partie dynamique devient critique
- Une entrée mal contrôlée peut devenir une commande complète
**Le programme ouvre une porte directe vers le système.**

**Évaluation dynamique**

**Le programme :**
- reçoit une expression
- l’analyse
- et l’exécute comme du code

Pourquoi c’est sensible
- La frontière donnée / code disparaît
- Toute entrée devient potentiellement exécutable
- Le moteur fait confiance à ce qu’il interprète
 **Ce qui est évalué n’est plus une donnée mais une logique active**

**Chargement dynamique de code**

**Le programme charge du code au moment de l’exécution au lieu de l’avoir défini à l’avance :**
- un module
- une bibliothèque
- un script
- un composant externe

**Pourquoi c’est sensible**
- Le contenu chargé n’est pas toujours maîtrisé
- Le programme exécute quelque chose qu’il ne connaît pas à l’avance
**Le programme accepte d’exécuter du code venu d’ailleurs**


**Templates interprétés**
**Un template est censé :**
- afficher des données
- produire du texte (HTML, mail, document, …)
Mais certains templates :
- contiennent une logique
- interprètent des expressions
- exécutent des instructions
- 
**Pourquoi c’est sensible :**

Une donnée injectée dans un template peut être interprétée comme une expression et devenir exécutable
**L’affichage devient un moteur d’exécution déguisé**


**Pourquoi la RCE est critique**

**Conséquences possibles**
- Exécution de commandes arbitraires
- Accès aux données
- Rebond dans le SI

**Lien avec les piliers de sécurité**
- Confidentialité : fuite de données
- Intégrité : modification du système
- Disponibilité : sabotage
