# TP 3 : TDD

## Objectif 🏁

- Réalisez les différents exercices en appliquant la TDD.

## Rendu 📮

- Créez un répo GitHub pour le TP
- Vous devez réaliser un commit après chaque test (= test rouge)
- Vous devez réaliser un commit après chaque implémentation (= test vert)

> NB : si vous ne faite pas de commit à chaque étape, rien ne prouve que vous avez suivi la TDD !

## Evaluation 📝

Vous serez évalué sur :
- Le respect du cycle de la TDD
- Le respect des bonnes pratiques
- La pertinence de vos tests
- La qualité des commits

### Suggestion : 

Pour l'ajout de tests qui échouent : `git commit -m "test : nom du test :test_tube:"`
Pour l'ajout de test qui passe : `git commit -m "test : nom de la feature :white_check_mark:"`
Pour une feature terminée: `git commit -m "feat : nom de la feature :sparkles:"`

> En cas d'oubli de commit, vous serez pénalisé !

## Exercices 📚

### Exercice 1 : Thermomètre 🌡️

Vous devez réaliser un thermomètre qui permet d'indiquer la température la plus proche de 0.

#### Contraintes 

- Elle prendra en paramètre un tableau d'entiers
- On ne peut pas passer plus de 10000 mesures, sinon on lève une exception
- En cas d'égalité, on prendra la température positive
- Si le tableau est vide, on retourne `0`

#### Exemple

- `[]` retourne `0`
- `[1, 2, 3]` retourne `1`
- `[-2, -8, 4, 5]` retourne `-2`
- `[-1, -2, -8, -4, 2]` retourne `2`

### Exercice 2 : La stack 📚

- Vous devez réaliser une stack qui permet de stocker des entiers.
- Elle doit permettre de :
  - `push` : ajouter un élément
  - `pop` : retirer le dernier élément
  - `peek` : retourner le dernier élément sans le retirer
  - `isEmpty` : vérifier si la stack est vide
  - `isFull` : vérifier si la stack est pleine

#### Contraintes

- La stack doit être implémentée avec un tableau (new int[10])
- On ne peut pas ajouter plus de 10 éléments

> Interdiction d'utiliser une implémentation de List ou autre ! Vous **devez** utiliser un tableau !

#### Exemple

```java
Stack stack = new Stack();
stack.push(1);
stack.push(2);
stack.push(3);
stacl.peek(); // 3
stack.pop(); // [1, 2]
stack.isEmpty(); // false
stack.isFull(); // false
stack.pop(); // [1]
stack.pop(); // []
stack.isEmpty(); // true
```

### Exercice 3 : De Nombre Arabe vers Nombre Romain 🏛️

- Vous devez réaliser un convertisseur de nombre arabe vers nombre romain

#### Contraintes

- Le nombre doit être compris entre 1 et 3000, sinon on lève une exception
- Le nombre doit être un entier, sinon on lève une exception
- Le nombre doit être positif, sinon on lève une exception
- Si on essaie de convertir autre chose qu'un nombre : on lève une exception

#### Exemple

> 1 --> I  
> 7 --> VII  
> 10 --> X  
> 49 -> XLIX  
> 847 -> DCCCXLVII  
> 1053 -> MLIII  
> 1776 -> MDCCLXXVI  
> 2018 -> MMXVIII  

