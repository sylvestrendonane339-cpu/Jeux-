# Turbo Kart Online 3D — prototype de départ

Prototype original de jeu de kart 3D pour Android, avec synchronisation multijoueur WebSocket.
Il ne reprend pas les personnages, voitures, circuits ou ressources propriétaires de Beach Buggy Racing.

## Contenu
- `game/` : projet Godot 4, circuit de démonstration généré par code, kart pilotable, interface et client WebSocket.
- `server/` : serveur Node.js/WebSocket avec salons, positions des joueurs et diffusion des états.
- `PROCHAINES_ETAPES.md` : limites du prototype et feuille de route.

## Prérequis
- Godot 4.x (version stable récente)
- Node.js 20 ou supérieur
- Pour Android : export templates de la même version Godot, Android SDK, OpenJDK 17 et configuration Android dans Godot.

## Lancer le serveur en local
Dans un terminal, ouvrir `server/`, puis :
```bash
npm install
npm start
```
Le serveur écoute sur le port 8080 par défaut. Pour changer le port : `PORT=8080 npm start`.

## Lancer le jeu dans Godot
1. Ouvrir Godot.
2. Importer le dossier `game/` (sélectionner `project.godot`).
3. Lancer le projet avec F6/F5.
4. Dans le champ serveur, utiliser `ws://127.0.0.1:8080` si le jeu tourne sur le même ordinateur que le serveur.
5. Pour un téléphone sur le même Wi-Fi, remplacer `127.0.0.1` par l'adresse IP locale de l'ordinateur serveur.
6. Pour jouer par Internet, déployer le serveur sur une machine publique et utiliser `wss://votre-domaine`.

## Compiler l'APK
1. Dans Godot, installer les export templates correspondant exactement à la version utilisée.
2. Aller dans `Editor > Manage Export Templates` et installer les templates.
3. Configurer Android SDK/JDK dans `Editor Settings > Export > Android`.
4. Aller dans `Project > Export`, ajouter le preset Android, définir le nom du paquet (ex. `com.example.turbokartonline`), puis exporter un APK debug.
5. Pour installer sur le téléphone, transférer l'APK et autoriser temporairement l'installation depuis cette source.
6. Pour une publication, créer une clé de signature et exporter une version release signée.

Les noms exacts des menus peuvent varier selon la version de Godot. Un APK debug n'est pas prêt pour une publication commerciale.

## Réseau et sécurité
Le serveur de ce prototype est un point de départ, pas une infrastructure de production. Il faut ajouter authentification, validation stricte des messages, limitation de fréquence, protections anti-triche, supervision, TLS/WSS et tests de charge avant une sortie publique. Ne pas exposer le port en production sans configuration réseau et pare-feu appropriés.


## Compilation APK via GitHub Actions depuis un téléphone
L'archive contient maintenant `game/export_presets.cfg`. Pour compiler depuis GitHub sans installer Godot sur Android :
1. Créer un dépôt GitHub vide.
2. Ajouter l'archive `TurboKartOnline_Starter.zip` à la racine du dépôt.
3. Créer le fichier `.github/workflows/build-apk.yml` dans GitHub et coller le workflow fourni dans les instructions de compilation.
4. Aller dans l'onglet Actions, lancer le workflow et télécharger l'artefact APK quand il a réussi.
