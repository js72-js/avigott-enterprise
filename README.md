# YATHAN, le Memory qui fait apprendre

Application Android (Capacitor) qui embarque le jeu. Tout fonctionne hors ligne : polices, sons et contenus sont inclus.

- Le jeu lui-même : `www/index.html`
- Projet Android : `android/`
- Identifiant de l'app : `com.yathan.memoire`, Android 6.0 minimum

## Obtenir l'APK sans rien installer (GitHub Actions)

1. Crée un dépôt GitHub et pousse ce dossier sur la branche `main`.
2. L'onglet **Actions** lance automatiquement « Construire l'APK YATHAN » (environ 5 min).
3. Ouvre l'exécution terminée, puis télécharge **yathan-apk** en bas de la page.
4. Décompresse le zip : il contient `yathan.apk`.

On peut aussi relancer la construction à la main avec le bouton **Run workflow**.

## Construire sur ton PC (Android Studio)

```bash
npm install
npx cap sync android
npx cap open android   # ouvre Android Studio
```

Dans Android Studio : Build > Build App Bundle(s) / APK(s) > Build APK(s).
Ou en ligne de commande : `cd android && ./gradlew assembleDebug`
L'APK se trouve dans `android/app/build/outputs/apk/debug/app-debug.apk`.

## Installer sur le téléphone

1. Copie `yathan.apk` sur le téléphone (câble, e-mail, Drive…).
2. Touche le fichier. Android demande d'autoriser l'installation depuis cette source : accepte.
3. YATHAN apparaît avec les autres applications.

## Modifier le jeu

Édite `www/index.html`, puis pousse sur GitHub (nouvelle APK automatique) ou lance `npx cap sync android` avant de reconstruire.
Pense à augmenter `versionCode` et `versionName` dans `android/app/build.gradle` pour qu'une nouvelle version s'installe par-dessus l'ancienne.

## Publier sur le Play Store

Le Play Store demande un fichier `.aab` signé avec ta propre clé : `./gradlew bundleRelease` après avoir configuré la signature (Android Studio : Build > Generate Signed App Bundle).
