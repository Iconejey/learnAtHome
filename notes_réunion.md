# Learn@Home

## Présentation du projet

Learn@Home est une association qui met en relation des enfants en difficulté scolaire et des bénévoles, en ligne. Elle a pour objectif de permettre à tout élève, où qu'il soit, d'accéder à un soutien scolaire à distance.

Chaque élève inscrit sur le site a un tuteur bénévole qui lui est assigné. Le bénévole a pour objectif de soutenir l'élève dans son apprentissage, à travers de courts rendez-vous prévus chaque semaine. Durant ces rendez-vous, le bénévole aide l'élève à réaliser ses devoirs et à s'organiser.

Pour faciliter les interactions et la communication, Learn@Home souhaite créer un nouveau site web, qui doit être composé des pages suivantes :

1. Une page de connexion.
2. Une page Interface de chat.
3. Une page de calendrier.
4. Une page de gestion des tâches.
5. Une page Tableau de bord.

## Détails page par page

### 1. La page de connexion

La page de connexion doit permettre à un élève ou à un bénévole de se connecter. Toutes les autres pages ne sont accessibles qu'une fois connecté à un compte. Cette page doit intégrer :

- un système de récupération de mot de passe oublié ;
- un lien vers une page de création de compte.

```mermaid
graph LR
    %% Actors
    Eleve((Élève))
    Benevole((Bénévole))

    %% System Boundary
    subgraph Page de Connexion
        UC_Login([Se connecter])
        UC_Register([Créer un compte])
        UC_Reset([Récupérer le mot de passe oublié])
    end

    %% Associations
    Eleve --- UC_Login
    Eleve --- UC_Register
    Eleve --- UC_Reset

    Benevole --- UC_Login
    Benevole --- UC_Register
    Benevole --- UC_Reset

    %% Styling
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000
    classDef usecase fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000

    class Eleve,Benevole actor
    class UC_Login,UC_Register,UC_Reset usecase
```

### 2. L'interface de chat

L'interface de chat de Learn@Home est une page de chat classique, intégrant un système de discussion instantanée entre élèves et bénévoles. Elle doit aussi permettre d'accéder à l'historique des conversations, et d'ajouter ou supprimer un contact.

D'autres éléments doivent être ajoutés :

- la photo de profil de l'expéditeur, à côté de chaque message ;
- un indicateur permettant de visualiser si un message a été lu ou non ;
- l'horodatage des messages.

```mermaid
graph LR
    %% Actors
    Eleve((Élève))
    Benevole((Bénévole))

    %% System Boundary
    subgraph Interface de Chat
        UC_Send([Envoyer un message])
        UC_History([Consulter l'historique])
        UC_AddContact([Ajouter un contact])
        UC_DelContact([Supprimer un contact])
    end

    %% Associations
    Eleve --- UC_Send
    Eleve --- UC_History
    Eleve --- UC_AddContact
    Eleve --- UC_DelContact

    Benevole --- UC_Send
    Benevole --- UC_History
    Benevole --- UC_AddContact
    Benevole --- UC_DelContact

    %% Styling
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000
    classDef usecase fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000

    class Eleve,Benevole actor
    class UC_Send,UC_History,UC_AddContact,UC_DelContact usecase
```

### 3. La page de calendrier

La page de calendrier de Learn@Home correspond à une page de calendrier classique, sur laquelle s'affichent les différents événements et rendez-vous de l'utilisateur.

```mermaid
graph LR
    %% Actors
    Eleve((Élève))
    Benevole((Bénévole))

    %% System Boundary
    subgraph Page de Calendrier
        UC_ViewEvents([Consulter les événements et RDV])
        UC_ManageEvents([Gérer les événements et RDV])
    end

    %% Associations
    Eleve --- UC_ViewEvents
    Eleve --- UC_ManageEvents

    Benevole --- UC_ViewEvents
    Benevole --- UC_ManageEvents

    %% Styling
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000
    classDef usecase fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000

    class Eleve,Benevole actor
    class UC_ViewEvents,UC_ManageEvents usecase
```

### 4. La page de gestion des tâches

L'interface de cette page doit permettre de créer des tâches pour soi-même ou pour un autre utilisateur.

- l'élève ne peut créer des tâches que pour lui-même ;
- le bénévole peut créer des tâches pour les élèves qu'il suit.

Il faut pouvoir lister, supprimer et ajouter des tâches, tout en maintenant la différence d'ajout de tâche entre le tuteur et l'étudiant.

```mermaid
graph LR
    %% Actors
    Eleve((Élève))
    Benevole((Bénévole))

    %% System Boundary
    subgraph Gestion des Tâches
        UC_List([Lister ses tâches])
        UC_Delete([Supprimer une tâche])
        UC_CreateSelf([Créer une tâche pour soi-même])
        UC_CreateOther([Créer une tâche pour l'élève suivi])
    end

    %% Associations
    Eleve --- UC_List
    Eleve --- UC_Delete
    Eleve --- UC_CreateSelf

    Benevole --- UC_List
    Benevole --- UC_Delete
    Benevole --- UC_CreateSelf
    Benevole --- UC_CreateOther

    %% Styling
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000
    classDef usecase fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000

    class Eleve,Benevole actor
    class UC_List,UC_Delete,UC_CreateSelf,UC_CreateOther usecase
```

### 5. Le tableau de bord

Cette page servira de page principale et devra donc regrouper un récapitulatif de toutes les informations récentes et importantes en provenance des autres pages : chat, calendrier, gestion des tâches.

La page affichera :

- un récapitulatif des tâches (to-do list) issu de la page de gestion des tâches (5.) ;
- la liste des événements prochains, issue de la page Calendrier (4.) ;
- un compteur de messages non lus.

```mermaid
graph LR
    %% Actors
    Eleve((Élève))
    Benevole((Bénévole))

    %% System Boundary
    subgraph Tableau de Bord
        UC_ViewTasksSummary([Consulter le récapitulatif des tâches])
        UC_ViewUpcomingEvents([Consulter les prochains événements])
        UC_ViewUnreadCounter([Visualiser le compteur de messages non lus])
    end

    %% Associations
    Eleve --- UC_ViewTasksSummary
    Eleve --- UC_ViewUpcomingEvents
    Eleve --- UC_ViewUnreadCounter

    Benevole --- UC_ViewTasksSummary
    Benevole --- UC_ViewUpcomingEvents
    Benevole --- UC_ViewUnreadCounter

    %% Styling
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000
    classDef usecase fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000

    class Eleve,Benevole actor
    class UC_ViewTasksSummary,UC_ViewUpcomingEvents,UC_ViewUnreadCounter usecase
```
