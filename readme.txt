Bonjour !
Je m'appelle Jérémy Rolland gdfgdf

sequenceDiagram
    Gitlab->>Gitlab: reçoit un Push sur main
    Gitlab->>Runner: Lance un runner
    Runner->>Serveur: Connexion SSH
    Runner->>Serveur: Envoie les instructions shell du job
    Serveur-->>Gitlab: Connexion SSH vers Gitlab
    Serveur-->>Gitlab: git pull
    Gitlab-->>Serveur: Fichiers
    Runner->>Gitlab: Retourne les logs
    Note over Runner, Serveur: Fin
