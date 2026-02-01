# Part 01

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

# Part 03

```
#exercie 18

def carre(n):
    return n*n

n=int(input("entrer un nb : "))
print ("votre nombre au carré est : ",carre(n))

#exercice 19
h=float(input("Hauteur du rectangle : "))
l=float(input("Largeur du rectangle : "))

def air(h,l):
    return h*l

print ("L'air est de ", air(h,l))

-----------------------

#exercice 20

def pair(n):
    if n % 2 ==0:
        return "paire"
    else:
        return "impaire"
n=int(input("Entrer un nombre : "))
print ("votre nombre est", pair(n))


-------------------

#exercice 21

def menu():
    return print (f"""  #MENU#
1-Démarrer

2-Arrêter

3-Quitter""")

menu()
```
# Part 04
```
#exercice 22

import string

somme = 0
i = 0
n = input("Entrer une note : ")

while (n != ""):
    
    nint = int(n)
    somme = somme + nint
    i = i + 1
    n = input("Entrer une note : ")
    
    
moyenne = somme/i
print("La Mayenne est de : ", moyenne)
if (moyenne <= 10):
    print ("vous etes refusé ! (petite merde)")
else:
    print ("Bien joué champion !!")
    
--------------------

#exercice 23


def verifa (n):
   if n>18:
       return print ("your are free ! welcome to work !")
   else:
       return print ("Cest pas grave mon petit bébé cadum")
n=int(input("Quel age as tu ? "))
verifa (n)

-------------------

#exercice 24

def compt (n):
    for i in range (1,n+1):
        print (n-i)
    return print ("Décollage !!!")

n=int(input("Donner un compte a rebour : "))
compt (n)
```

# Part 05

```
#exercice 25

def age(n):
    return (n+5)
n=int ( input ( "Quel age as tu ? "))
print (f""" Dans 5 ans, tu auras {age(n)} ans.""")

----------------------

#exercice 26

def convertion(n):
    return (n*9/5+32)
n=float(input("Quelle température avez vous en Celcius ? "))
print (f"""Il fait donc {convertion(n)} degrés Fahrenheit""")


----------------------------

#exercice 27

liste =[]

n = input("Entrer un nombre : ")

while (n != ""):
    nint = int(n)
    if ((nint % 2) == 0 ):
        liste.append(nint)
    n = input("Entrer un nombre : ")
print ("Les élément paire de votre liste sont ",liste)


--------------------------------------
    
#exercice 28

test = ["+","-","*","/"]
print ("bonjours je suis une calculculatrice !!")

n1= float ( input ("veuillez rentrer une première valeur : "))

calc = str (input(" Quelle opératiopn voulez vous faire ? (+, -, *, /)"))

while (calc not in test):
    calc = str (input(" Quelle opératiopn voulez vous faire ? (+, -, *, /)"))

if calc == "/":
    n2= float ( input ("veuillez rentrer une deuxième valeur : "))
    while (n2 == 0.0):
        n2= float ( input ("veuillez rentrer une deuxième valeur : "))
else :
    n2= float ( input ("veuillez rentrer une deuxième valeur : "))
    

if  calc == "/": print (f""" Le résultat de votre calcul : {n1} {calc} {n2} = """, n1 / n2 )
if  calc == "+": print (f""" Le résultat de votre calcul : {n1} {calc} {n2} = """, n1 + n2 )
if  calc == "-": print (f""" Le résultat de votre calcul : {n1} {calc} {n2} = """, n1 - n2 )
if  calc == "*": print (f""" Le résultat de votre calcul : {n1} {calc} {n2} = """, n1 * n2 )

-------------------------------

#exercice 29

import random
import string


l=string.ascii_lowercase
L=string.ascii_uppercase
N=string.digits
c=string.punctuation
mdp=""
n=int(input("Nombre de charactère du mots de passe : "))
for i in range (1,n):
    r=random.randint(1,4)
    if r==1:
       r=random.choice(l)
    if r==2:
        r = random.choice(L)
    if r==3:
        r = random.choice(N)
    if r==4:
        r = random.choice(c)
    
    mdp = mdp + r
print ("votre nouveau mots de passe : ",mdp)



--------------------


#exercie 30

import random

i=0

valeur = random.randint(1, 99999)
trouve = False

print (valeur)

print ("Votre nombre est comprit entre 1 et 99999")


n = int(input("entrer un nombre : "))


while ( trouve == False):
    
    i=i+1
    
    if (n < valeur):
        print (" c'est plus grand !!")
        n = int(input ("entrer un nombre : "))
        
        
    elif (n == valeur) :
        trouve = True
        
    else :
        print (" c'est plus petit !!")
        n = int (input ("entrer un nombre : "))
        
   
    
print ("Bravo le nombre était " , valeur )
print ("Votre nombre d'essai est : " , i )
```
