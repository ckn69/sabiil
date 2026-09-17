# CLAUDE.md — Projet Sabīl

Contexte pour toute instance de Claude qui travaille sur ce dépôt. À lire avant de coder.

## Interlocuteur
- Nassim, débutant en dev mobile. Explique simplement, ne saute pas d'étapes.
- Réponds **en français**, registre direct et informel.
- **Concis et structuré**. Pas de verbosité, pas de sur-ingénierie.
- **Édits ciblés** plutôt que régénérations complètes.
- **Jamais d'emojis** sauf demande explicite (exception : emojis qui sont des éléments d'UI, ex. arbres du mode focus).

## Ce qu'est Sabīl
App compagnon quotidien pour le musulman. **Mission centrale** : organiser sa journée **autour des prières**, puis compléter avec le reste (apprentissage, discipline). Viser la **rétention** (revenir chaque jour), pas le temps passé.

**Périmètre à garder net** : pratique quotidienne du musulman. Hors périmètre : finance/patrimoine islamique, zakat pro B2B, annuaire. La calculatrice zakat perso reste (simple, ponctuelle).

## Stack
- **App** : React Native (Expo) + TypeScript.
- **Backend/BDD/Auth/Storage** : Supabase (PostgreSQL, RLS, auth email/Google/Apple).
- **Notifs** : Expo Push + notifications locales (prières, hors-ligne).
- **Horaires de prière** : API Mawaqit.
- État : prototype fonctionnel en HTML/CSS/JS autonome (données en mémoire). Migration vers React Native pas encore commencée.

## Fonctionnalités déjà construites (proto)
- **Navigation** (5 onglets) : Accueil · Agenda · Apprendre · Groupes · Assistant. Compte accessible via avatar en haut de l'Accueil.
- **Accueil** : prochaine prière, tracker 5 prières (4 états : groupe/seul/manqué/pending), app-drawer de modules, lanceur Forêt de concentration.
- **Agenda** : type Google Calendar. Vues Jour / 3 jours / Semaine / Mois. Drag & drop, prières en piliers. Suggestion d'adoration quand trou libre entre Fajr et ʿIshāʾ+30min.
- **Apprendre** : 2 programmes (Cours religieux / Langue arabe), 3 niveaux chacun, modules, leçons, quiz (seuil 75%), fiches de révision, badges. Widget "débloquer niveau suivant" entre niveau courant et suivant.
- **Flashcards** universelles/personnalisables (créer/éditer paquets), SRS (again/hard/good/easy), types custom/course/quran, paquet ḥifẓ Coran, génération de cartes depuis un cours.
- **Groupes d'étude** (simulés) : chat écrit/vocal, écoute simultanée, objectifs de groupe, agenda de groupe séparé, blocs ajoutables à l'agenda perso, multi-groupes.
- **Modules** : Mushaf (lecteur Coran + validation de page → stats/ḥasanāt), Ressources (bibliothèque + moutoun + récitateur IA simulé), Adhkār (compteur tactile + mode Apprendre), Notes (unifiées perso + notes de cours, style Apple, assistant insertion versets/hadiths/fatwa), Objectifs (to-do daily/weekly/monthly/yearly), Habitudes, Zakat.
- **Habitudes** (façon Habitica) : profil avec Vie (HP), XP, pièces ; difficulté easy/medium/hard ; validation = gains + animation ; côté punitif (fin de journée = perte HP sur habitudes manquées) ; boutique de récompenses ; création d'habitude.
- **Zakat** : choix référence or OU argent (2 niṣāb), bloc niṣāb en avant avec jauge au-dessus/en-dessous du seuil, calcul 2,5%. Onglet Sadaqa.
- **Profil/Niveau** (façon Habitica) : niveau, XP, rang, cosmétiques déblocables (cadres/titres/thème).
- **Mode Focus** (façon Forest) : arbres SVG qui poussent selon le temps de concentration, 5 espèces, 4 modes (prière/lecture/révision/dhikr), abandon = arbre meurt, onglet Ma forêt.
- **Mode Voyage/Dérogations** : toggle (voyage/maladie/règles/intempérie) qui ajuste prières (qaṣr/jamʿ) et objectifs, ton déculpabilisant (rukhṣa).
- **Auth** (simulée UI).

## Design system
- Palette **sobre** : émeraude `#0E7C5A` / foncé `#075E45`, ocre `#C7892D`, tons papier crème. Éviter le vif "IA".
- Titres serif **Fraunces** ; corps **Plus Jakarta Sans**.
- Motif **zellige** discret (étoiles 8 branches) en filigrane sur les heros.
- Icônes SVG soignées (proto ne peut pas embarquer de vraies images bitmap).

## Contraintes connues (proto HTML)
- Impossible dans le proto : vraies images, reconnaissance vocale réelle (récitateur simulé), temps réel des groupes (simulé), forcer le mode concentration OS / bloquer les notifs (nécessite le natif).

## Conventions de travail
- **Vérifier la syntaxe JS avant de livrer.**
- Livraisons petites et focalisées ; dire quoi tester à chaque fois.
- Simulation OK pour l'impossible en HTML pur, mais **le signaler clairement**.
- Quand on dit "go"/"continue", enchaîner les sous-tâches.

## Prochaines pistes
- Migration proto → React Native + Supabase.
- Pont Mushaf ↔ ḥifẓ (lire une page crée une carte de révision).
- Notifications adhkār matin/soir et rappels de prière réels (Mawaqit).
- Backend réel : schéma SQL, RLS, auth, invitations.
