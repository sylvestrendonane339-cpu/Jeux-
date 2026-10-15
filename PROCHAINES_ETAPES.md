# Feuille de route

## Prototype inclus
- Kart local à contrôles clavier et tactiles simples.
- Circuit construit par primitives 3D.
- Client WebSocket qui rejoint un salon et envoie sa position.
- Serveur qui relaie les états aux autres joueurs du même salon.

## À développer avant une vraie sortie
1. Physique de kart plus convaincante : accélération, friction, drift, suspension, collisions.
2. Réplication réseau interpolée et prédiction locale pour réduire la latence.
3. Serveur autoritaire : calcul des mouvements côté serveur, validation des vitesses et collisions.
4. Comptes joueurs, matchmaking, classement, reconnexion et gestion des abandons.
5. Ressources 3D originales optimisées, LOD, éclairage mobile, textures compressées.
6. Tests sur plusieurs téléphones Android et sur réseaux mobiles.
7. Hébergement WSS/TLS, sauvegardes, métriques, limites de débit et protection contre les abus.

## Important
Le serveur inclus diffuse les positions déclarées par les clients : il n'est pas anti-triche et ne doit pas être considéré comme compétitif ou sécurisé. Il sert à valider le chemin de communication multijoueur.
