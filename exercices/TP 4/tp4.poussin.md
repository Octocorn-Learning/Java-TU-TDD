# TP Gilded Rose

## Objectif 🏁

Vous devrez refactorer le code de la Rose Dorée en utilisant la TDD.
Vous disposez d'une classe `GildedRose` qui contient une méthode `updateQuality` qui permet de mettre à jour la qualité des produits.

> Voir le `README.md` de la Rose Dorée pour plus d'informations !

## Rendu 📮

- Créez un répo GitHub pour le TP
- Vous devrez réaliser des commits à chaque étape de la TDD !

> Réaliser autant de commits permet de montrer les différentes étapes. Sans commit, il sera impossible de vous évaluer !

## Evaluation 📝

Vous serez évalué sur :
- L'utilisation d'un Golden Master
- Le respect du cycle de la TDD
- Le respect des bonnes pratiques
- La pertinence de vos tests
- La qualité des commits
- La qualité du code 
- La qualité de la documentation
- La présence d'un README.md

### Conventions de commits ✅

Préfixez vos commits avec : 
- `test: ` pour l'ajout de tests
- `feat: ` pour l'ajout de nouvelles fonctionnalités
- `refactor: ` pour la refactorisation du code
- `chore: ` pour les tâches de maintenance (installation, configuration, etc.)

Suffixez vos commits avec :
- `:white_check_mark:` si le test passe
- `:test_tube:` si le test échoue
- `:recycle:` si vous refactorez le code
- `:sparkles:` si vous ajoutez une nouvelle fonctionnalité
- `:package:` si vous installez une nouvelle dépendance

> Il est possible de combiner les suffixes !

Exemples : 
- `chore: installation de JUnit :package:`
- `test: Golden Master :white_check_mark:`
- `test: elements conjurés :test_tube:`
- `feat: Priseen charge des éléments Conjured :sparkles: :white_check_mark:`
- `refactor: extraction de la méthode updateQuality() :recycle:`

> Un point bonus vous sera accordé si vous respectez ces conventions sur tous vos commits !

Si tout va bien, vous aurez (dans l'ordre) : 
- Quelques commits `chore` au début
- Des commits `test` pour le golden master
- Beaucoup de commits `refactor` pour la refactorisation
- Des commits `test` avec `:test_tube:` pour les tests unitaires qui échouent, après votre refactorisation
- Un seul commit `feat` avec `:sparkles: :white_check_mark:` lorsque vous aurez terminé d'implémenter la nouvelle fonctionnalité

## Consignes 📚

- Le `README.md` de la Rose Dorée vous demande d'implémenter une nouvelle fonctionnalité : les produits invoqués ("Conjured").
- Placez le code source et les tests dans différents packages, et installez les dépendances.
- Vous devrez d'abord refactoriser le code.
- Vous réaliserez un **Golden Master** pour valider votre refactorisation (il pourra être supprimé une fois la refactorisation terminée).

### Rappels : 
- Vous n'avez pas le droit de modifier la classe `Item`, ni à créer de nouvelles classes

## Sources

- [Emily Bache - The Coding Dojo Handbook](https://leanpub.com/codingdojohandbook)
- [Emily Bach - Gilded Rose](https://github.com/emilybache/GildedRose-Refactoring-Kata/tree/main)