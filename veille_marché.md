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

---

## 2. Tendances d'Interface (UI) et Design du Marche

L'analyse de ces acteurs revele plusieurs tendances majeures pour les applications dediees a l'education et a la mise en relation.

### Structure des pages

- **Layouts epures et compartimentes :** Les interfaces reduisent au maximum la surcharge cognitive. Les elements sont divises en cartes distinctes (cards layout), facilitant la lecture rapide par les enfants et les parents.
- **Parcours d'inscription progressifs :** Des tunnels d'inscription structures sous forme d'etapes sequentielles plutot que de grands formulaires d'un seul bloc.
- **Tableaux de bord bi-profils :** Une separation claire de l'interface utilisateur selon le role connecte (Tableau de bord Eleve oriente motivation / progression ; Tableau de bord Tuteur oriente calendrier / suivi).

### Accessibilite (A11y)

- **Rapports de contraste eleves :** Utilisation stricte de polices bien lisibles et de contrastes eleves conformes aux normes WCAG AA minimum.
- **Support dys- / neurodivergence :** integration de polices d'ecriture specifiques aux personnes dyslexiques (comme OpenDyslexic) et de filtres d'affichage de texte adaptes.
- **Prise en charge clavier et vocale :** Possibilite de naviguer entierement au clavier et compatibilite optimale avec les lecteurs d'ecran standard pour l'accessibilite visuelle.

### Couleurs et chartes graphiques

- **Le bleu et le vert comme couleurs socles :** Utilises par une majorite d'acteurs (E.S.A, Superprof, Acadomia) pour etablir un sentiment de confiance, de professionnalisme, d'ordre et de calme.
- **Touches de couleurs stimulantes :** Jaune chaleureux, orange ou violet (Khan Academy, Kartable) par petites touches pour stimuler l'attention, souligner une reussite ou attirer l'attention sur un appel a l'action important.
- **Fonds majoritairement blancs ou gris clair :** Des fonds epures qui permettent d'eviter la fatigue visuelle lors des sessions de travail prolongees.

### Elements graphiques et iconographie

- **Illustrations bienveillantes :** Utilisation massive de visuels vectoriels, de mascottes souriantes et de portraits d'humains representant la diversite et l'entraide sociale.
- **Gamification visuelle :** Presence de jauges de progression coloriees, de pastilles de reussite et de badges interactifs pour rendre l'accomplissement des taches ludique.
- **Icones universelles :** Des icones claires, associees systematiquement a des labels textuels explicites pour eviter toute confusion.

---

## 3. Contenu du Diaporama (Slides de Veille de Marche)

Voici le contenu structure pour une presentation de 5 diapositives synthetisant cette veille strategique pour l'association Learn@Home.

---

### Slide 1 : Titre & Contexte du Projet

- **Titre :** Veille Strategique & Opportunites d'Architecture - Projet Learn@Home
- **Sous-titre :** Analyse de marche pour un service de tutorat benevole en ligne moderne
- **Contenu :**
    - **Le Defi de Learn@Home :** Associer l'accessibilite totale pour les eleves en difficulte a la simplicite d'engagement pour les tuteurs benevoles.
    - **Objectif de la presentation :** Tirer le meilleur parti des leaders du marche et des tendances techniques / UI actuelles pour concevoir une plateforme robuste, inclusive et performante.

---

### Slide 2 : Cartographie du Marche - Les 5 Acteurs Cles

- **Titre :** Un ecosysteme varie pour inspirer Learn@Home
- **Contenu :**
    - **Les Places de Marche (Superprof) :** Excellentes pour la mise en relation et la pertinence de la recherche multicritere.
    - **L'Auto-apprentissage (Khan Academy) :** Referent de la progression pedagogique autonome et des standards d'accessibilite eleves.
    - **L'Accompagnement Benevole (E.S.A) :** Modele associatif miroir, focalise sur l'engagement solidaire et la gestion rigoureuse des bénévoles.
    - **La Rigueur Pedagogique (Kartable) :** Modele structure par programme scolaire et auto-correction dynamique.
    - **L'Accompagnement Premium (Acadomia) :** Leader du suivi administratif et de la classe virtuelle collaborative integree.

---

### Slide 3 : Analyse Technique - Ce que nous devons implementer

- **Titre :** Defis techniques de la plateforme Learn@Home
- **Contenu :**
    - **Frontend :** Framework moderne (React ou Vue.js) privilegiant la modularite et l'accessibilite numerique complete.
    - **Backend & Recherche :** Service robuste de mise en relation et algorithme de correspondance tuteur-eleve (matchmaking) base sur la geolocalisation, le niveau d'etudes et la disponibilite.
    - **Securite des donnees :** Chiffrement des pieces jointes d'inscription (ex: casiers judiciaires des benevoles) et gestion stricte des acces via des roles dedies (Eleve, Tuteur, Coordinateur).
    - **Integrations :** Utilisation d'un protocole WebRTC ou d'une API tierce pour integrer un espace classe virtuelle audio/video et tableau blanc collaboratif legers sans developper une infrastructure lourde.

---

### Slide 4 : Tendances de l'Interface (UI/UX)

- **Titre :** Des choix graphiques clairs, rassurants et inclusifs
- **Contenu :**
    - **Double Interface Dediee :**
        - Espace Eleve simplifie, ludique et stimulant (utilisation de la gamification, jauges de progression).
        - Espace Tuteur sobre, axe sur l'organisation (agenda partage, notes de suivi, bibliotheque de ressources).
    - **Palette de couleurs :** Base de bleu profond (confiance) associe a des accents de jaune chaleureux ou d'orange (action et encouragements).
    - **Charte d'accessibilite :** Support des polices pour dyslexiques, contrastes maximises pour eviter la fatigue oculaire, et layouts adaptatifs au mobile (beaucoup d'eleves se connectent sur smartphone ou tablette).

---

### Slide 5 : Recommandations Claires pour Learn@Home

- **Titre :** Feuille de route fonctionnelle et technique
- **Contenu :**
    - **Phase 1 : Un onboarding simplifie et securise :** Formulaires d'inscription par etapes claires avec module securise d'upload de pieces justificatives pour les benevoles.
    - **Phase 2 : L'algorithme de matching :** Un systeme d'aide a la decision automatique pour les coordinateurs de l'association, triant les tuteurs compatibles selon les besoins et disponibilites de l'eleve.
    - **Phase 3 : La boite a outils pedagogique :** integre un calendrier de rendez-vous avec rappels automatiques et un espace classe virtuelle minimaliste, simple et gratuit (ex: Jitsi Meet integre ou classe virtuelle WebRTC legere).
    - **Phase 4 : Standardisation A11y :** Adopter d'entree de jeu les standards WCAG AA pour affirmer l'aspect solidaire et social de l'association, accessible a tous les handicaps et toutes les connexions reseau.
