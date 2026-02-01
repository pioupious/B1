# Part01

```
#exercice 1

nom = "Pierre"
ville = "Angouleme"
print( nom + ville )
#exercice 2
a = float (5)
b = float (2.5)
somme = a + b
print (somme)

--------

#exercice 3

connecter = str ("true")
print ( " l'utilisateur est connecté ?", connecter )

--------------

#exercice 4

nom = str ("Pierre")
age = int (18)
print ("je m'appelle", nom, "et j'ai", age, "ans.")
#exercices 5
age = int ( input ( "Quel age avez vous ? " ))
if (age < 18):
            print ("vous etes encore un bébé")
else:
            print ("vous avez déja passer les meuilleurs année de votre vie ...")

---------------

#exercice 6

y = float ( input ("Entré un premier nombre :"))
z = float ( input ("Entrée un deuxième nombre :"))

if (y>z):
    print (y,"plus grand que ", z)
elif (y==z): print ( "tu es tubé les 2 nombres sont egaux")
else:
    print (z,"plus grand que ", y)

-------------------

#exercice 7

p = int (input ("Donner moi un chiffre a manger !!!! "))
if (p %2==0):
    print ("Ton chiffres est paire tu devrais le savoir !")
else :
    print ("Ton chiffres est impaire tu devrais le savoir !")

-----------

#exercice 8

n = int ( input ( "quelle est ta note ?"))
while (0 > n or n > 20):
            n = float ( input ( "quelle est ta note ?"))
if (n >= 16 ):
    print ("Excellent")
elif (n >= 14):
    print ("Bien")
elif (n >=10):
    print ("Bof")
else :
    print ("T NUL !!!")

----------------

#exercice 9

for i in range ( 1, 11):
    print (i)
```

# Part 02

```
#exercice 10

nom = str (input ( "Quel est votre nom ? "))
age = int (input ( "Quel est votre age ? "))
taille = float (input ( "Combien messurez vous ? "))
stagiaire = str (input ( "Etes vous stagiaire y/n ? "))
if (stagiaire == "y" or stagiaire == "yes" or stagiaire == "Yes" or stagiaire == "YES"):
    stagiaire = "true"
else :
    stagiaire = "false"
    
print ("Nom : ", nom )
print ("Âge : ", age )
print ("Taille : ", taille )
print ("stagiaire : ", stagiaire)

--------------

#exercice 11

for i in range (1,11):
 print (11-i)
 
print ("Décolage !!!")

------------------

#exercice 12

nb = int ( input ( "entrer un bombre entier" ))
for i in range (1,11):
    print ( i, " X ", nb, " = ", nb * i)

-----------------------
    
#exercice 13

n = 0
somme = 0
while ( n <  100):
 n = n + 1
 somme = somme + n
print (f""" la somme des entier de  1 à 100 est {somme} """)

-----------------

#exercice 14


enter = "caca"
while ( enter != "stop" ):
    enter = str (input( "veuillez ecrire un mots !!!"))
print ("bravo vous avez stopez le programme")

----------------------

#exercice 15

n = int ( input ("Entrez un nombre :"))
for i in range (1,(n+1)):
     print (i)

------------------
    
#exercie 16
     
enter = "caca"
while ( enter != "secret" ):
    enter = str (input( "veuillez ecrire le mots de passe !!!"))
print ("bravo vous avez donné le mots de passe")

-----------------------

#exercice 17

import random

valeur = random.randint(1, 99999)
trouve = False

print (valeur)
print ("Votre nombre est comprit entre 1 et 99999")

n = int(input("entrer un nombre : "))

while ( trouve == False):
    
    if (n < valeur):
        print (" c'est plus grand !!")
        n = int(input ("entrer un nombre : "))
       
    elif (n == valeur) :
        trouve = True
        
    else :
        print (" c'est plus petit !!")
        n = int (input ("entrer un nombre : "))
print ("Bravo le nombre était " , valeur )
```
