# Veille de Marché

## 1. Analyse de 5 Acteurs du Marche

### Superprof

Superprof est une plateforme commerciale de mise en relation directe entre élèves et enseignants.

- **Fonctionnalités clés :**
    - Moteur de recherche.
    - Messagerie interne.
    - Systeme de paiement mensuel ou à l'heure.
- **Implications techniques :**
    - Site web.
    - Base de données relationnelle avec indexation pour la recherche avec filtres.
    - API/librairie d'affichage de cartes (Google Maps).
    - Librairie/API de paiements et gestions d'abonnement (Stripe).
    - Sockets pour envoyer/recevoir les messages en temps réel (Socket.io).
- **Accessibilité :** Impossible à naviguer au clavier !
- **Charte Grahique :** Rouge et blanc, avec des cards. Ressemble à un site de rencontre.

### Entraide Scolaire Amicale (E.S.A)

L'E.S.A est une association qui propose un accompagnement aux élèves en difficulté scolaire grâce à des bénévoles.

- **Fonctionnalites cles :**
    - Formulaires d'inscription selon le rôle (famille, benevole, partenaire).
    - Outils de gestion d'affectation (répartition géographique et par niveau).
    - Espace de ressources pédagogiques pour les bénévoles avec des guides d'accompagnement et des fiches d'exercices.
- **Implications techniques :**
    - Site web.
    - Base de données relationnelle pour les profils.
    - Stockage de fichiers pour les pièces justificatives et potentiellement des vidéos pour les cours.
    - Librairie/API pour calculer les distances (vol d'oiseau ou intinéraire) entre les élèves et les bénévoles (geolib, adresse.data.gouv.fr).

- **Accessibilité :** Presque naviguable au clavier
- **Charte Grahique :** Bleu foncé et blanc. Ressemble à un site du gouvernement.

### Kartable

Kartable propose une plateforme payante de soutien scolaire structuré sur le programme de l'Education Nationale francaise.

- **Fonctionnalités clés :**
    - Organisation du contenu par niveau scolaire, matière, chapitres (cours, questions, quiz, exercices, fiches).
    - Correction et évaluation des quiz avec explications.
    - Application mobile hors-ligne pour la consultation des cours.
- **Implications techniques :**
    - Site web + App mobile avec cache.
    - Base de données relationnelle indexée pour la structure en arborescence du contenu et la recherche par mots clés.
    - Librairie/API de paiements et gestions d'abonnement (Stripe).
- **Accessibilité :** Peu navigable au clavier, permet l'utilisation d'**openDyslexic**
- **Charte Grahique :** Bleu et blanc, avec beaucoup de dégradés.

### Acadomia

Acadomia propose des cours particuliers et des cours collectifs, en présentiel mais aussi via une plateforme en ligne.

- **Fonctionnalités clés :**
    - Classe virtuelle en visio avec tableau interactif collaboratif et partage de documents.
    - Planification de rendez-vous avec rappels automatiques (e-mail et SMS).
- **Implications techniques :**
    - APIs de visioconference (Zoom API, Twilio Video ou Lessonspace).
    - Sockets pour le tableau interractif (Socket.io).
    - Librairies pour l'envoi d'emails (Nodemailer) et SMS (Twilio).
    - API de gestion de calendrier / prise de rendez-vous en headless (cal.com) ou intégré (Calendly).
- **Accessibilité :** Très navigable au clavier.
- **Charte Grahique :** Bleu et blanc.

### My Mooc

My Mooc est un annuaire et comparateur de formations en ligne (MOOC) qui agrège les cours de différentes plateformes pour guider les utilisateurs dans leur choix d'apprentissage.

- **Fonctionnalités clés :**
    - Moteur de recherche de cours en ligne avec filtres avancés (langue, thématique, gratuité, certification).
    - Système d'avis, de notation et de commentaires des utilisateurs pour évaluer la qualité des cours.
    - Espace personnel de suivi d'apprentissage pour organiser ses formations sélectionnées.
- **Implications techniques :**
    - Site web.
    - Base de données relationnelle indexée pour la recherche et l'arborescence des catégories, ou moteur de recherche.
    - APIs et connecteurs de synchronisation automatique pour importer les catalogues de cours de plateformes externes (Coursera, edX, FUN-MOOC).
- **Accessibilité :** Très navigable au clavier.
- **Charte Grahique :** Bleu et blanc, beaucoup d'icônes, cards, images (souvent rondes).

## 2. Tendances d'Interface (UI) et Design du Marche

- Généralement un thème clair, souvent avec du bleu.
- Peu navigables au clavier.
- Grande utilisation de cards, parfois des icônes.

## 3. Diapos

### Diapo 1 : Les Acteurs

Dans le secteur des cours en ligne et cours particuliers, nous pouvons trouver ces 5 acteurs :

- **Superprof**, une plateforme commerciale de mise en relation directe entre élèves et enseignants.
- **Entraide Scolaire Amicale (E.S.A)**, une association qui propose un accompagnement aux élèves en difficulté scolaire grâce à des bénévoles.
- **Kartable**, une plateforme payante de soutien scolaire structuré sur le programme de l'Education Nationale francaise.
- **Acadomia**, des cours particuliers et des cours collectifs, en présentiel mais aussi via une plateforme en ligne.
- **My Mooc**, un annuaire et comparateur de formations en ligne qui recense les cours de différentes plateformes pour guider les utilisateurs dans leur choix d'apprentissage.

### Diapo 2 : Fonctionalités Clés

### Diapo 3 : Implications Techniques

### Diapo 4 : Accessibilité

### Diapo 5 : Charte Graphique
