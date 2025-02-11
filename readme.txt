Bonjour !
Je m'appelle Jérémy Rolland gdfgdf

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
