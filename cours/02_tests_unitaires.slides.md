---
title: Tests Unitaires
theme: solarized
author: Alexandre Devos
company: Octocorn
contributors:
  - Alexandre Devos
sources:
  - 
---

# Tests Unitaires

![Java](assets/java.png) <!-- .element width="19%"  align="left" -->

![Red Green Refactor](assets/red-green-refactor.png) <!-- .element width="40%"  align="right" -->

----

## Tests unitaires

### Objectif

- L'objectif est de tester une unité de code isolée

- L'isolation assure que si le test échoue, c'est uniquement à cause de l'unité testée et non d'une autre !

---

## Tests unitaires

### FIRST

- FIRST est un acronyme qui définit les bonnes pratiques de tests unitaires

- **F**ast
- **I**solated and **I**ndependent
- **R**epeatable
- **S**elf-validating
- **T**imely

----

## Tests unitaires

### Fast

- Les tests unitaires doivent être rapides à exécuter

- Le temps ne doit pas dissuader le développeur de les exécuter !

> Ils ne doivent pas être une contrainte !

----

## Tests unitaires

### Isolated and Independent

- Les tests unitaires doivent être isolés

- Ils ne doivent pas dépendre d'autres tests, ni de l'environnement

- Ils doivent être indépendants les uns des autres

> Ils doivent pouvoir être exécutés dans n'importe quel ordre !

----

## Tests unitaires

### Repeatable

- On doit pouvoir exécuter un test et avoir le même résultat à chaque fois !

- Pas de dépendance, pas de hasard, pas de date, pas de connexion internet, ...

----

## Tests unitaires

### Self-validating

- Un test doit pouvoir se valider sans intervention humaine

- Un test à la main n'est pas un test unitaire !

> Non, un `console.log` n'est pas un test unitaire !

----

## Tests unitaires

### Timely

- Les tests doivent être rapides

- On teste le fonctionnement, pas les datas !

> On ne teste pas les données, on teste le code !

---

## Tests unitaires

### Les 3 A

Les tests sont découpés en 3 étapes :

- **A**rrange
- **A**ct
- **A**ssert

----

## Tests unitaires

### Arrange

On prépare l'environnement de test :

- Création des classes nécessaires
- Création des **mocks** (simulations de dépendances)

> `Calculatrice calculette = new Calculatrice();`

----

## Tests unitaires

### Act

On exécute la méthode à tester :

- Appel de la méthode
- Récupération du résultat si nécessaire

> `int resultat = calculette.additionner(2, 2);`

----

## Tests unitaires

### Assert

On vérifie que le résultat obtenu est bien celui attendu :

- Comparaison du résultat avec le résultat attendu

> `assertEquals(4, resultat);`

---

# Tests unitaires

## JUnit

![JUnit](assets/junit.png) <!-- .element width="50%"  align="right" -->

![java](assets/java.png) <!-- .element width="10%"  align="left" -->

----

## JUnit

### Présentation

- JUnit est un framework de tests unitaires pour Java

- Il est Open Source et gratuit

- Il permet la création de tests unitaires en Java

> Il est intégré à la plupart des IDE Java !

----

## JUnit

### Installation

- JUnit est disponible sur [Maven Central](https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api)

- Il peut être ajouté à n'importe quel projet Java !

----

## JUnit

### Emplacement des tests

- Dans un projet Maven, les tests unitaires doivent être placés dans le dossier `src/test/java`

- On reprendra les mêmes packages que dans le dossier `src/main/java`

----

## JUnit

### Structure d'un test

- La classe test reprend le nom de la classe testée, avec le suffixe `Test`

- Un test est une méthode annotée avec `@Test`

- Elle ne prend aucun paramètre et ne retourne rien

- Une méthode de test doit être publique

----

## JUnit

### Exemple

Dans le dossier `src/main/java/fr/octocorn/tu/demo/helloworld` :

```java
public class HelloWorld {

    public String helloWorld() {
        return "Hello World !";
    }
}
```

----

## JUnit

### Exemple

Dans le dossier `src/test/java/fr/octocorn/tu/demo/helloworld` :

```java [0 | 5-6 | 8-9 | 11-12]
public class HelloWorldTest {

    @Test
    public void testHelloWorld() {
        // Arrange : Création de l'instante à tester
        HelloWorld helloWorld = new HelloWorld();

        // Act : Appel de la méthode à tester
        String resultat = helloWorld.helloWorld();

        // Assert : Vérification du résultat
        assertEquals("Hello World !", resultat);
    }
}
```

----

## JUnit

### AssertEquals

- `assertEquals` est une méthode statique de la classe `Assertions`

- Il s'agit d'annoncer ce qui permet au test de réussir

- Ici, il réussit si les deux résultats sont égaux

> J'affirme que le résultat doit être égal à "Hello World !"

----

## JUnit

### AssertEquals

```java
assertEquals(valeurAttendue, valeurObtenue, "messageErreur");
```

- `valeurAttendue` : La valeur attendue
- `valeurObtenue` : La valeur obtenue
- `messageErreur` (facultatif) : Le message d'erreur à afficher si le test échoue

----

## JUnit

### Autres assertions

- `assertEquals` et `assertNotEquals` : Égalité et inégalité

- `assertTrue` et `assertFalse` : Vrai et faux

- `assertNull` et `assertNotNull` : Null et non null

- `assertThrows` : Lève une exception

> Il en existe bien d'autres !

----

## JUnit

### Démonstration !

----

## JUnit

### Hello World !

```java
public class HelloWorld {
    public String sayHello() {
        return "Hello World!";
    }
}
```

```java
public class HelloWorldTest {

    @Test
    public void testHelloWorld() {
        HelloWorld helloWorld = new HelloWorld();
        String resultat = helloWorld.sayHello();
        assertEquals("Hello World!", resultat);
    }
}
```

----

## JUnit

### Calculatrice

`src/main/java/fr/octocorn/tu/demo/calculatrice`

```java
package fr.octocorn.tu.demo.calculatrice;

public class Calculatrice {
    /**
     * Additionne deux nombres
     *
     * @param premierNombre le premier nombre
     * @param secondNombre le second nombre
     * @return la somme des deux nombres
     */
    public float additionner(float premierNombre, float secondNombre) {
        return premierNombre + secondNombre;
    }


    /**
     * Soustrait deux nombres
     *
     * @param premierNombre le premier nombre
     * @param secondNombre le second nombre
     * @return la différence des deux nombres
     */
    public float soustraire(float premierNombre, float secondNombre) {
        return premierNombre - secondNombre;
    }

    /**
     * Multiplie deux nombres
     *
     * @param premierNombre le premier nombre
     * @param secondNombre le second nombre
     * @return le produit des deux nombres
     */
    public float multiplier(float premierNombre, float secondNombre) {
        return premierNombre * secondNombre;
    }

    /**
     * Divise deux nombres
     *
     * @param premierNombre le premier nombre
     * @param secondNombre le second nombre
     * @return le quotient des deux nombres
     */
    public float diviser(float premierNombre, float secondNombre) {
        return premierNombre / secondNombre;
    }
}
```

----

## JUnit

### Calculatrice

`src/test/java/fr/octocorn/tu/demo/calculatrice`

```java
public class CalculatriceTest {
    @Test
    public void testAdditionner() {
        Calculatrice calculatrice = new Calculatrice();
        float result = calculatrice.additionner(1, 2);
        assertEquals(3, result);
    }

    @Test
    public void testSoustraire() {
        Calculatrice calculatrice = new Calculatrice();
        float result = calculatrice.soustraire(1, 2);
        assertEquals(-1, result);
    }

    @Test
    public void testMultiplier() {
        Calculatrice calculatrice = new Calculatrice();
        float result = calculatrice.multiplier(1, 2);
        assertEquals(2, result);
    }

    @Test
    public void testDiviser() {
        Calculatrice calculatrice = new Calculatrice();
        float result = calculatrice.diviser(1, 2);
        assertEquals(0.5, result);
    }
}
```

----

## JUnit

### Calculatrice - Refactoring

```java
public class CalculatriceTest {
    // Attribut privé qui doit être initialisé avant chaque test
    // On le place en haut de la classe pour éviter les problèmes de portée
    private Calculatrice calculatrice;
    // Attributs privés qui doivent être initialisés avant chaque test
    private float premierNombre;
    private float secondNombre;

    // Méthode appelée avant chaque test
    // L'annotation @BeforeEach permet de l'identifier
    @BeforeEach
    public void setUp() {
        // Ici, on initialise les attributs
        // NB : ils doivent être déclarés en haut de la classe !
        calculatrice = new Calculatrice();
    }

    @Test
    public void testAdditionner() {
        // Arrange
        premierNombre = 1;
        secondNombre = 2;

        // Act
        float result = calculatrice.additionner(premierNombre, secondNombre);

        // Assert
        assertEquals(3, result);
    }

    @Test
    public void testSoustraire() {
        // Arrange
        premierNombre = 1;
        secondNombre = 2;

        // Act
        float result = calculatrice.soustraire(premierNombre, secondNombre);

        // Assert
        assertEquals(-1, result);
    }

    @Test
    public void testMultiplier() {
        // Arrange
        premierNombre = 1;
        secondNombre = 2;

        // Act
        float result = calculatrice.multiplier(premierNombre, secondNombre);

        // Assert
        assertEquals(2, result);
    }

    @Test
    public void testDiviser() {
        // Arrange
        premierNombre = 1;
        secondNombre = 2;

        // Act
        float result = calculatrice.diviser(premierNombre, secondNombre);

        // Assert
        assertEquals(0.5, result);
    }
}
```

----

## JUnit

### `@BeforeEach`

- `@BeforeEach` est une annotation qui permet d'identifier une méthode qui doit être exécutée avant chaque test

- Elle est utile pour initialiser des attributs

- Il existe également `@BeforeAll`, `@AfterEach` et `@AfterAll`

----

## JUnit

### Nommer les tests

- Le nom de la méthode peut être difficile à lire

- L'annotation `@DisplayName` permet de donner un nom plus explicite au test

```java

@DisplayName("Test de la méthode additionner")
@Test
public void testAdditionner() {
    // ...
}
```

----

## JUnit

### Tests paramétrés

- Plutôt que de créer une méthode de test par cas, on peut utiliser les tests paramétrés

- C'est très utile pour éviter la duplication de code

- On utilise l'annotation `@ParameterizedTest`

----

## JUnit

### Tests paramétrés

- Il faut importer la classe `org.junit.jupiter.params.ParameterizedTest`

- Elle doit être installée dans le projet

```xml
<!-- https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-params -->
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-params</artifactId>
    <version>5.10.1</version>
    <scope>test</scope>
</dependency>
```

----

## JUnit

### Tests paramétrés - Exemple

```java
// On indique que la méthode est un test paramétré
// On peut donner un nom à ce test
@ParameterizedTest(name = "Test {index} : {0}")
// Définition des paramètres
// ints pour les entiers, strings pour les chaînes de caractères, etc.
@ValueSource(ints = {1, 2, 3, 4, 5})
// Paramètres qui doivent être injectés dans la méthode
public void testSoustraire(int nombre) {

    // Act
    float result = calculatrice.soustraire(nombre, nombre);

    // Assert
    assertEquals(0, result);
}
```

> Problème : tous les résultats doivent être égaux à 0 !

----

## JUnit

## Tests Paramétrés

- `@ParameterizedTest` permet de définir des paramètres pour un test (remplace `@Test`)
- `@ValueSource` permet de définir les valeurs à tester
- `ints` permet de définir le type des valeurs

----

## JUnit

### Tests paramétrés - CsvSource

```java

@DisplayName("Test des additions")
@ParameterizedTest(name = "Test {index} : {0} + {1} = {2}")
// On définit les paramètres sous forme de csv
@CsvSource({
        "1, 2, 3",
        "2, 3, 5",
        "3, 4, 7",
        "4, 5, 9",
        "5, 6, 11"
})
public void testAdditionner(int premierNombre, int secondNombre, int resultatAttendu) {
    // Act
    float result = calculatrice.additionner(premierNombre, secondNombre);

    // Assert
    assertEquals(resultatAttendu, result);
}
```

----

## JUnit

### Tests paramétrés - CsvSource

- `@CsvSource` permet de définir les paramètres sous forme de csv
- `{index}` correspond à l'index du paramètre
- `{0}` correspond au premier paramètre
- `{1}` correspond au second paramètre, etc.

----

## Démonstration !

Refactoring des tests de la calculatrice en tests paramétrés

----

## JUnit

### Tests paramétrés - Exemple complet

```java
package fr.octocorn.tu.demo.calculatrice;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;

import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatriceTest {
    // Attribut privé qui doit être initialisé avant chaque test
    // On le place en haut de la classe pour éviter les problèmes de portée
    private Calculatrice calculatrice;

    // Sera exécuté avant chaque test
    @BeforeEach
    public void setUp() {
        calculatrice = new Calculatrice();
    }

    // Nom du test
    @DisplayName("Test des additions")
    // Remplace l'annotation @Test
    // Précise qu'il y a des paramètres
    // On peut aussi donner un nom à chaque paramètre
    // {index} correspond à l'index du paramètre
    // {0} correspond au premier paramètre
    // {1} correspond au second paramètre, etc.
    @ParameterizedTest(name = "Test {index} : {0} + {1} = {2}")
    // On définit les paramètres sous forme de csv
    // Il faut voir un CSV comme un tableau, avec des lignes et des colonnes
    @CsvSource({
            "1, 2, 3",
            "2, 3, 5",
            "3, 4, 7",
            "4, 5, 9",
            "5, 6, 11"
    })
    public void testAdditionner(float premierNombre, float secondNombre, float resultatAttendu) {
        // Act
        float result = calculatrice.additionner(premierNombre, secondNombre);

        // Assert
        assertEquals(resultatAttendu, result);
    }

    @DisplayName("Test des soustractions")
    @ParameterizedTest(name = "Test {index} : {0} - {1} = {2}")
    @CsvSource({
            "1, 2, -1",
            "6, 5, 1",
            "1000, 9, 991",
    })
    public void testSoustraire(float premierNombre, float secondNombre, float resultatAttendu) {

        // Act
        float result = calculatrice.soustraire(premierNombre, secondNombre);

        // Assert
        assertEquals(resultatAttendu, result);
    }

    @DisplayName("Test des multiplications")
    @ParameterizedTest(name = "Test {index} : {0} * {1} = {2}")
    @CsvSource({
            "1, 2, 2",
            "2, 3, 6",
            "3, 4, 12",
            "4, 5, 20",
            "5, 6, 30"
    })
    public void testMultiplier(float premierNombre, float secondNombre, float resultatAttendu) {
        // Act
        float result = calculatrice.multiplier(premierNombre, secondNombre);

        // Assert
        assertEquals(resultatAttendu, result);
    }

    @DisplayName("Test des divisions")
    @ParameterizedTest(name = "Test {index} : {0} / {1} = {2}")
    @CsvSource({
            "1, 2, 0.5",
            "6, 5, 1.2",
            "1000, 10, 100"
    })
    public void testDiviser(float premierNombre, float secondNombre, float resultatAttendu) {
        // Act
        float result = calculatrice.diviser(premierNombre, secondNombre);

        // Assert
        assertEquals(resultatAttendu, result);
    }
}
```

----

## JUnit

### Test des exceptions

> Faut-il tester/anticiper les exceptions ?

----

## JUnit

### Test des exceptions

Oui... Et non :

- Les exceptions sont des cas particuliers
- Elles doivent être testées uniquement si elles sont susceptibles d'être levées

> La question : Est-ce important d'un point de vue métier ?

----

## JUnit

### Test des exceptions

- On testera les erreurs qui représentent un besoin métier uniquement

- Inutile de chercher à anticiper ce qui n'est pas demandé et qui pourrait ne jamais arriver

- Et puis : qu'est-ce qui vous dit que ce n'est pas volontaire ?

> Faites-le en bonne intelligence !

----

## JUnit

### Test des exceptions

- `assertThrows` permet de tester qu'une exception est bien levée

- La syntaxe est un peu particulière

- Elle prend en paramètre la classe de l'exception et une **lambda**

> On peut aussi se baser sur le message d'erreur au lieu de la classe

----

## JUnit

### Test des exceptions - Exemple

Modification de la classe `Calculatrice` :

```java
/**
 * Divise deux nombres
 *
 * @param premierNombre le premier nombre
 * @param secondNombre le second nombre
 * @return le quotient des deux nombres
 */
public float diviser(float premierNombre, float secondNombre) {
    verifierDivisionParZero(secondNombre);
    return premierNombre / secondNombre;
}

/**
 * Vérifie que le second nombre n'est pas égal à zéro
 *
 * @param secondNombre le second nombre
 */
private void verifierDivisionParZero(float secondNombre) throws IllegalArgumentException {
    if (secondNombre == 0) {
        throw new IllegalArgumentException("La division par zéro est impossible");
    }
}
```

----

## JUnit

### Test des exceptions - Exemple

Avec le message d'erreur :

```java

@DisplayName("Test de la division par zéro")
@ParameterizedTest(name = "Test {index} : {0} / 0")
@ValueSource(floats = {1, 10, 500, 1000})
public void testDiviserParZero(float premierNombre) {
    IllegalArgumentException exception;

    exception = assertThrows(IllegalArgumentException.class, () -> calculatrice.diviser(premierNombre, 0));

    assertEquals("La division par zéro est impossible", exception.getMessage());
}
```

----

## JUnit

### Test des exceptions - Exemple

Avec la classe de l'erreur :

```java

@DisplayName("Test de la division par zéro")
@ParameterizedTest(name = "Test {index} : {0} / 0")
@ValueSource(floats = {1, 10, 500, 1000})
public void testDiviserParZero(float premierNombre) {
    IllegalArgumentException exception;

    exception = assertThrows(IllegalArgumentException.class, () -> calculatrice.diviser(premierNombre, 0));

    assertEquals(IllegalArgumentException.class, exception.getClass());
}
```

----

## JUnit

### Test des exceptions - Exemple

Ou, en utilisant une lambda (à préférer) :

```java

@DisplayName("Test de la division par zéro")
@ParameterizedTest(name = "Test {index} : {0} / 0")
@ValueSource(floats = {1, 10, 500, 1000})
public void testDiviserParZero(float premierNombre) {
    assertThrows(
            IllegalArgumentException.class,
            () -> calculatrice.diviser(premierNombre, 0)
    );
}
```

----

## JUnit

### Les méthodes privées

> Faut-il tester les méthodes privées ?

----

## JUnit

### Les méthodes privées

- Les méthodes privées sont des méthodes internes à la classe

- C'est un détail d'implémentation qui ne doit pas être testé

- Les tester revient à casser l'encapsulation !

> On ne teste pas les méthodes privées !

----

## JUnit

### Les méthodes privées

- Attention : Ca ne veut pas dire que ce morceau de logique doit être ignoré !

- On entend juste par là qu'il ne faut pas tester la méthode privée en elle-même

- On vérifiera cependant le comportement de la méthode publique qui l'appelle !

----

## JUnit

### Exemple concrêt

- Notre calculatrice a une méthode publique `diviser`

- Elle appelle une méthode privée `verifierDivisionParZero`

- On ne teste pas la méthode privée, mais on teste la méthode publique !

- On peut cependant s'assurer que la méthode l'exception est bien levée

----

## JUnit

### MethodSource

- `@MethodSource` permet de définir les paramètres sous forme de méthode

- Elle prend en paramètre le nom de la méthode qui fournit les paramètres

- La méthode doit être statique et retourner un `Stream` de `Arguments`

> Utile pour passer des objets, des tableaux, etc.

----

## JUnit

### MethodSource - Exemple

```java

@DisplayName("Test des additions")
@ParameterizedTest(name = "Test {index} : {0} + {1} = {2}")
@MethodSource("argumentsAdditionner")
public void testAdditionner(float[] nombres, float resultatAttendu) {
    // Act
    float result = calculatrice.additionner(nombres[0], nombres[1]);

    // Assert
    assertEquals(resultatAttendu, result);
}

private static Stream<Arguments> argumentsAdditionner() {
    return Stream.of(
            Arguments.of((Object) new float[]{1, 2}, 3),
            Arguments.of((Object) new float[]{2, 3}, 5),
            Arguments.of((Object) new float[]{3, 4}, 7),
            Arguments.of((Object) new float[]{4, 5}, 9)
    );
}
```

----

## JUnit

### À vous de jouer !

Réalisez le TP 1 !

---

# Tests unitaires

## Mockito

![Mockito](assets/mockito.png) <!-- .element width="50%"  align="right" -->

![java](assets/java.png) <!-- .element width="10%"  align="left" -->

----

## Mockito

### Présentation

- Mockito est un framework de tests unitaires pour Java

- Il permet de créer des **mocks** (simulations de dépendances)

----

## Mockito

### Mock

- Un mock est une simulation d'une classe

- Elle permet de rédiger des tests unitaires sans dépendre d'autres classes

----

## Mockito

### Exemple

- Vous avez une classe `Utilisateur` qui dépend d'une classe `Adresse`

- Vous souhaitez rédiger les tests unitaires de la classe `Utilisateur`

- Sans mock, vous devez créer une instance de `Adresse` pour chaque test

> Mais que se passe-t-il si la classe `Adresse` a un bug ?

----

## Mockito

### Exemple

- Les mock permettent d'éviter tout problème éventuel avec une dépendance

- Ils permettent de se concentrer sur la classe à tester

- On évitera ainsi les faux négatifs

----

## Mockito

### Les types de mock

Il existe plusieurs outils pour simuler des dépendances :

- Les stubs
- Les mocks
- Les spies

> Chaque type a ses avantages et ses inconvénients !

----

## Mockito

### Les stubs

- Objet fictif qui simule un objet réel

- Un type de mock très simple

- Sert généralement à retourner des données contrôlées

- Ne dispose pas de comportement

> Exemple : simuler la réponse d'une API/BDD

----

## Mockito

### Les mocks

- Le plus utilisé !

- Stub qui dispose d'un comportement

- On peut définir des comportements pour chaque méthode

> Permet de simuler une classe complète, implémentée ou non !

----

## Mockito

### Les spies

- Version partielle d'un objet réel

- Contrairement aux mocks, les méthodes non définies sont appelées

- On contrôlera généralement le fait qu'une méthode a été appelée, et pas nécessairement son résultat

----

## Mockito

### Installation

- Mockito est disponible sur [Maven Central](https://mvnrepository.com/artifact/org.mockito/mockito-core)

```xml
<!-- https://mvnrepository.com/artifact/org.mockito/mockito-core -->
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>5.8.0</version>
    <scope>test</scope>
</dependency>
```

----

## Mockito

### Créer un stub

Syntaxe :

```java
TypeDeLaClasse nomDuStub = mock(TypeDeLaClasse.class, params);
```

- `TypeDeLaClasse` : Le type de la classe à simuler
- `nomDuStub` : Le nom du stub
- `TypeDeLaClasse.class` : Le type de la classe à simuler
- `params` : Les paramètres de la classe à simuler

----

## Mockito

### Paramètres d'un stub

Le second paramètre de la méthode `mock` permet de définir le comportement du stub.  
Il peut s'agir de :

- Une constante,
- Une lambda de type `Answer`,

> Il existe beaucoup de constantes prédéfinies !

----

## Mockito

### Paramètres d'un stub - Constantes

- `RETURNS_DEFAULTS` : Retourne la valeur par défaut du type de retour
- `RETURNS_SMART_NULLS` : Retourne une valeur intelligente
- `RETURNS_MOCKS` : Retourne un mock
- `RETURNS_DEEP_STUBS` : Retourne un stub imbriqué

----

## Mockito

### Paramètres d'un stub - Answer

- `Answer` est une interface fonctionnelle

- Elle permet de définir un comportement personnalisé

```java
Foo stubFoo = mock(Foo.class, new Answer<Object>() {
    @Override
    public Object answer(InvocationOnMock invocation) {
        return "custom return value";
    }
});
```

----

## Mockito

### Les Mocks

- Un mock est un stub qui dispose d'un comportement plus avancé

- On pourra intercepter chaque appel de méthode et définir ce qui est retourné

- On pourra également vérifier les paramètres passés à chaque méthode

----

## Mockito

### Créer un mock

Syntaxe :

```java
TypeDeLaClasse nomDuMock = mock(TypeDeLaClasse.class);
```

- `TypeDeLaClasse` : Le type de la classe à simuler

----

## Mockito

### Définir le comportement d'un mock

```java
TypeDeLaClasse nomDuMock = mock(TypeDeLaClasse.class);
when(nomDuMock.nomMethode()).thenReturn(valeur);
```

- `nomDuMock` : Le nom du mock
- `nomMethode` : Le nom de la méthode à simuler
- `valeur` : La valeur à retourner

> A chaque fois que `nomMethod` est appelée, `valeur` est retournée

----

## Mockito

### Récupérer les arguments d'un mock

```java [0 | 2 | 4]
TypeDeLaClasse nomDuMock = mock(TypeDeLaClasse.class);
ArgumentCaptor<String> argument = ArgumentCaptor.forClass(String.class);
when(nomDuMock.nomMethode(argument.capture())).thenReturn(valeur);
String argumentCapture = argument.getValue();
```

- `ArgumentCaptor` permet de récupérer les arguments passés à une méthode

> Ici, on récupère le premier argument de la méthode `nomMethode`

----

## Mockito

### Méthode plus avancée

```java
TypeDeLaClasse nomDuMock = mock(TypeDeLaClasse.class);
when(nomMock.nomMethode()).thenAnswer(invocation -> {
    Object[] argumentsDeLaMethode = invocation.getArguments();
    return "called with arguments: " + Arrays.toString(argumentsDeLaMethode);
});
```

- `invocation` : L'invocation de la méthode
- `getArguments` : Récupère les arguments passés à la méthode

----

## Mockito

### Pourquoi ?

> Quitte à redéfinir le comportement, pourquoi ne pas utiliser l'objet pour se simplifier la vie ?

----

## Mockito

### Pourquoi ?

- En théorie, la dépendence à déjà été testée. 

- Il serait inutile de la tester à nouveau !

- On veut aussi éviter les erreurs !

> On ne cherche pas à tester la dépendance, mais interaction !

----

## Mockito

### Les spies

- Un spy permet de vérifier un appel réel d'une méthode

- On pourra vérifier que la méthode a été appelée, mais pas son résultat

- On pourra également définir un comportement personnalisé

----

## Mockito

### Créer un spy

Syntaxe :

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
```

- `TypeDeLaClasse` : Le type de la classe à simuler
- `nomDuSpy` : Le nom du spy

----

## Mockito

### Définir le comportement d'un spy

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
doReturn(valeur).when(nomDuSpy).nomMethode();
```

> Syntaxe similaire à celle des mocks

----

## Mockito

### Vérifier un appel

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
nomDuSpy.nomMethode();
verify(nomDuSpy).nomMethode();
```

- `verify` permet de vérifier qu'une méthode a été appelée

- Fonctionne aussi avec les mocks

----

## Mockito

### Vérifier un appel avec des paramètres

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
nomDuSpy.nomMethode("param1", "param2");
verify(nomDuSpy).nomMethode("param1", "param2");
```

- Ici on vérifie l'appel de la méthode

- On s'assure qu'elle a été appelée avec les bons paramètres

----

## Mockito

### Et si on ne connaît pas les paramètres ?

On peut utiliser `any` :

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
nomDuSpy.nomMethode("param1", "param2");
verify(nomDuSpy).nomMethode(any(), anyString());
```

- `anyString` permet de définir une chaîne de caractères quelconque
- Il y a aussi `anyInt`, `anyBoolean`, etc.

----

## Mockito

### Compter le nombre d'appels

```java
TypeDeLaClasse nomDuSpy = spy(TypeDeLaClasse.class);
nomDuSpy.nomMethode();
nomDuSpy.nomMethode();
verify(nomDuSpy, times(2)).nomMethode();
```

----

## Mockito

### Les automocks

- Mockito permet de créer des mocks automatiquement

- Pour ce faire, il y a une dépendance à ajouter dans le `pom.xml`

```xml
<dependency>
      <groupId>org.mockito</groupId>
      <artifactId>mockito-junit-jupiter</artifactId>
      <version>5.3.1</version>
      <scope>test</scope>
    </dependency>
```

----

## Mockito

### Les automocks

- Il suffit d'annoter la classe à mocker avec `@Mock`

- On pourra alors injecter les mocks avec `@InjectMocks`

- Il faut également ajouter `@ExtendWith(MockitoExtension.class)`

----

## Mockito

### Exemple

Avec le diagramme suivant : 

![Hero](assets/hero.png)

----

## Mockito

### Exemple

`Hero.java`

```java
public class Hero {
    private final Identity identity;
    private List<Power> powers;

    public Hero(Identity identity, List<Power> powers) {
        this.identity = identity;
        this.setPowers(powers);
    }

    public List<Power> getPowers() {
        return powers;
    }

    public void setPowers(List<Power> powers) {
        this.powers = powers;
    }

    public String removeCostume() {
        return "Le héro enlève son costume. Il redevient " + identity.getIdentity();
    }

    public String fight() {
        return this.getRandomPower().usePower();
    }

    private Power getRandomPower() {
        int index = (int) Math.floor(Math.random() * powers.toArray().length);
        return this.getPowers().get(index);
    }
}
```

----

## Mockito

### Exemple

`Identity.java`

```java
public class Identity {
    private String firstName;
    private String lastName;

    private String job;

    public Identity(String firstName, String lastName, String job) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.job = job;
    }

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getJob() {
        return job;
    }

    public void setJob(String job) {
        this.job = job;
    }

    public String getIdentity() {
        return firstName + " " + lastName + ": " + job;
    }
}
```

----

## Mockito

### Exemple

`Power.java`

```java
package fr.octocorn.tu.demo.superhero;

public class Power {
    private final String name;
    private final String description;

    public Power(String name, String description) {
        this.name = name;
        this.description = description;
    }

    public String getName() {
        return this.name;
    }

    public String getDescription() {
        return description;
    }

    public String usePower() {
        return "Le héro utilise " + name + " et " + description;
    }
}
```

----

## Mockito

### Exemple

Test manuel :

```java
class HeroTest {

    private Hero hero;

    @BeforeEach
    void setUp() {
        List<Power> powers = new ArrayList<>();

        Power powerMock = mock(Power.class);
        when(powerMock.getName()).thenReturn("Super force");
        when(powerMock.getDescription()).thenReturn("soulève des montagnes");
        when(powerMock.usePower()).thenReturn(
                "Le héro utilise son pouvoir : Super force qui soulève des montagnes"
        );
        powers.add(powerMock);

        Identity identityMock = mock(Identity.class);
        when(identityMock.getIdentity()).thenReturn("Bruce Wayne: Riche héritier");

        hero = new Hero(identityMock, powers);
    }

    @DisplayName("Test de la méthode removeCostume")
    @Test
    public void removeCostume() {
        // When
        String result = hero.removeCostume();
        // Then
        assertEquals(
                "Le héro enlève son costume. Il redevient Bruce Wayne: Riche héritier",
                result
        );
    }

    @DisplayName("Test de la méthode fight")
    @Test
    public void fight() {
        // When
        String result = hero.fight();
        // Then
        assertEquals(
                "Le héro utilise son pouvoir : Super force qui soulève des montagnes",
                result
        );
    }

}
```

----

## Mockito

### Exemple

Test avec automocks :

```java
@ExtendWith(MockitoExtension.class)
class HeroAutoTest {

    @Mock
    private Identity identity;

    @Mock
    private Power power;


    @InjectMocks
    private Hero hero;

    @BeforeEach
    void setUp() {
        List<Power> powers = new ArrayList<>();
        powers.add(power);
        hero.setPowers(powers);
    }

    @DisplayName("Test de la méthode removeCostume")
    @Test
    public void removeCostume() {
        // When
        String result = hero.removeCostume();
        // Then
        verify(
                identity,
                times(1)
        ).getIdentity();
        assertEquals(
                "Le héro enlève son costume. Il redevient " + identity.getIdentity(),
                result
        );
    }

    @DisplayName("Test de la méthode fight")
    @Test
    public void fight() {
        // Given

        // When
        String result = hero.fight();
        // Then
        verify(
                power,
                times(1)
        ).usePower();
        assertEquals(
                power.usePower(),
                result
        );
    }
}
```

----

## Mockito

### Stub, Spiers ou Mocks ?

- Les stubs sont utiles pour les données

- Les mocks sont utiles pour les tests unitaires de classes avec comportement

- Les spies sont utiles pour les tests d'intégration !

---

# Tests unitaires

## Les approches

![java](assets/java.png) <!-- .element width="10%"  align="left" -->

----

## Tests unitaires

### Les approches

On distingue deux approches :

- Le test before

- Le test after

----

## Tests unitaires

### Le test before

- On écrit les tests avant de coder

- On décrit la fonctionnalité attendue entièrement avec son fonctionnement final

- Puis, on rédige le code pour que les tests passent

> On peut utiliser les tests paramétrés pour tester plusieurs cas

----

## Tests unitaires

### Le test before - Avantages

- Les `specs` sont souvent définis avant le développement

- Ils assurent que la feature soit développée, sans mauvaise compréhension

- Ils guident le développeur et lèvent les ambiguïtés

----

## Tests unitaires

### Le test before - Inconvénients

- Implique un effort de rédaction supplémentaire

- Souvent rédigé par une autre personne que le développeur

- Peut-être difficile à appréhender et être 'désespérant'

----

## Tests unitaires

### Le test after

- Le plus utilisé

- On écrit le code avant de rédiger les tests

- Puis, on s'assure que le code fonctionne avec les tests

----

## Tests unitaires

### Le test after - Avantages

- Test le code qui vient d'être écrit

- Peut être fait par le même développeur, ou un testeur dédié

- Génère souvent une phase de refactorisation du code

----

## Tests unitaires

### Le test after - Inconvénients

- Risque de rédiger des tests qui ne sont pas pertinents

- Risque de rédiger des tests erronés 'pour les faire passer'

- Allonge le temps de développement

----

## Tests unitaires

### Faut-il tester systématiquement ?

- Idéalement oui !

- On considère que l'ajout de test augmente de 20% le temps de développement

- Ce temps est largement rentabilisé par la suite, car moins de bugs ou des bugs plus simples à corriger

----

## Tests unitaires

### Dans la vraie vie

- L'ajout ou non de test dépend généralement du client

- Si tout le monde s'accorde à dire que c'est important, il n'est pas toujours possible de le faire

- Il faut donc trouver un compromis

----

## Tests unitaires

### Le coverage

- Le coverage est un indicateur de qualité du code

- Il désigne combien de % du code est couvert par les tests

- Il est généralement calculé par un outil

----

## Tests unitaires

### Le coverage

- Un bon coverage est généralement supérieur à 80%

- On utilisera généralement l'approche du '80/20'

- On ne testera pas les méthodes privées, les getters/setters, etc.

----

## Tests unitaires

### Le 80/20

- On considère que 80% du code sera fait en 20% du temps

- Les 20% restants seront fait en 80% du temps

> Ici, on l'applique aux tests !

----

## Tests unitaires

### Pourquoi 80% ?

- 80% est un bon compromis, car il permet de tester les cas les plus importants

- Les 20% restants sont généralement des cas particuliers, en marge de l'usage normal

> Aller au-delà reviendrait à tester des cas qui n'arriveront peut-être jamais !

----

## Tests unitaires

### A vous de jouer !

Réalisez le TP 2 !

---

# La suite !

[Index](index.html)