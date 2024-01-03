# Tests unitaires - TP 1

## Objectifs 🎯

Votre objectif est de réaliser les tests unitaires des différents exercices de ce TP.

Les algorithmes à tester proviennent du TP 1 du cours [Java-POO](https://github.com/Octocorn-Learning/Java-POO).
Vous pouvez reprendre les algorithmes de ce TP, ou bien les réécrire vous-même (version coq).

> NB : les méthodes **ne doivent pas** être statiques !

Vous utiliserez des tests paramétrés pour tester les algorithmes.
Vous testerez également les erreurs explicitement déclarées dans le code.

## Rendu 📥

Vous devrez créer un repository sur GitHub, et y pousser votre code.

Vous devrez respecter les consignes suivantes :
- Le code source sera dans le dossier `./src/main/java`, et les tests dans le dossier `./src/test/java`.
- Chaque fichier `.java` sera dans un package correspondant à son exercice.
- Vous réaliserez un commit par exercice, avec un message de commit explicite.

### Evaluation

Vous serez évalué sur les points suivants :
- L'exercice est terminé,
- Utilisation de tests paramétrés sur tous les tests,
- Respect des consignes de rendu (commits, packages, etc.),
- La qualité générale du code des tests (lisibilité, factorisation, etc.)

## Exercices 🏋️

### Exercice 1 : Calcul de la moyenne

```java
public class Moyenne {
    public int moyenne(int[] notes) {

        verifierTaille(notes);

        verifierNotes(notes);

        return calculerMoyenne(notes);
    }

    /**
     * Calcule la moyenne des notes
     * @param notes Tableau de notes
     * @return La moyenne des notes
     */
    private int calculerMoyenne(int[] notes) {
        int somme = 0;
        for (int note : notes) {
            somme += note;
        }
        return somme / notes.length;
    }

    /**
     * Vérifie que les notes sont comprises entre 0 et 20
     * @param notes Tableau de notes
     */
    private void verifierNotes(int[] notes) {
        for (int note : notes) {
            if (note < 0 || note > 20) {
                throw new IllegalArgumentException("Les notes doivent être comprises entre 0 et 20");
            }
        }
    }

    /**
     * Vérifie que le carnet de notes contient 3 notes
     * @param notes Tableau de notes
     */
    private void verifierTaille(int[] notes) {
        if (notes.length != 3) {
            throw new IllegalArgumentException("Le carnet de notes doit contenir 3 notes");
        }
    }
}
```

#### Aides du poulet 🐔

- Commencez par tester un usage "normal" de la méthode
- Essayez ensuite d'identifier les cas limites

> Vous aurez donc au moins 5 tests à réaliser !

### Exercice 2 : calcul du prix TTC

```java
public class Ttc {

    /**
     * Taux de TVA à 20%
     */
    public final double TVA = 1.20;

    /**
     * Calcule le prix TTC à partir du prix HT
     * @param prixHt Prix HT
     * @return Prix TTC
     */
    public double HtToTtc(int prixHt) {

        verifierPrix(prixHt);

        return ajouterTva(prixHt);
    }

    /**
     * Ajoute la TVA à un nombre
     * @param prixHt Nombre à multiplier par la TVA
     * @return Nombre multiplié par la TVA
     */
    private double ajouterTva(int prixHt) {
        return prixHt * this.TVA;
    }

    /**
     * Vérifie que le prix HT est positif
     * @param prixHt Prix HT
     */
    private void verifierPrix(int prixHt) {
        if (prixHt < 0) {
            throw new IllegalArgumentException("Le prix HT doit être positif");
        }
    }
}
```

#### Aides du poulet 🐔

- Commencez par tester un usage "normal" de la méthode : un prix HT positif
- Transformez ensuite votre test en test paramétré pour tester plusieurs prix HT
- Essayez ensuite d'identifier les cas limites 

> Vous aurez donc au moins 3 tests à réaliser !

### Exercice 3 : Nombre Palindrome

```java
public class Palindrome {

    /**
     * Vérifie si un nombre est un palindrome
     * @param nombre long : Nombre à vérifier
     * @return boolean : Vrai si le nombre est un palindrome, faux sinon
     */
    public boolean estUnPalindrome(long nombre) {
        verifierNombre(nombre);

        return nombre == renverserNombre(nombre);
    }

    /**
     * Renverse un nombre
     * @param nombre long : Nombre à renverser
     * @return long : Nombre renversé
     */
    private long renverserNombre(long nombre) {
        long decompte = nombre;
        long renverse = 0;
        while (decompte != 0) {
            renverse = renverse * 10 + (decompte % 10);
            decompte /= 10;
        }
        return renverse;
    }

    /**
     * Vérifie que le nombre contient au moins 2 chiffres
     * @param nombre long : Nombre à vérifier
     */
    private void verifierNombre(long nombre) {
        if (nombre < 10) {
            throw new IllegalArgumentException("Le nombre doit contenir au moins 2 chiffres");
        }
    }
}
```

#### Aides du poulet 🐔

- Commencez par tester un usage "normal" de la méthode : un nombre palindrome
- Transformez ensuite votre test en test paramétré pour tester plusieurs nombres
- Testez ensuite le cas ou le nombre n'est pas un palindrome
- Enfin, testez les cas limites

> On serait tenté de tester le cas des nombres négatifs, mais rien ne nous le demande ici !

### Exercice 4 : Contient un doublon

```java
public class Doublon {
    /**
     * Vérifie si un tableau contient un doublon
     * @param nombres Tableau de nombres
     * @return Vrai si le tableau contient un doublon, faux sinon
     */
    public boolean verifierSiDoublons(int[] nombres) {
        HashMap<Integer, Integer> vues = new HashMap<>();

        for (int nombre : nombres) {
            if (vues.containsKey(nombre) && vues.get(nombre) >= 1) {
                return true;
            }
            vues.put(nombre, vues.getOrDefault(nombre, 0) + 1);
        }
        return false;
    }
}
```

#### Aides du poulet 🐔

- Commencez par tester un usage "normal" de la méthode : un tableau avec un doublon
- Transformez ensuite votre test en test paramétré pour tester plusieurs tableaux
- Testez ensuite le cas ou le tableau ne contient pas de doublon
- Transformez votre test en test paramétré pour tester plusieurs tableaux
- Y a t il des cas limites ?

- Il existe plusieurs moyens de passer un tableau en paramètre d'un test paramétré :
    - En utilisant la notation `@CsvSource` 
    - Il est aussi possible d'utiliser la notation `@MethodSource` (pas encore abordée dans le cours).

### Exercice 5 : Nombre romain vers nombre Arabes

```java
public class RomanToNumber {

    public final Map<Character, Integer> NOMBRES_ROMAINS = new HashMap<>();

    public RomanToNumber() {
        ajouterNombresRomains();
    }

    /**
     * Convertit un nombre romain en nombre arabe
     * @param nombreRomain String : Nombre romain
     * @return int : Nombre arabe
     */
    public int convertirNombreRomainEnNombreArabe(String nombreRomain) {

        ajouterNombresRomains();

        int nombreArabe = 0;

        for (int index = 0; index < nombreRomain.length(); index++) {
            if (
                    index != nombreRomain.length() - 1
                            && estUnNombreSpecial(nombreRomain.charAt(index), nombreRomain.charAt(index + 1))
            ) {
                nombreArabe -= NOMBRES_ROMAINS.get(nombreRomain.charAt(index));
            } else {
                nombreArabe += NOMBRES_ROMAINS.get(nombreRomain.charAt(index));
            }
        }
        return nombreArabe;
    }

    /**
     * Ajoute les nombres romains dans la map
     */
    private void ajouterNombresRomains() {
        NOMBRES_ROMAINS.put('I', 1);
        NOMBRES_ROMAINS.put('V', 5);
        NOMBRES_ROMAINS.put('X', 10);
        NOMBRES_ROMAINS.put('L', 50);
        NOMBRES_ROMAINS.put('C', 100);
        NOMBRES_ROMAINS.put('D', 500);
        NOMBRES_ROMAINS.put('M', 1000);
    }

    /**
     * Vérifie si le chiffre romain actuel est un nombre spécial en le comparant avec le nombre suivant.
     * Si le nombre actuel est plus petit que le nombre suivant, alors il s'agit d'un nombre spécial.
     * @param nombreActuel  Nombre romain actuel
     * @param nombreSuivant Nombre romain suivant
     * @return Vrai si le nombre romain est un nombre spécial, faux sinon
     */
    private boolean estUnNombreSpecial(
            char nombreActuel,
            char nombreSuivant
    ) {
        return this.NOMBRES_ROMAINS.get(nombreActuel) < this.NOMBRES_ROMAINS.get(nombreSuivant);
    }
}
```

#### Aides du poulet 🐔

- Le code source a l'air plus complexe que les autres, et pourtant il y aura moins de tests à réaliser !
- Tester un usage "normal" de la méthode : un nombre romain valide
- Y a t il des cas limites ?

### Exercice 6 : Nombre majoritaire

```java
public class Majoritaire {
    /**
     * Retourne le nombre majoritaire d'un tableau qui en contient un
     * Un élément est majoritaire s'il apparaît plus de n/2 fois dans le tableau
     * Où 'n' est la taille du tableau
     * @param nombres Tableau de nombres
     * @return Nombre majoritaire
     */
    public int hashMap(int[] nombres) {
        int taille = nombres.length;
        Map<Integer, Integer> compteur = new HashMap<>();
        
        for (int nombre : nombres) {
            compteur.put(nombre, compteur.getOrDefault(nombre, 0) + 1);
        }
        
        for (Map.Entry<Integer, Integer> nombre : compteur.entrySet()) {
            if (nombre.getValue() > taille / 2) {
                return nombre.getKey();
            }
        }
        return 0;
    }
}
```

#### Aides du poulet 🐔

- Comme pour le précédent, les tests seront bien plus simple que le code source

> Le morceau de code ne gère pas le cas ou il n'y a pas d'élément majoritaire : donc pas de test à réaliser !
