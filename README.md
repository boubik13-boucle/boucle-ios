# Boucle — préparation iPhone

Cette archive contient une copie de travail du projet Boucle. Le moteur musical d'origine est conservé dans `www/index.html` et `www/samples.js`.

## Architecture

- Application hybride : Capacitor + moteur HTML/JavaScript existant.
- Identifiant iOS réservé : `fr.boucle.music` (à vérifier avant publication).
- Les sons restent embarqués dans `www/samples.js` : aucune dépendance à un serveur distant pour les banques audio.
- Les données actuelles utilisent notamment `localStorage`. Elles doivent être testées sur appareil avant toute migration ou mise à jour.

## Préparer le projet iOS (sur un environnement Mac ou CI macOS)

```bash
npm install
npx cap add ios
npx cap sync ios
npx cap open ios
```

La génération et la signature d'une application iOS nécessitent Xcode sur macOS ou un service de compilation macOS dans le cloud. Un iPhone seul ne peut pas exécuter Xcode localement.

## Points à vérifier avant distribution

1. Autorisation microphone iOS (`NSMicrophoneUsageDescription`) avant d'utiliser l'onglet Voix.
2. Import/export de fichiers et accès aux fichiers audio dans WKWebView.
3. Persistance des playlists, mélodies et réglages après fermeture forcée.
4. Lecture audio en arrière-plan, verrouillage de l'écran et interruptions (appels, casque).
5. Tests de performances avec la banque de sons complète.

Ne pas remplacer la version en ligne tant que ces tests ne sont pas validés.
