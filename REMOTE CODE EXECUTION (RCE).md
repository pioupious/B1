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
