# Eaton UPS Card (FR)

Carte Home Assistant pour onduleur Eaton : état, tension de sortie, charge, autonomie, puissance active, **charge de la batterie**, seuils de transfert, signal sonore et fréquence nominale. Style verre avec nuance de couleur au choix, optimisée pour iPhone, iPad et kiosque en mode portrait. Elle suit automatiquement le thème clair/sombre de Home Assistant. Traduction française de [home-assistant-eaton-ups-card](https://github.com/BeGiBue/home-assistant-eaton-ups-card) de BeGiBue.

## Installation via HACS (dépôt personnalisé)

1. HACS → ⋮ (en haut à droite) → **Dépôts personnalisés**.
2. Collez l'URL de ce dépôt, choisissez la catégorie **Tableau de bord** (Dashboard), puis **Ajouter**.
3. Recherchez « Eaton UPS Card (FR) » et cliquez sur **Télécharger**.
4. Rechargez le navigateur (Ctrl+Maj+R).

## Utilisation

```yaml
type: custom:eaton-ups-card
name: Eaton 3S 850
status_entity: sensor.myups_etat
status_data_entity: sensor.myups_code_d_etat
voltage_entity: sensor.myups_tension_de_sortie
load_entity: sensor.myups_charge
runtime_entity: sensor.myups_autonomie_de_la_batterie
power_entity: sensor.myups_puissance_reelle
# Facultatif (masqué si l'entité n'existe pas)
battery_entity: sensor.myups_charge_de_la_batterie
nominal_power_entity: sensor.myups_puissance_nominale
low_battery_entity: sensor.myups_consigne_de_batterie_faible
transfer_low_entity: sensor.myups_transfert_tension_basse
transfer_high_entity: sensor.myups_transfert_tension_haute
beeper_entity: sensor.myups_etat_du_signal_sonore
frequency_entity: sensor.myups_frequence_de_sortie_nominale
show_status_data: true
scale: 1
image_mode: background
image: /local/image/onduleur.webp   # facultatif
```

Les entités par défaut sont celles de l'intégration NUT de Home Assistant en français, pour un onduleur nommé `myups` : adaptez-les aux vôtres dans l'éditeur visuel.

## Apparence : thème et nuance de couleur

Dans l'éditeur visuel, section **Apparence** :

| Option | Valeurs |
|---|---|
| `theme` | `auto` (suit Home Assistant), `light`, `dark` |
| `nuance` | `theme` (par défaut), `braise`, `ocean`, `lagon`, `foret`, `lavande`, `framboise`, `ambre`, `ardoise`, `perso` |
| `nuance_perso` | Couleur au choix (sélecteur de couleur), utilisée avec `nuance: perso` |
| `intensite` | De `0` (neutre) à `2` (très coloré), `1` par défaut |

La nuance teinte le dégradé de fond et la couleur principale des tuiles ; les couleurs d'alerte (vert, orange, rouge) restent identiques.

**Une seule nuance pour toutes tes cartes** : laisse `nuance: theme` et ajoute cette ligne à ton thème Home Assistant (sans thème, c'est la nuance braise) :

```yaml
carte-nuance: "#2f8fd8"
```

## Entités facultatives

| Option | Ce qu'elle ajoute |
|---|---|
| `battery_entity` | Tuile pleine largeur « Charge de la batterie » avec barre, icône selon le niveau et « en charge ». Passe en orange puis en rouge à l'approche du seuil de batterie faible (15 % par défaut). |
| `low_battery_entity` | Repère du seuil de batterie faible sur la barre de batterie, et seuil utilisé pour les couleurs. |
| `nominal_power_entity` | Sous la puissance active : « sur 850 W » et une barre de la puissance par rapport à la capacité de l'onduleur. |
| `transfer_low_entity` / `transfer_high_entity` | Sous la tension de sortie : « Transfert : 184 – 253 V ». La tuile passe en orange si la tension sort de cette plage. |
| `beeper_entity` | Bouton rond à côté de l'état : haut-parleur actif, ou barré en orange si le signal sonore est coupé. |
| `frequency_entity` | Ligne discrète en bas de carte : « Fréquence nominale 50 Hz ». |

Un appui sur n'importe quelle tuile ou icône ouvre la fiche de l'entité.

## Historique des versions

- **2.2.0** : style verre propre à la carte (fond dégradé, tuiles en verre), thème clair/sombre automatique ou forcé, nuance de couleur au choix (8 nuances, couleur personnalisée, intensité, ou nuance commune via le thème).
- **2.1.0** : charge de la batterie, puissance nominale, seuil de batterie faible, seuils de transfert, signal sonore et fréquence nominale ; entités par défaut en français ; `validate.yml` déplacé dans `.github/workflows/` pour que la validation HACS fonctionne.
- **2.0.0** : version initiale.

## Licence

Voir la licence du projet d'origine (BeGiBue). Ajoutez le fichier `LICENSE` correspondant à votre dépôt.
