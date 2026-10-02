# Home-Automatisierung

Hier stelle ich meine selbst erstellten Home-Assistant-Blueprints zur Verfügung.

## 🪟 Rollladensteuerung – Astro, Fenster, Ruhemodus und Beschattung

Blueprint zur automatischen Steuerung eines Rollladens in Home Assistant.

### Funktionen

- 🌙 Automatisches Schließen über den Astro-Modus
- ☀️ Automatisches Öffnen am Morgen
- 🪟 Berücksichtigung eines Fensterkontakts
- 🔇 Optionaler Ruhemodus
- 🌤️ Beschattungsfunktion mit einstellbarer Position
- ⏰ Einstellbare Verzögerung morgens und abends
- ⏱️ Späteste Öffnungszeit als Zwangsöffnung
- 🪟 Bei geöffnetem Fenster wird nachts nur bis zur eingestellten Fensterposition gefahren
- 🌙 Beim Schließen des Fensters während der Nacht wird der Rollladen vollständig geschlossen
- 🔇 Wird der Ruhemodus tagsüber beendet, öffnet der Rollladen anschließend automatisch bzw. fährt in die Beschattungsposition

## Installation

Der Blueprint kann direkt in Home Assistant importiert werden:

[![Open your Home Assistant instance and show the blueprint import dialog.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fossilampe%2FHome-Automatisierung%2Fblob%2Fmaster%2Fblueprints%2Ffensterautomation.yaml)

Alternativ kann der Blueprint hier aufgerufen werden:

https://github.com/ossilampe/Home-Automatisierung/blob/master/blueprints/fensterautomation.yaml

## Hinweis

Für die Verwendung müssen die benötigten Entitäten in Home Assistant vorhanden sein. Dazu gehören je nach Konfiguration unter anderem:

- Rollladen / Cover
- Fensterkontakt
- Astro-Modus
- Beschattungsmodus
- optional ein Ruhemodus
