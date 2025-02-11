Bonjour !
Je m'appelle Jérémy Rolland gdfgdf

# Adaptateur
C'est un  patron de conception structurel qui permet de faire collaborer des objets ayant des interfaces normalement 
incompatibles.
 ### Exemple
Vous avez un objet "clé" qui permet d'intéragir avec des "portes". 
Un jour, vous souhaitez implémenter la détection d'empreintes digitales en important
une librairie externe.
#### Problème
Les objets de la librairie "scanner" n'acceptent que le type "empreinte".
```mermaid

classDiagram
    class Lock {
        +void unlock()
    }

    class KeyLock {
        +void unlock()
    }

    class FingerprintScanner {
        +void scanFingerprint()
    }

    Lock --> KeyLock : Relation normale
    Lock ..> FingerprintScanner : <<incompatible>>
    note for FingerprintScanner "Cette relation est incompatible."


```
#### Solution
Il faut créer un adaptateur clé -> empreinte.
```mermaid

classDiagram
    class Lock {
        +void unlock()
    }

    class KeyLock {
        +void unlock()
    }

    class FingerprintScanner {
        +void scanFingerprint()
    }

    class FingerprintAdapter {
        -FingerprintScanner scanner
        +FingerprintAdapter(FingerprintScanner scanner)
        +void unlock()
    }

    Lock <|.. KeyLock
    Lock <|.. FingerprintAdapter
    FingerprintAdapter o-- FingerprintScanner
   

```
# Explication
Un adaptateur encapsule un des objets afin de masquer la complexité de la conversion.
L'objet encapsulé n'en a pas conscience.
1. L'adaptateur prend une interface compatible avec un des objets existants.
2. L’objet existant peut appeler les méthodes de l’adaptateur via cette interface en toute sécurité. 
3. Lorsque l’adaptateur reçoit un appel, il passe la requête au second objet dans un format et dans un ordre qu’il 
peut interpréter.

Il est possible de réaliser la conversion dans les deux sens.
### Exemple
Dans notre exemple.
1. **Lock** est une classe qui contient la logique métier du programme.
2. **L'interface** ici revient à utiliser la méthode *unlock()*
