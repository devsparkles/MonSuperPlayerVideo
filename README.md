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

## Approche Technique

- **Compose Multiplatform**: L'UI et la logique métier sont partagées entre Android, iOS et le Web.
- **Lecteurs Natifs**: Utilisation de `ExoPlayer` (Android), `AVPlayer` (iOS) et `<video>` (Web) via `expect/actual` pour des performances optimales.
- **Layout Dynamique**: L'interface du lecteur n'est pas codée en dur. Elle est générée dynamiquement à partir d'une structure JSON fournie par un backend.

---

## Roadmap

### Phase 1 : Moteur de Layout Dynamique (Priorité #1)

L'objectif est de créer un système où l'interface du lecteur est définie par une configuration JSON. Le code Compose Multiplatform lira cette configuration et dessinera l'interface correspondante.

- [ ] **Définir le schéma JSON du layout** : Structurer les composants, leurs propriétés (position, taille, icône, action) et leur hiérarchie.
  ```json
  {
    "layout": {
      "type": "Box", // ou Column, Row
      "children": [
        {
          "type": "Button",
          "id": "play_pause_button",
          "icon": "play_arrow",
          "action": "toggle_playback",
          "alignment": "Center"
        }
      ]
    }
  }
  ```

- [ ] **Parser JSON** : Créer les modèles de données (data classes) et la logique de parsing dans `commonMain`.

- [ ] **Moteur de rendu Compose** : Créer les composants (`Button`, `Slider`, `Box`, etc.) qui sont capables de se dessiner à partir des objets parsés du JSON.

- [ ] **Implémenter un premier layout de base** : Afficher un simple bouton Play/Pause à partir d'un JSON local pour valider l'architecture.

### Phase 2 : Lecteur Vidéo Core

- [ ] **Intégrer le lecteur vidéo `expect/actual`** : Brancher `ExoPlayer`, `AVPlayer` et la balise `<video>`.
- [ ] **Lecture de base** : HLS, DASH.
- [ ] **Connecter les actions** : Lier l'action `toggle_playback` du JSON au `player.play()` ou `player.pause()`.
- [ ] **Gestion des états** : Buffering, erreurs.

### Phase 3 : Publicité & Analytics

- [ ] **Interface de publicité** : `AdLoader`.
- [ ] **Intégration IMA**.
- [ ] **Bus d'événements d'analytics**.
