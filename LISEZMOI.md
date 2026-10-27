# Appli UE Danse · Dauphine

## Contenu

- `public/index.html` : l'appli (espace étudiantes + espace enseignantes)
- `public/firebase-config.js` : la configuration de ton projet Firebase (à remplir)
- `firestore.rules` : les règles de sécurité (notes invisibles aux étudiantes, choix non modifiables)
- `firebase.json` : configuration de mise en ligne

## Mise en ligne (une seule fois, environ 20 minutes)

1. **Créer le projet** sur https://console.firebase.google.com (ou réutiliser un projet existant).
2. **Ajouter une application Web** (icône `</>`) et copier la config dans `public/firebase-config.js`.
3. **Firestore Database** > Créer une base > mode production, région `europe-west`.
4. **Authentication** > Méthode de connexion, activer :
   - **Google** (pour vous deux, enseignantes) ;
   - **E-mail/Mot de passe**, puis cocher **« Lien envoyé par e-mail (connexion sans mot de passe) »** (pour les étudiantes).
5. **Authentication** > Paramètres > Domaines autorisés : vérifier que `TONPROJET.web.app` est bien listé.
6. Dans un terminal, depuis le dossier `danse-app` :
   ```
   npm install -g firebase-tools
   firebase login
   firebase use --add        (choisir ton projet)
   firebase deploy
   ```
   L'adresse de l'appli s'affiche à la fin : `https://TONPROJET.web.app`.

## Premier lancement (espace prof)

1. Ouvrir l'appli, « Se connecter avec Google » avec mzubaloff@gmail.com ou florianeude@gmail.com.
2. Onglet **Réglages** > « Créer les sujets manquants » (les 25 sujets) et choisir le nombre de places par sujet.
3. Onglet **Étudiantes** : ajouter chaque étudiante (prénom, nom, mail Dauphine, jour de danse).
4. Quand tout est prêt : **Réglages** > cocher « Choix ouverts » et envoyer le lien de l'appli aux étudiantes.

## Notation

5 cases par item, du rouge (non acquis) au vert foncé (acquis) : 0 · 1,25 · 2,5 · 3,75 · 5.
La note de chaque partie (/5) est la moyenne des items cochés, arrondie au demi-point.
La note sur 20 est la somme des 4 parties. Un item laissé vide n'est pas compté.
Recliquer sur une case l'efface.

## Ajouter une enseignante

Modifier la liste `ADMINS` dans `public/index.html` **et** la fonction `isAdmin()` dans `firestore.rules`, puis `firebase deploy`.
