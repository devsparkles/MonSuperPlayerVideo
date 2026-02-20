# 🎬 MonSuperPlayerVideo - Roadmap

> L'objectif de ce projet est de créer une plateforme vidéo modulaire, comparable à un "WordPress de la vidéo". Elle doit permettre à une organisation de déployer, gérer et diffuser facilement son propre contenu vidéo.
> 
---

## Acteurs

- **Client (Consommateur)**:
  - Regarde du contenu (Live, VOD).
  - Interagit avec des plugins (overlays) affichés par-dessus la vidéo.

- **Créateur**:
  - Publie et gère le contenu.

---

## Approche Technique : Compose Multiplatform

Ce projet est construit sur **Compose Multiplatform** pour maximiser le partage de code entre les plateformes cibles.

- **Interface Utilisateur (UI)**: L'ensemble des contrôles (lecture, pause, barre de progression, etc.) et la logique d'affichage sont écrits **une seule fois** dans le code commun (`commonMain`).

- **Composant Lecteur Vidéo**: La lecture vidéo elle-même utilise les lecteurs natifs de chaque plateforme via le mécanisme `expect/actual` de Kotlin Multiplatform pour garantir les meilleures performances.

| Plateforme | Implémentation du lecteur (`actual`) |
|---|---|
| **Android** | `ExoPlayer` (Media3) |
| **iOS/tvOS** | `AVPlayer` (natif) |
| **Web** | Balise HTML5 `<video>` |

Cette approche combine le meilleur des deux mondes : une UI et une logique métier 100% partagées, avec des performances de lecture vidéo natives.
