# Module Connexion & Authentification

## Développement de l'interface et de la logique de connexion utilisateur

- Dev Frontend

> ### User Story 1 : Se connecter à son compte (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole de Learn@Home, je souhaite me connecter à mon compte avec mon e-mail et mon mot de passe afin d'accéder à mon espace personnel sécurisé._
>
> #### Scénario 1 : Connexion réussie avec des identifiants valides
>
> - **Given** l'utilisateur est sur la page de connexion de Learn@Home
> - **And** son compte est actif dans le système
> - **When** l'utilisateur saisit son adresse e-mail valide
> - **And** l'utilisateur saisit son mot de passe correct
> - **And** l'utilisateur clique sur le bouton "Se connecter"
> - **Then** l'utilisateur est authentifié avec succès par l'application
> - **And** l'utilisateur est redirigé vers son Tableau de Bord (Dashboard)
> - **And** une session utilisateur sécurisée est ouverte
>
> #### Scénario 2 : Échec de la connexion avec des identifiants invalides
>
> - **Given** l'utilisateur est sur la page de connexion
> - **When** l'utilisateur saisit une adresse e-mail invalide ou un mot de passe incorrect
> - **And** l'utilisateur clique sur le bouton "Se connecter"
> - **Then** l'accès à l'application lui est refusé
> - **And** un message d'erreur générique "Identifiants incorrects" s'affiche à l'écran
> - **And** les champs de saisie sont réinitialisés mais l'utilisateur reste sur la page de connexion
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le champ "Adresse e-mail" doit valider le format de l'e-mail (présence d'un caractère "@" et d'un nom de domaine valide).
> 2.  Le mot de passe doit être masqué par défaut lors de la saisie, avec une option d'affichage en texte clair.
> 3.  L'accès direct aux pages internes (Dashboard, Chat, Calendrier, Tâches) via leur URL doit être bloqué et rediriger automatiquement vers la page de connexion si l'utilisateur n'est pas authentifié.

### Instructions & Tâches de réalisation

- Intégrer l'écran de connexion en respectant la maquette Figma.
- Ajouter la validation du format de l'adresse e-mail (présence de l'arobase `@` et nom de domaine valide).
- Masquer le mot de passe par défaut avec une option pour basculer en texte clair.
- Gérer la soumission du formulaire d'authentification vers l'API Backend.
- En cas de succès : enregistrer le jeton de session / JWT et rediriger l'utilisateur vers son Tableau de Bord (Dashboard).
- En cas d'échec : réinitialiser les champs de saisie et afficher le message d'erreur générique `"Identifiants incorrects"`.
- Mettre en place un gardien de route (Route Guard) pour bloquer l'accès direct aux URLs protégées si l'utilisateur n'est pas authentifié.

## Création de l'API d'authentification et de gestion de session

- Dev Backend

> ### User Story 1 : Se connecter à son compte (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole de Learn@Home, je souhaite me connecter à mon compte avec mon e-mail et mon mot de passe afin d'accéder à mon espace personnel sécurisé._
>
> #### Scénario 1 : Connexion réussie avec des identifiants valides
>
> - **Given** l'utilisateur est sur la page de connexion de Learn@Home
> - **And** son compte est actif dans le système
> - **When** l'utilisateur saisit son adresse e-mail valide
> - **And** l'utilisateur saisit son mot de passe correct
> - **And** l'utilisateur clique sur le bouton "Se connecter"
> - **Then** l'utilisateur est authentifié avec succès par l'application
> - **And** l'utilisateur est redirigé vers son Tableau de Bord (Dashboard)
> - **And** une session utilisateur sécurisée est ouverte
>
> #### Scénario 2 : Échec de la connexion avec des identifiants invalides
>
> - **Given** l'utilisateur est sur la page de connexion
> - **When** l'utilisateur saisit une adresse e-mail invalide ou un mot de passe incorrect
> - **And** l'utilisateur clique sur le bouton "Se connecter"
> - **Then** l'accès à l'application lui est refusé
> - **And** un message d'erreur générique "Identifiants incorrects" s'affiche à l'écran
> - **And** les champs de saisie sont réinitialisés mais l'utilisateur reste sur la page de connexion
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le champ "Adresse e-mail" doit valider le format de l'e-mail (présence d'un caractère "@" et d'un nom de domaine valide).
> 2.  Le mot de passe doit être masqué par défaut lors de la saisie, avec une option d'affichage en texte clair.
> 3.  L'accès direct aux pages internes (Dashboard, Chat, Calendrier, Tâches) via leur URL doit être bloqué et rediriger automatiquement vers la page de connexion si l'utilisateur n'est pas authentifié.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/auth/login`.
- Vérifier l'existence du compte utilisateur et valider le mot de passe hashé en base de données.
- Générer un jeton d'authentification JWT ou initialiser une session sécurisée en cas de succès.
- En cas d'identifiants incorrects, renvoyer un statut HTTP 401 avec le message d'erreur générique `"Identifiants incorrects"`.
- Implémenter le middleware de sécurité pour protéger les routes privées de l'application (Dashboard, Chat, Calendrier, Tâches).

## Développement du formulaire d'inscription des nouveaux utilisateurs

- Dev Frontend

> ### User Story 2 : Créer un compte (Nouvel Utilisateur)
>
> _En tant que nouvel utilisateur, je souhaite créer un compte en choisissant mon rôle (Élève ou Bénévole) afin de pouvoir utiliser la plateforme Learn@Home._
>
> #### Scénario 1 : Inscription réussie
>
> - **Given** le visiteur est sur la page d'inscription de Learn@Home
> - **When** le visiteur saisit son nom, son prénom et une adresse e-mail unique
> - **And** le visiteur choisit un mot de passe sécurisé et le confirme
> - **And** le visiteur sélectionne le rôle "Élève" ou "Bénévole"
> - **And** le visiteur coche la case d'acceptation des conditions d'utilisation
> - **And** le visiteur clique sur le bouton "S'inscrire"
> - **Then** le système enregistre les informations du nouvel utilisateur
> - **And** un e-mail de confirmation d'inscription lui est envoyé
> - **And** le visiteur est redirigé vers la page de connexion avec un message de confirmation
>
> #### Scénario 2 : Échec de l'inscription à cause de mots de passe différents
>
> - **Given** le visiteur remplit le formulaire d'inscription
> - **When** le visiteur saisit un mot de passe dans le premier champ
> - **And** le visiteur saisit un mot de passe différent dans le champ de confirmation
> - **And** le visiteur clique sur le bouton "S'inscrire"
> - **Then** la création du compte est bloquée
> - **And** un message d'erreur "Les mots de passe ne correspondent pas" s'affiche au-dessus du champ concerné
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Tous les champs du formulaire sont obligatoires.
> 2.  La politique de sécurité du mot de passe exige au moins 8 caractères, dont une majuscule, une minuscule, un chiffre et un caractère spécial.
> 3.  L'adresse e-mail saisie doit être unique. Si elle existe déjà dans le système, la création est rejetée avec un message explicite.

### Instructions & Tâches de réalisation

- Intégrer l'interface de création de compte à partir des maquettes Figma.
- Contrôler la saisie obligatoire de tous les champs (Nom, Prénom, E-mail, Mot de passe, Confirmation, Rôle, CGU).
- Intégrer la validation en temps réel de la politique de sécurité du mot de passe (au moins 8 caractères, 1 majuscule, 1 minuscule, 1 chiffre et 1 caractère spécial).
- Vérifier que la confirmation du mot de passe correspond au mot de passe et afficher `"Les mots de passe ne correspondent pas"` si ce n'est pas le cas.
- Permettre le choix obligatoire du rôle (`Élève` ou `Bénévole`).
- Transmettre les données à l'API et rediriger vers la page de connexion avec un message de confirmation.

## Création de l'API d'inscription et service d'envoi d'e-mail de confirmation

- Dev Backend

> ### User Story 2 : Créer un compte (Nouvel Utilisateur)
>
> _En tant que nouvel utilisateur, je souhaite créer un compte en choisissant mon rôle (Élève ou Bénévole) afin de pouvoir utiliser la plateforme Learn@Home._
>
> #### Scénario 1 : Inscription réussie
>
> - **Given** le visiteur est sur la page d'inscription de Learn@Home
> - **When** le visiteur saisit son nom, son prénom et une adresse e-mail unique
> - **And** le visiteur choisit un mot de passe sécurisé et le confirme
> - **And** le visiteur sélectionne le rôle "Élève" ou "Bénévole"
> - **And** le visiteur coche la case d'acceptation des conditions d'utilisation
> - **And** le visiteur clique sur le bouton "S'inscrire"
> - **Then** le système enregistre les informations du nouvel utilisateur
> - **And** un e-mail de confirmation d'inscription lui est envoyé
> - **And** le visiteur est redirigé vers la page de connexion avec un message de confirmation
>
> #### Scénario 2 : Échec de l'inscription à cause de mots de passe différents
>
> - **Given** le visiteur remplit le formulaire d'inscription
> - **When** le visiteur saisit un mot de passe dans le premier champ
> - **And** le visiteur saisit un mot de passe différent dans le champ de confirmation
> - **And** le visiteur clique sur le bouton "S'inscrire"
> - **Then** la création du compte est bloquée
> - **And** un message d'erreur "Les mots de passe ne correspondent pas" s'affiche au-dessus du champ concerné
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Tous les champs du formulaire sont obligatoires.
> 2.  La politique de sécurité du mot de passe exige au moins 8 caractères, dont une majuscule, une minuscule, un chiffre et un caractère spécial.
> 3.  L'adresse e-mail saisie doit être unique. Si elle existe déjà dans le système, la création est rejetée avec un message explicite.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/auth/register`.
- Controler l'unicité de l'adresse e-mail en base de données et rejeter l'inscription avec un message explicite si elle existe déjà.
- Vérifier le respect des critères de sécurité du mot de passe côté serveur.
- Hacher le mot de passe avant son enregistrement en base de données.
- Créer le compte utilisateur avec le rôle sélectionné (`Élève` ou `Bénévole`).
- Configurer l'envoi d'un e-mail de confirmation d'inscription au nouvel utilisateur.

## Développement des interfaces de demande et de réinitialisation de mot de passe

- Dev Frontend

> ### User Story 3 : Récupérer son mot de passe oublié (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole ayant oublié mon mot de passe, je souhaite demander la réinitialisation de mes accès via mon adresse e-mail afin de retrouver l'accès à mon espace personnel._
>
> #### Scénario 1 : Demande de réinitialisation réussie
>
> - **Given** l'utilisateur est sur la page "Mot de passe oublié"
> - **When** l'utilisateur saisit son adresse e-mail enregistrée
> - **And** l'utilisateur clique sur le bouton "Envoyer le lien de récupération"
> - **Then** le système génère un jeton de réinitialisation sécurisé et temporaire
> - **And** un e-mail contenant un lien de réinitialisation unique est envoyé à l'adresse saisie
> - **And** un message général confirme l'envoi du message sur l'écran de l'utilisateur
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Pour éviter l'aspiration d'e-mails (User Enumeration), le message de confirmation affiché à l'écran doit être identique, que l'e-mail existe ou non dans le système.
> 2.  Le lien de récupération reçu par e-mail doit expirer après une heure d'inactivité.
> 3.  Le clic sur le lien doit ouvrir un formulaire sécurisé permettant de définir un nouveau mot de passe conforme aux exigences de sécurité de l'US 2.

### Instructions & Tâches de réalisation

- Créer la page "Mot de passe oublié" avec saisie de l'e-mail selon les maquettes Figma.
- Afficher un message de confirmation générique après soumission du formulaire.
- Développer la page de réinitialisation du mot de passe (accessible via le lien sécurisé reçu par e-mail).
- Intégrer la validation des règles de complexité pour le nouveau mot de passe.
- Envoyer le nouveau mot de passe à l'API Backend et rediriger vers l'écran de connexion après confirmation.

## Création de l'API de réinitialisation de mot de passe et gestion des jetons temporaires

- Dev Backend

> ### User Story 3 : Récupérer son mot de passe oublié (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole ayant oublié mon mot de passe, je souhaite demander la réinitialisation de mes accès via mon adresse e-mail afin de retrouver l'accès à mon espace personnel._
>
> #### Scénario 1 : Demande de réinitialisation réussie
>
> - **Given** l'utilisateur est sur la page "Mot de passe oublié"
> - **When** l'utilisateur saisit son adresse e-mail enregistrée
> - **And** l'utilisateur clique sur le bouton "Envoyer le lien de récupération"
> - **Then** le système génère un jeton de réinitialisation sécurisé et temporaire
> - **And** un e-mail contenant un lien de réinitialisation unique est envoyé à l'adresse saisie
> - **And** un message général confirme l'envoi du message sur l'écran de l'utilisateur
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Pour éviter l'aspiration d'e-mails (User Enumeration), le message de confirmation affiché à l'écran doit être identique, que l'e-mail existe ou non dans le système.
> 2.  Le lien de récupération reçu par e-mail doit expirer après une heure d'inactivité.
> 3.  Le clic sur le lien doit ouvrir un formulaire sécurisé permettant de définir un nouveau mot de passe conforme aux exigences de sécurité de l'US 2.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/auth/forgot-password`.
- Générer un jeton de réinitialisation sécurisé avec une durée de validité d'une heure.
- Transmettre l'e-mail contenant le lien de récupération personnalisé.
- Garantir une réponse API neutre et identique (prévention du User Enumeration) que l'adresse e-mail existe ou non.
- Créer le point de terminaison POST `/api/auth/reset-password` pour valider le jeton et enregistrer le nouveau mot de passe haché.

# Module Tableau de Bord (Dashboard)

## Développement de l'interface du Tableau de Bord et intégration des widgets

- Dev Frontend

> ### User Story 4 : Consulter le Tableau de Bord (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole connecté, je souhaite visualiser une synthèse de mon activité sur mon Tableau de Bord afin de suivre mes priorités de la journée en un coup d'œil._
>
> #### Scénario 1 : Affichage des informations de synthèse
>
> - **Given** l'utilisateur est connecté et navigue sur sa page d'accueil
> - **When** le Tableau de Bord se charge
> - **Then** le système affiche un bloc "Tâches" récapitulant les prochaines actions à mener
> - **And** le système affiche un bloc "Calendrier" listant les événements et rendez-vous des 7 prochains jours
> - **And** le système affiche un badge de notification contenant le nombre de messages non lus dans le Chat
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le bloc "Tâches" affiche au maximum les 3 tâches les plus urgentes non terminées.
> 2.  Si le nombre de messages non lus est égal à zéro, le badge sur l'indicateur de messagerie doit être masqué.
> 3.  Chaque bloc de synthèse doit comporter un bouton ou lien d'action permettant de basculer instantanément sur le module concerné (Tâches, Calendrier ou Chat).

### Instructions & Tâches de réalisation

- Intégrer la page d'accueil du Tableau de Bord en suivant la maquette Figma.
- Créer le widget "Tâches" listant au maximum les 3 tâches les plus urgentes non terminées.
- Créer le widget "Calendrier" récapitulant les événements prévus pour les 7 prochains jours.
- Intégrer le badge de notification affichant le nombre de messages non lus sur l'icône du Chat (masqué si le nombre est égal à zéro).
- Configurer les liens de redirection interactive sur chaque widget vers leurs modules respectifs.

## Création de l'API d'agrégation de données pour le Tableau de Bord

- Dev Backend

> ### User Story 4 : Consulter le Tableau de Bord (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole connecté, je souhaite visualiser une synthèse de mon activité sur mon Tableau de Bord afin de suivre mes priorités de la journée en un coup d'œil._
>
> #### Scénario 1 : Affichage des informations de synthèse
>
> - **Given** l'utilisateur est connecté et navigue sur sa page d'accueil
> - **When** le Tableau de Bord se charge
> - **Then** le système affiche un bloc "Tâches" récapitulant les prochaines actions à mener
> - **And** le système affiche un bloc "Calendrier" listant les événements et rendez-vous des 7 prochains jours
> - **And** le système affiche un badge de notification contenant le nombre de messages non lus dans le Chat
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le bloc "Tâches" affiche au maximum les 3 tâches les plus urgentes non terminées.
> 2.  Si le nombre de messages non lus est égal à zéro, le badge sur l'indicateur de messagerie doit être masqué.
> 3.  Chaque bloc de synthèse doit comporter un bouton ou lien d'action permettant de basculer instantanément sur le module concerné (Tâches, Calendrier ou Chat).

### Instructions & Tâches de réalisation

- Créer le point de terminaison GET `/api/dashboard/summary`.
- Récupérer les 3 tâches non terminées avec l'échéance la plus proche pour l'utilisateur connecté.
- Extraire la liste des événements du calendrier prévus dans les 7 prochains jours.
- Calculer le nombre total de messages non lus destinés à l'utilisateur connecté dans le Chat.

# Module Messagerie Instantanée (Chat)

## Développement de l'interface d'envoi et d'affichage des messages en temps réel

- Dev Frontend

> ### User Story 5 : Envoyer un message (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite rédiger et envoyer un message à un contact afin d'échanger en temps réel._
>
> #### Scénario 1 : Envoi de message réussi dans une discussion active
>
> - **Given** l'utilisateur a ouvert le module de Chat
> - **And** une discussion est active avec un contact sélectionné
> - **When** l'utilisateur saisit du texte dans le champ de saisie
> - **And** l'utilisateur clique sur le bouton d'envoi ou appuie sur la touche "Entrée"
> - **Then** le message s'ajoute instantanément en bas de l'historique de discussion
> - **And** le message affiche l'avatar de l'expéditeur, le contenu, l'heure d'envoi et un indicateur de statut "Envoyé"
> - **And** le champ de saisie est vidé pour permettre un nouvel envoi
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le système doit interdire l'envoi de messages vides ou contenant uniquement des espaces.
> 2.  La zone d'affichage des messages doit effectuer un défilement automatique vers le bas (auto-scroll) à chaque nouveau message reçu ou envoyé.
> 3.  L'indicateur de statut doit évoluer de "Envoyé" à "Lu" lorsque le destinataire affiche la conversation correspondante.

### Instructions & Tâches de réalisation

- Développer la zone principale de messagerie instantanée (zone de saisie, historique, avatars, horodatage, statut).
- Empêcher l'envoi de messages vides ou composés exclusivement d'espaces.
- Autoriser l'envoi du message via le bouton "Envoyer" ou l'appui sur la touche "Entrée".
- Implémenter le défilement automatique (auto-scroll) vers le bas lors de l'envoi ou de la réception d'un nouveau message.
- Afficher les indicateurs de statut (`Envoyé`, `Lu`).
- Connecter le composant au canal temps réel WebSockets.

## Mise en place du service WebSockets et de l'API d'envoi de messages

- Dev Backend

> ### User Story 5 : Envoyer un message (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite rédiger et envoyer un message à un contact afin d'échanger en temps réel._
>
> #### Scénario 1 : Envoi de message réussi dans une discussion active
>
> - **Given** l'utilisateur a ouvert le module de Chat
> - **And** une discussion est active avec un contact sélectionné
> - **When** l'utilisateur saisit du texte dans le champ de saisie
> - **And** l'utilisateur clique sur le bouton d'envoi ou appuie sur la touche "Entrée"
> - **Then** le message s'ajoute instantanément en bas de l'historique de discussion
> - **And** le message affiche l'avatar de l'expéditeur, le contenu, l'heure d'envoi et un indicateur de statut "Envoyé"
> - **And** le champ de saisie est vidé pour permettre un nouvel envoi
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le système doit interdire l'envoi de messages vides ou contenant uniquement des espaces.
> 2.  La zone d'affichage des messages doit effectuer un défilement automatique vers le bas (auto-scroll) à chaque nouveau message reçu ou envoyé.
> 3.  L'indicateur de statut doit évoluer de "Envoyé" à "Lu" lorsque le destinataire affiche la conversation correspondante.

### Instructions & Tâches de réalisation

- Configurer le serveur WebSockets pour la gestion des communications bidirectionnelles en temps réel.
- Développer l'événement / endpoint d'envoi de message avec contrôle de contenu non vide.
- Enregistrer le message en base de données avec la date/heure d'envoi et le statut initial `Envoyé`.
- Transmettre l'événement instantanément au destinataire connecté.
- Mettre à jour et émettre le statut `Lu` dès que le destinataire affiche la conversation.

## Développement du composant d'affichage de l'historique de discussion et lazy loading

- Dev Frontend

> ### User Story 6 : Consulter l'historique de discussion (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite sélectionner un de mes contacts afin de recharger et lire l'ensemble des messages échangés avec lui._
>
> #### Scénario 1 : Chargement d'une conversation existante
>
> - **Given** l'utilisateur est sur l'interface de Chat
> - **When** l'utilisateur sélectionne un contact dans sa liste de conversations à gauche
> - **Then** le système charge l'historique des échanges par ordre chronologique décroissant (du plus ancien en haut au plus récent en bas)
> - **And** les messages envoyés par l'utilisateur s'alignent à droite avec une couleur de fond distincte
> - **And** les messages reçus du contact s'alignent à gauche avec une autre couleur de fond
> - **And** les messages non lus de cette discussion passent au statut "Lu"
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le chargement de l'historique doit être optimisé par un système de pagination ou de chargement progressif au défilement vers le haut (lazy loading) afin de préserver les performances du système.
> 2.  L'affichage doit grouper les messages par jour avec un indicateur de date lisible (ex: "Aujourd'hui", "Hier", "Lundi 14 Octobre").

### Instructions & Tâches de réalisation

- Recharger l'historique de la discussion lors du clic sur un contact dans la liste de gauche.
- Positionner les messages envoyés par l'utilisateur à droite (couleur spécifique) et les messages reçus à gauche.
- Grouper chronologiquement les échanges avec des indicateurs de date lisibles (`Aujourd'hui`, `Hier`, `Lundi 14 Octobre`).
- Intégrer le chargement progressif au défilement vers le haut (lazy loading / pagination) pour charger les anciens messages.
- Transmettre la confirmation de lecture pour les messages non lus lors de l'ouverture du chat.

## Création de l'API de récupération paginée de l'historique de discussion

- Dev Backend

> ### User Story 6 : Consulter l'historique de discussion (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite sélectionner un de mes contacts afin de recharger et lire l'ensemble des messages échangés avec lui._
>
> #### Scénario 1 : Chargement d'une conversation existante
>
> - **Given** l'utilisateur est sur l'interface de Chat
> - **When** l'utilisateur sélectionne un contact dans sa liste de conversations à gauche
> - **Then** le système charge l'historique des échanges par ordre chronologique décroissant (du plus ancien en haut au plus récent en bas)
> - **And** les messages envoyés par l'utilisateur s'alignent à droite avec une couleur de fond distincte
> - **And** les messages reçus du contact s'alignent à gauche avec une autre couleur de fond
> - **And** les messages non lus de cette discussion passent au statut "Lu"
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le chargement de l'historique doit être optimisé par un système de pagination ou de chargement progressif au défilement vers le haut (lazy loading) afin de préserver les performances du système.
> 2.  L'affichage doit grouper les messages par jour avec un indicateur de date lisible (ex: "Aujourd'hui", "Hier", "Lundi 14 Octobre").

### Instructions & Tâches de réalisation

- Créer le point de terminaison GET `/api/chat/messages/:contact_id` supportant la pagination (limit / cursor).
- Retourner l'historique par ordre chronologique.
- Mettre à jour automatiquement les messages reçus non lus vers le statut `Lu` à la consultation.

## Développement de l'interface de recherche et d'ajout de contact

- Dev Frontend

> ### User Story 7 : Ajouter un contact (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite rechercher un autre utilisateur par son adresse e-mail afin de l'ajouter à ma liste de chat._
>
> #### Scénario 1 : Ajout d'un contact existant
>
> - **Given** l'utilisateur est sur l'interface de Chat
> - **And** l'utilisateur clique sur le bouton "Ajouter un contact"
> - **When** l'utilisateur saisit l'adresse e-mail d'un autre membre inscrit sur Learn@Home
> - **And** l'utilisateur valide sa recherche
> - **Then** le système ajoute le contact dans la liste de chat de l'utilisateur à gauche
> - **And** le système ouvre automatiquement la nouvelle discussion vide dans la zone centrale
>
> #### Scénario 2 : Recherche d'un contact inexistant
>
> - **Given** l'utilisateur effectue une recherche de contact
> - **When** l'utilisateur saisit une adresse e-mail qui n'existe pas dans le système
> - **And** l'utilisateur valide sa recherche
> - **Then** l'ajout est bloqué
> - **And** un message d'erreur "Aucun utilisateur trouvé pour cette adresse e-mail" s'affiche
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Un utilisateur ne peut pas s'ajouter lui-même à sa propre liste de contacts.
> 2.  Si le contact recherché est déjà présent dans la liste, le système doit simplement basculer l'utilisateur sur la discussion existante sans créer de doublon.

### Instructions & Tâches de réalisation

- Développer le bouton "Ajouter un contact" et la boîte de dialogue de recherche par e-mail.
- Envoyer la requête de recherche d'e-mail à l'API Backend.
- Si le membre existe : l'ajouter dans la liste de gauche et ouvrir la discussion vide associée.
- Si le contact est déjà dans la liste : basculer automatiquement sur sa discussion sans doublon.
- En cas d'erreur : afficher le message `"Aucun utilisateur trouvé pour cette adresse e-mail"`.

## Création de l'API de recherche et d'association de nouveaux contacts

- Dev Backend

> ### User Story 7 : Ajouter un contact (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite rechercher un autre utilisateur par son adresse e-mail afin de l'ajouter à ma liste de chat._
>
> #### Scénario 1 : Ajout d'un contact existant
>
> - **Given** l'utilisateur est sur l'interface de Chat
> - **And** l'utilisateur clique sur le bouton "Ajouter un contact"
> - **When** l'utilisateur saisit l'adresse e-mail d'un autre membre inscrit sur Learn@Home
> - **And** l'utilisateur valide sa recherche
> - **Then** le système ajoute le contact dans la liste de chat de l'utilisateur à gauche
> - **And** le système ouvre automatiquement la nouvelle discussion vide dans la zone centrale
>
> #### Scénario 2 : Recherche d'un contact inexistant
>
> - **Given** l'utilisateur effectue une recherche de contact
> - **When** l'utilisateur saisit une adresse e-mail qui n'existe pas dans le système
> - **And** l'utilisateur valide sa recherche
> - **Then** l'ajout est bloqué
> - **And** un message d'erreur "Aucun utilisateur trouvé pour cette adresse e-mail" s'affiche
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Un utilisateur ne peut pas s'ajouter lui-même à sa propre liste de contacts.
> 2.  Si le contact recherché est déjà présent dans la liste, le système doit simplement basculer l'utilisateur sur la discussion existante sans créer de doublon.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/chat/contacts` acceptant l'adresse e-mail.
- Contrôler l'existence du compte recherché en base de données.
- Empêcher l'utilisateur de s'ajouter lui-même comme contact.
- Vérifier si l'utilisateur appartient déjà à la liste de contacts active pour éviter la création de doublons.
- Enregistrer la relation et renvoyer les informations du contact à l'utilisateur.

## Développement de l'interface de suppression d'un contact de la liste active

- Dev Frontend

> ### User Story 8 : Supprimer un contact (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite retirer un contact de ma liste de conversations afin de nettoyer mon interface de messagerie._
>
> #### Scénario 1 : Suppression de contact validée
>
> - **Given** l'utilisateur est sur l'interface de Chat et consulte sa liste de conversations
> - **When** l'utilisateur clique sur l'option "Supprimer le contact" à côté du nom de l'interlocuteur
> - **And** l'utilisateur valide sa décision dans la boîte de confirmation
> - **Then** le contact est masqué de sa liste active à gauche
> - **And** l'écran principal de discussion se réinitialise à l'état neutre (aucun contact sélectionné)
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Une boîte de dialogue de confirmation doit s'afficher avant toute suppression effective.
> 2.  La suppression d'un contact retire le contact de la liste active mais n'efface pas l'historique des messages de la base de données (si le contact est rajouté ultérieurement, l'historique est restauré).

### Instructions & Tâches de réalisation

- Intégrer l'option "Supprimer le contact" dans le menu d'action du contact dans la liste.
- Afficher une boîte de dialogue de confirmation avant de valider la suppression.
- Retirer le contact de la liste affichée à gauche.
- Réinitialiser l'écran central à son état neutre (aucun contact sélectionné).

## Création de l'API de retrait d'un contact de la liste active

- Dev Backend

> ### User Story 8 : Supprimer un contact (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite retirer un contact de ma liste de conversations afin de nettoyer mon interface de messagerie._
>
> #### Scénario 1 : Suppression de contact validée
>
> - **Given** l'utilisateur est sur l'interface de Chat et consulte sa liste de conversations
> - **When** l'utilisateur clique sur l'option "Supprimer le contact" à côté du nom de l'interlocuteur
> - **And** l'utilisateur valide sa décision dans la boîte de confirmation
> - **Then** le contact est masqué de sa liste active à gauche
> - **And** l'écran principal de discussion se réinitialise à l'état neutre (aucun contact sélectionné)
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Une boîte de dialogue de confirmation doit s'afficher avant toute suppression effective.
> 2.  La suppression d'un contact retire le contact de la liste active mais n'efface pas l'historique des messages de la base de données (si le contact est rajouté ultérieurement, l'historique est restauré).

### Instructions & Tâches de réalisation

- Créer le point de terminaison DELETE `/api/chat/contacts/:contact_id`.
- Masquer la relation dans la liste de l'utilisateur sans supprimer les messages stockés en base de données.
- Permettre le rétablissement de l'historique si l'utilisateur réajoute le contact ultérieurement.

# Module Calendrier

## Développement du composant Calendrier interactif et gestion des vues

- Dev Frontend

> ### User Story 9 : Consulter le calendrier (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite visualiser mon calendrier interactif afin de planifier mon temps et de consulter mes cours ou rendez-vous._
>
> #### Scénario 1 : Navigation et affichage des créneaux
>
> - **Given** l'utilisateur est sur la page Calendrier
> - **When** l'utilisateur sélectionne la vue mensuelle, hebdomadaire ou journalière
> - **And** l'utilisateur navigue vers une période temporelle spécifique
> - **Then** le calendrier se met à jour pour afficher les événements correspondants à la période sélectionnée
> - **And** chaque événement est représenté par un bloc affichant le titre, l'horaire précis et un code couleur correspondant à la catégorie de l'événement
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le calendrier s'ouvre par défaut sur la vue mensuelle avec la date du jour mise en valeur graphiquement.
> 2.  Un clic sur un bloc d'événement doit ouvrir une modale de détails affichant le titre complet, la description, les participants concernés et le lien de la réunion virtuelle ou le lieu physique.

### Instructions & Tâches de réalisation

- Développer l'interface interactive du calendrier en respectant la maquette Figma.
- Permettre de basculer entre la vue mensuelle, hebdomadaire et journalière (vue mensuelle par défaut).
- Mettre en valeur visuellement la date du jour.
- Afficher les créneaux avec leur titre, leur horaire précis et un code couleur associé à la catégorie.
- Déclencher une modale d'information au clic sur un événement (titre complet, description, liste des participants, lien visio ou lieu).

## Création de l'API de récupération des événements du calendrier

- Dev Backend

> ### User Story 9 : Consulter le calendrier (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite visualiser mon calendrier interactif afin de planifier mon temps et de consulter mes cours ou rendez-vous._
>
> #### Scénario 1 : Navigation et affichage des créneaux
>
> - **Given** l'utilisateur est sur la page Calendrier
> - **When** l'utilisateur sélectionne la vue mensuelle, hebdomadaire ou journalière
> - **And** l'utilisateur navigue vers une période temporelle spécifique
> - **Then** le calendrier se met à jour pour afficher les événements correspondants à la période sélectionnée
> - **And** chaque événement est représenté par un bloc affichant le titre, l'horaire précis et un code couleur correspondant à la catégorie de l'événement
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le calendrier s'ouvre par défaut sur la vue mensuelle avec la date du jour mise en valeur graphiquement.
> 2.  Un clic sur un bloc d'événement doit ouvrir une modale de détails affichant le titre complet, la description, les participants concernés et le lien de la réunion virtuelle ou le lieu physique.

### Instructions & Tâches de réalisation

- Créer le point de terminaison GET `/api/calendar/events` acceptant des paramètres d'intervalle (`start_date`, `end_date`).
- Requéter les événements où l'utilisateur connecté est organisateur ou participant invité.
- Inclure les informations détaillées : catégorie, couleur, plages horaires, lien/lieu, liste des invités.

## Développement des formulaires de création, modification et annulation d'événements

- Dev Frontend

> ### User Story 10 : Gérer les événements et rendez-vous (Élève / Bénévole)
>
> _En tant que **Bénévole** (et non élève),, je souhaite planifier, modifier ou annuler un événement dans mon calendrier afin de maintenir mon emploi du temps à jour._
>
> #### Scénario 1 : Création d'un événement réussie
>
> - **Given** l'utilisateur est sur la page Calendrier
> - **When** l'utilisateur clique sur un créneau horaire vide ou clique sur le bouton "Nouvel événement"
> - **And** l'utilisateur saisit le titre, la date, l'heure de début et l'heure de fin de l'événement
> - **And** l'utilisateur sélectionne les participants invités
> - **And** l'utilisateur clique sur "Enregistrer"
> - **Then** l'événement est créé dans le système
> - **And** le nouvel événement s'affiche sur le calendrier de l'organisateur et des participants invités
> - **And** une notification de planification est envoyée par e-mail aux invités
>
> #### Scénario 2 : Blocage de la création d'un événement incohérent
>
> - **Given** l'utilisateur remplit le formulaire de création d'un événement
> - **When** l'utilisateur choisit une heure de fin antérieure à l'heure de début
> - **And** l'utilisateur tente de valider l'enregistrement
> - **Then** l'enregistrement est refusé
> - **And** un message d'erreur "L'heure de fin doit être postérieure à l'heure de début" s'affiche
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Les champs "Titre", "Date", "Heure de début" et "Heure de fin" sont obligatoires.
> 2.  Seul le créateur de l'événement a l'autorisation de le modifier ou de l'annuler (les participants invités le voient en mode lecture seule).
> 3.  L'annulation d'un événement doit faire l'objet d'une confirmation de la part du créateur et d'un envoi automatique d'e-mail d'annulation aux participants.

### Instructions & Tâches de réalisation

- Ouvrir le formulaire de création lors du clic sur un créneau libre ou le bouton "Nouvel événement".
- Contrôler les champs obligatoires (Titre, Date, Heure de début, Heure de fin).
- Valider que l'heure de fin est strictement postérieure à l'heure de début ; afficher `"L'heure de fin doit être postérieure à l'heure de début"` si la condition n'est pas remplie.
- Permettre d'inviter des participants à l'événement.
- Désactiver la modification ou l'annulation pour les participants invités (mode lecture seule).
- Afficher une modale de confirmation lors de l'annulation d'un événement par son organisateur.

## Création de l'API de gestion des événements et notifications e-mail

- Dev Backend

> ### User Story 10 : Gérer les événements et rendez-vous (Élève / Bénévole)
>
> _En tant que **Bénévole** (et non élève),, je souhaite planifier, modifier ou annuler un événement dans mon calendrier afin de maintenir mon emploi du temps à jour._
>
> #### Scénario 1 : Création d'un événement réussie
>
> - **Given** l'utilisateur est sur la page Calendrier
> - **When** l'utilisateur clique sur un créneau horaire vide ou clique sur le bouton "Nouvel événement"
> - **And** l'utilisateur saisit le titre, la date, l'heure de début et l'heure de fin de l'événement
> - **And** l'utilisateur sélectionne les participants invités
> - **And** l'utilisateur clique sur "Enregistrer"
> - **Then** l'événement est créé dans le système
> - **And** le nouvel événement s'affiche sur le calendrier de l'organisateur et des participants invités
> - **And** une notification de planification est envoyée par e-mail aux invités
>
> #### Scénario 2 : Blocage de la création d'un événement incohérent
>
> - **Given** l'utilisateur remplit le formulaire de création d'un événement
> - **When** l'utilisateur choisit une heure de fin antérieure à l'heure de début
> - **And** l'utilisateur tente de valider l'enregistrement
> - **Then** l'enregistrement est refusé
> - **And** un message d'erreur "L'heure de fin doit être postérieure à l'heure de début" s'affiche
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Les champs "Titre", "Date", "Heure de début" et "Heure de fin" sont obligatoires.
> 2.  Seul le créateur de l'événement a l'autorisation de le modifier ou de l'annuler (les participants invités le voient en mode lecture seule).
> 3.  L'annulation d'un événement doit faire l'objet d'une confirmation de la part du créateur et d'un envoi automatique d'e-mail d'annulation aux participants.

### Instructions & Tâches de réalisation

- Créer les points de terminaison POST, PUT et DELETE sur `/api/calendar/events`.
- Valider la cohérence des horaires fin > début côté serveur.
- Contrôler les autorisations : seul l'organisateur peut modifier ou supprimer l'événement.
- Envoyer un e-mail de notification de planification à l'ensemble des invités lors de la création ou modification.
- Envoyer un e-mail automatique d'annulation aux participants invités lors de la suppression de l'événement.

# Module Gestion des Tâches

## Développement de l'interface de gestion, validation et suppression des tâches

- Dev Frontend

> ### User Story 11 : Lister et supprimer ses tâches (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite consulter la liste de mes tâches en cours afin d'organiser mes devoirs et mon travail personnel._
>
> #### Scénario 1 : Consultation et validation d'une tâche
>
> - **Given** l'utilisateur navigue sur la page "Gestion des Tâches"
> - **When** la liste se charge
> - **Then** le système affiche deux sections distinctes : "Tâches en cours" et "Tâches terminées"
> - **When** l'utilisateur coche la case de validation d'une tâche "Faire l'exercice de mathématiques"
> - **Then** la tâche est immédiatement barrée visuellement et transférée dans la section "Tâches terminées"
> - **And** le compteur de tâches en cours du Tableau de Bord est décrémenté
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Chaque tâche affiche son libellé, son auteur (si assignée par un Bénévole) et sa date d'échéance optionnelle.
> 2.  Une tâche marquée comme terminée peut être décochée à tout moment, ce qui la replace dans la section "Tâches en cours".
> 3.  Un bouton de suppression définitive (icône poubelle) permet de supprimer une tâche, après une confirmation de l'utilisateur.

### Instructions & Tâches de réalisation

- Développer la page de gestion des tâches organisée en deux sections : "Tâches en cours" et "Tâches terminées".
- Afficher pour chaque tâche son libellé, son auteur (si assignée par un bénévole) et sa date d'échéance.
- Offrir la possibilité de cocher/décocher une tâche pour la barrer visuellement et la déplacer automatiquement dans la section adéquate.
- Répercuter la modification sur le compteur de tâches en cours du Tableau de Bord.
- Ajouter le bouton de suppression avec icône poubelle et modale de confirmation.

## Création de l'API de mise à jour du statut et de suppression des tâches

- Dev Backend

> ### User Story 11 : Lister et supprimer ses tâches (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite consulter la liste de mes tâches en cours afin d'organiser mes devoirs et mon travail personnel._
>
> #### Scénario 1 : Consultation et validation d'une tâche
>
> - **Given** l'utilisateur navigue sur la page "Gestion des Tâches"
> - **When** la liste se charge
> - **Then** le système affiche deux sections distinctes : "Tâches en cours" et "Tâches terminées"
> - **When** l'utilisateur coche la case de validation d'une tâche "Faire l'exercice de mathématiques"
> - **Then** la tâche est immédiatement barrée visuellement et transférée dans la section "Tâches terminées"
> - **And** le compteur de tâches en cours du Tableau de Bord est décrémenté
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Chaque tâche affiche son libellé, son auteur (si assignée par un Bénévole) et sa date d'échéance optionnelle.
> 2.  Une tâche marquée comme terminée peut être décochée à tout moment, ce qui la replace dans la section "Tâches en cours".
> 3.  Un bouton de suppression définitive (icône poubelle) permet de supprimer une tâche, après une confirmation de l'utilisateur.

### Instructions & Tâches de réalisation

- Créer le point de terminaison GET `/api/tasks` pour lister les tâches de l'utilisateur.
- Créer le point de terminaison PATCH `/api/tasks/:id/status` pour basculer le statut entre en cours et terminée.
- Créer le point de terminaison DELETE `/api/tasks/:id` pour la suppression définitive d'une tâche après vérification des droits.

## Développement de la barre d'ajout rapide de tâche personnelle

- Dev Frontend

> ### User Story 12 : Créer une tâche pour soi-même (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite ajouter une tâche à ma liste personnelle afin de planifier mes objectifs de révision ou de préparation._
>
> #### Scénario 1 : Création d'une tâche personnelle
>
> - **Given** l'utilisateur est sur la page de gestion des tâches
> - **When** l'utilisateur saisit le libellé "Préparer l'exposé d'anglais" dans la barre d'ajout rapide
> - **And** l'utilisateur sélectionne une date d'échéance valide
> - **And** l'utilisateur clique sur le bouton "Ajouter"
> - **Then** le système enregistre la tâche
> - **And** la tâche s'affiche instantanément en tête de la liste des "Tâches en cours" de l'utilisateur
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le libellé de la tâche est obligatoire et doit comporter au moins 3 caractères.
> 2.  Il est impossible de choisir une date d'échéance passée.
> 3.  La tâche ainsi créée est privée et visible exclusivement par son auteur.

### Instructions & Tâches de réalisation

- Intégrer la barre d'ajout rapide de tâche sur l'interface de gestion des tâches.
- Exiger un libellé de 3 caractères au minimum.
- Interdire la sélection d'une date d'échéance passée.
- Ajouter instantanément la tâche créée au sommet de la section "Tâches en cours".

## Création de l'API de création de tâches personnelles

- Dev Backend

> ### User Story 12 : Créer une tâche pour soi-même (Élève / Bénévole)
>
> _En tant qu'Élève ou Bénévole, je souhaite ajouter une tâche à ma liste personnelle afin de planifier mes objectifs de révision ou de préparation._
>
> #### Scénario 1 : Création d'une tâche personnelle
>
> - **Given** l'utilisateur est sur la page de gestion des tâches
> - **When** l'utilisateur saisit le libellé "Préparer l'exposé d'anglais" dans la barre d'ajout rapide
> - **And** l'utilisateur sélectionne une date d'échéance valide
> - **And** l'utilisateur clique sur le bouton "Ajouter"
> - **Then** le système enregistre la tâche
> - **And** la tâche s'affiche instantanément en tête de la liste des "Tâches en cours" de l'utilisateur
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Le libellé de la tâche est obligatoire et doit comporter au moins 3 caractères.
> 2.  Il est impossible de choisir une date d'échéance passée.
> 3.  La tâche ainsi créée est privée et visible exclusivement par son auteur.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/tasks/personal`.
- Contrôler que le libellé contient au moins 3 caractères.
- Vérifier que la date d'échéance sélectionnée n'est pas antérieure à la date actuelle.
- Enregistrer la tâche avec un niveau d'accès strictement privé pour l'utilisateur qui l'a créée.

## Développement de l'interface d'assignation de tâche à un élève pour les Bénévoles

- Dev Frontend

> ### User Story 13 : Créer une tâche pour l'élève suivi (Bénévole uniquement)
>
> _En tant que Bénévole connecté, je souhaite créer une tâche pour un élève que j'accompagne afin de lui attribuer du travail ou des objectifs pédagogiques précis._
>
> #### Scénario 1 : Attribution d'une tâche par un Bénévole
>
> - **Given** le Bénévole est connecté à son compte sur la page de gestion des tâches
> - **When** le Bénévole clique sur "Assigner une tâche à un élève"
> - **And** le Bénévole saisit le libellé "Rédiger l'introduction de l'exposé"
> - **And** le Bénévole sélectionne le nom de l'élève suivi dans son menu déroulant
> - **And** le Bénévole sélectionne une date d'échéance
> - **And** le Bénévole clique sur "Assigner la tâche"
> - **Then** la tâche est créée et ajoutée à la liste des "Tâches en cours" de l'élève sélectionné
> - **And** la tâche porte la mention visuelle "Assignée par mon tuteur [Nom du Bénévole]" dans l'interface de l'élève
>
> #### Scénario 2 : Refus d'accès pour les Élèves
>
> - **Given** un utilisateur connecté avec le rôle "Élève" est sur sa page de gestion des tâches
> - **When** l'utilisateur cherche l'option ou le bouton "Assigner une tâche à un élève"
> - **Then** cette option ne s'affiche pas sur son écran
> - **And** si l'Élève tente de forcer l'accès via une URL ou une requête API directe, l'accès lui est refusé avec une erreur "Action non autorisée"
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Seuls les utilisateurs ayant le rôle "Bénévole" peuvent assigner des tâches à des tiers.
> 2.  Un Bénévole ne peut assigner des tâches qu'aux élèves qui lui sont officiellement liés par le système d'accompagnement.
> 3.  L'élève destinataire peut cocher la tâche comme "Terminée" pour signaler son avancement, mais il ne peut pas modifier le titre de la tâche défini par le Bénévole. Une fois cochée par l'élève, le Bénévole reçoit une notification d'accomplissement.

### Instructions & Tâches de réalisation

- Afficher l'option "Assigner une tâche à un élève" uniquement pour les utilisateurs ayant le rôle "Bénévole" (masquer la fonction pour le rôle "Élève").
- Proposer la liste déroulante des élèves accompagnés par le bénévole.
- Côté élève : afficher la mention visuelle `"Assignée par mon tuteur [Nom du Bénévole]"`.
- Verrouiller la modification du titre de la tâche pour l'élève (lecture seule).
- Notifier le bénévole lorsque l'élève valide la réalisation de la tâche.

## Création de l'API d'assignation et contrôle des permissions des tâches attribuées

- Dev Backend

> ### User Story 13 : Créer une tâche pour l'élève suivi (Bénévole uniquement)
>
> _En tant que Bénévole connecté, je souhaite créer une tâche pour un élève que j'accompagne afin de lui attribuer du travail ou des objectifs pédagogiques précis._
>
> #### Scénario 1 : Attribution d'une tâche par un Bénévole
>
> - **Given** le Bénévole est connecté à son compte sur la page de gestion des tâches
> - **When** le Bénévole clique sur "Assigner une tâche à un élève"
> - **And** le Bénévole saisit le libellé "Rédiger l'introduction de l'exposé"
> - **And** le Bénévole sélectionne le nom de l'élève suivi dans son menu déroulant
> - **And** le Bénévole sélectionne une date d'échéance
> - **And** le Bénévole clique sur "Assigner la tâche"
> - **Then** la tâche est créée et ajoutée à la liste des "Tâches en cours" de l'élève sélectionné
> - **And** la tâche porte la mention visuelle "Assignée par mon tuteur [Nom du Bénévole]" dans l'interface de l'élève
>
> #### Scénario 2 : Refus d'accès pour les Élèves
>
> - **Given** un utilisateur connecté avec le rôle "Élève" est sur sa page de gestion des tâches
> - **When** l'utilisateur cherche l'option ou le bouton "Assigner une tâche à un élève"
> - **Then** cette option ne s'affiche pas sur son écran
> - **And** si l'Élève tente de forcer l'accès via une URL ou une requête API directe, l'accès lui est refusé avec une erreur "Action non autorisée"
>
> #### Critères d'acceptation complémentaires :
>
> 1.  Seuls les utilisateurs ayant le rôle "Bénévole" peuvent assigner des tâches à des tiers.
> 2.  Un Bénévole ne peut assigner des tâches qu'aux élèves qui lui sont officiellement liés par le système d'accompagnement.
> 3.  L'élève destinataire peut cocher la tâche comme "Terminée" pour signaler son avancement, mais il ne peut pas modifier le titre de la tâche défini par le Bénévole. Une fois cochée par l'élève, le Bénévole reçoit une notification d'accomplissement.

### Instructions & Tâches de réalisation

- Créer le point de terminaison POST `/api/tasks/assign`.
- Vérifier que l'utilisateur ayant soumis la demande possède le rôle "Bénévole" (retourner un statut HTTP 403 `"Action non autorisée"` en cas de tentative par un Élève).
- Vérifier que l'élève destinataire est bien lié au bénévole dans le système.
- Interdire toute modification du titre de la tâche par l'élève.
- Envoyer une notification au bénévole référent lorsque l'élève marque la tâche comme terminée.
