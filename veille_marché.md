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

### Diapo 2 : Fonctionnalités Clés

- **Mise en relation et profils utilisateurs**
    - Moteur de recherche multicritère (matières, tarifs, avis, proximité géographique).
    - Formulaires d'inscription différenciés selon le rôle (bénévoles, familles, partenaires).
    - Validation et certification des profils de tuteurs (diplômes, réactivité).

- **Contenus éducatifs et apprentissage**
    - Cours structurés et conformes aux programmes officiels (leçons, quiz, exercices résolus) chez Kartable.
    - Classe virtuelle synchrone (visioconférence intégrée, tableau interactif, partage d'écran) chez Acadomia.
    - Annuaire complet avec système d'avis, de notation et d'agrégation thématique de MOOCs chez My Mooc.

- **Mise en relation et communication**
    - Messagerie interne sécurisée et gestion intégrée de la prise de rendez-vous.
    - Algorithmes d'affectation basés sur la géolocalisation et les niveaux scolaires chez l'E.S.A.
    - Tableaux de bord de suivi de progression et statistiques d'apprentissage chez Kartable et Acadomia.

### Diapo 3 : Implications Techniques

- **Bases de données et indexation de gros volumes**
    - Stockage de fichiers (Documents, images, vidéos).
    - Relationnelle et indéxée pour une recherche/mise en relation basée sur la position géographique, le niveau, la matière...

- **APIs et intégrations de services tiers**
    - **Paiements en ligne sécurisés :** Solutions comme Stripe pour la facturation à l'abonnement ou à l'usage (Superprof, Kartable).
    - **Visioconférence et communication :** Intégration d'outils temps réel (WebRTC, Zoom API, Twilio) pour les classes virtuelles d'Acadomia.
    - **Cartographie et calcul de distance :** APIs de géolocalisation (Google Maps API, adresse.data.gouv.fr) pour la mise en relation de proximité (Superprof, E.S.A).

- **Outils en ligne et hors ligne**
    - Site web pour un accès en ligne simple.
    - Application mobile (Kartable) avec mise en cache pour accessibilié hors ligne.

### Diapo 4 : Accessibilité

    - Malheureusement la navigation au clavier et le lecteur d'écran sont peu intégrés sur la plupart de ces sites.
    - L'acessibilité pourrait être un point fort de Learn@Home pour se démarquer.
    - On notera que Kartable intègre l'outil OpenDyslexic pour les personnes dyslexiques.

### Diapo 5 : Charte Graphique

- **Identités visuelles et choix colorimétriques**
    - **La prédominance du bleu et du blanc :** Couleur majoritaire chez E.S.A, Kartable, Acadomia et My Mooc. Le bleu inspire la confiance, le sérieux, le calme et s'associe naturellement à l'univers éducatif.
    - **L'exception Superprof :** Utilisation intensive du rouge et du blanc avec une interface ressemblant presque à un site de rencontre.

- **Composants d'interface (UI) récurrents**
    - **Thème clair omniprésent :** L'ensemble des acteurs privilégie des fonds clairs (blancs ou gris très clairs) pour optimiser la lisibilité du texte.
    - **Format "Card" (cartes) :** Usage massif pour présenter les fiches de tuteurs (Superprof), les modules de cours (Kartable) ou les formations proposées (My Mooc).
    - **Visuels engageants :** Photos chaleureuses d'élèves ou de professeurs, avatars ronds et icônes épurées pour rendre l'interface rassurante, accessible et moderne.
