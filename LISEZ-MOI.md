# Compagnon de voyage — compiler l'app Android depuis votre tablette

Tout se passe dans le navigateur. GitHub compile l'APK à votre place sur ses
propres serveurs — vous n'installez rien, vous ne touchez à aucun terminal.

## Étape 1 — Créer un compte GitHub (si vous n'en avez pas)

Allez sur [github.com](https://github.com) et créez un compte gratuit. Deux
minutes, juste un email.

## Étape 2 — Créer un nouveau dépôt

1. En haut à droite, cliquez sur **+** puis **New repository**.
2. Donnez-lui un nom, par exemple `compagnon-voyage`.
3. Laissez-le en **Public** (le plus simple pour la version gratuite d'Actions —
   les dépôts privés ont aussi droit à des minutes gratuites, mais Public est
   sans limite).
4. Cliquez sur **Create repository**.

## Étape 3 — Envoyer les fichiers de ce dossier, sans terminal

Sur la page de votre nouveau dépôt vide, GitHub propose un lien
**"uploading an existing file"** — cliquez dessus. Vous arrivez sur une zone où
vous pouvez **glisser-déposer** des fichiers directement depuis votre tablette.

Faites-le en deux fois, parce que ce dossier contient des sous-dossiers cachés
(`.github`) que le glisser-déposer simple ne gère pas toujours bien d'un coup :

**D'abord**, glissez ces fichiers à la racine :
- `package.json`
- `capacitor.config.json`
- `icon-192.png`
- `icon-512.png`
- `LISEZ-MOI.md`

**Ensuite**, ouvrez le dossier `www` sur votre tablette, et dans la zone
d'upload de GitHub, tapez `www/index.html` comme nom de chemin quand elle vous
le demande (ou utilisez l'option "Add file" → "Upload files" à nouveau une fois
dans le bon dossier — l'interface GitHub vous laisse naviguer/créer des
dossiers directement en tapant le chemin dans le nom du fichier au moment de
l'upload, ex : `www/index.html`).

**Enfin**, faites pareil pour le fichier de configuration du robot de
compilation : `.github/workflows/build-android.yml` (tapez bien ce chemin
complet avec les slashs quand vous nommez le fichier dans la zone d'upload —
GitHub crée les dossiers automatiquement).

En bas de la page, cliquez sur **Commit changes** à chaque envoi.

## Étape 4 — Laisser GitHub compiler

Dès que le fichier `.github/workflows/build-android.yml` est envoyé, GitHub
lance automatiquement la compilation. Pour suivre ça :

1. Allez dans l'onglet **Actions** en haut de votre dépôt.
2. Vous verrez une exécution en cours ("Build Android APK") — cliquez dessus.
3. Ça prend entre 3 et 8 minutes. Une coche verte ✅ apparaît quand c'est fini.

Si jamais rien ne s'est lancé automatiquement, ou pour relancer une compilation
plus tard : dans l'onglet **Actions**, cliquez sur **Build Android APK** dans
la liste à gauche, puis sur le bouton **Run workflow** à droite.

## Étape 5 — Télécharger l'APK

Une fois la coche verte affichée, cliquez sur cette exécution, puis descendez
jusqu'à la section **Artifacts** en bas de page : vous y trouverez
`compagnon-voyage-debug-apk` — cliquez pour le télécharger (ça arrive en `.zip`,
qui contient l'APK à l'intérieur).

## Étape 6 — Installer sur votre téléphone

1. Téléchargez ce `.zip` sur votre téléphone Android (pas la tablette — sauf
   si vous testez directement sur une tablette Android, ça marche aussi).
2. Décompressez-le pour récupérer `app-debug.apk`.
3. Ouvrez ce fichier. Android va probablement demander d'autoriser
   l'installation depuis cette source ("Autoriser depuis cette source" /
   "Installer des apps inconnues") — c'est normal pour un APK qui ne vient pas
   du Play Store, acceptez.
4. L'app s'installe et apparaît sur votre écran d'accueil, comme n'importe
   quelle app.

C'est un APK de test ("debug") — parfait pour vérifier que tout fonctionne,
tester les notifications natives, etc. Pas besoin de compte développeur payant
pour ça. Le compte Google Play (25 $) ne sera nécessaire que le jour où vous
voudrez le publier officiellement sur le store.

## Pour les mises à jour suivantes

Si je vous redonne un nouveau `www/index.html` plus tard, remplacez juste ce
fichier sur GitHub (ouvrez-le dans le dépôt, crayon "Edit", collez le nouveau
contenu, ou re-uploadez par-dessus) — la compilation se relance automatiquement,
et vous retéléchargez un nouvel APK dans Actions.

## Et pour iOS ?

C'est possible aussi via un service cloud équivalent (Codemagic), mais Apple
exige un compte développeur payant (99 $/an) même pour cette voie — c'est une
vraie exigence d'Apple, aucun moyen de la contourner, cloud ou pas. Dites-le moi
si vous voulez qu'on mette ça en place aussi, une fois que vous aurez ce compte.
