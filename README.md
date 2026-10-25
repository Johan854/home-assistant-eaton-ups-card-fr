# Eaton UPS Card (FR)

Carte Home Assistant pour onduleur Eaton : état, tension de sortie, charge, autonomie et puissance active, au style verre, optimisée pour iPhone, iPad et kiosque en mode portrait.
Traduction française de [home-assistant-eaton-ups-card](https://github.com/BeGiBue/home-assistant-eaton-ups-card) de BeGiBue.

## Installation via HACS (dépôt personnalisé)

1. HACS → ⋮ (en haut à droite) → **Dépôts personnalisés**.
2. Collez l'URL de ce dépôt, choisissez la catégorie **Tableau de bord** (Dashboard), puis **Ajouter**.
3. Recherchez « Eaton UPS Card (FR) » et cliquez sur **Télécharger**.
4. Rechargez le navigateur (Ctrl+Maj+R).

## Utilisation

```yaml
type: custom:eaton-ups-card
name: Eaton 3S 850
status_entity: sensor.ups_status
status_data_entity: sensor.ups_status_data
voltage_entity: sensor.ups_output_voltage
load_entity: sensor.ups_load
runtime_entity: sensor.ups_battery_runtime
power_entity: sensor.ups_real_power
show_status_data: true
scale: 1
image_mode: background
image: /local/image/onduleur.webp   # facultatif
```

Les entités par défaut sont celles de l'intégration NUT avec Home Assistant en allemand : adaptez-les aux vôtres dans l'éditeur visuel.

## Licence

Voir la licence du projet d'origine (BeGiBue). Ajoutez le fichier `LICENSE` correspondant à votre dépôt.
