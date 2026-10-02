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

### Voraussetzungen – benötigte Helfer

Bevor der Blueprint verwendet wird, sollten in Home Assistant folgende drei Helfer angelegt werden:

1. **Astro Rollladen**
   - Typ: **Umschalter**
   - Entität: `input_boolean.astro_rollladen`
   - Dieser Helfer steuert den Tag-/Nachtzustand für die Rollladenautomatik.

2. **Beschattung**
   - Typ: **Umschalter**
   - Entität: `input_boolean.beschattung`
   - Dieser Helfer aktiviert bzw. deaktiviert die automatische Beschattungsfunktion.

3. **Ruhe Rollladen**
   - Typ: **Umschalter**
   - Entität: `input_boolean.ruhe_rollladen`
   - Dieser Helfer aktiviert den Ruhemodus und verhindert das automatische Öffnen des Rollladens am Morgen.

Die Helfer können in Home Assistant unter:

**Einstellungen → Geräte & Dienste → Helfer → Helfer erstellen → Umschalter**

angelegt werden.

Anschließend kann der Blueprint importiert und die entsprechenden Helfer bei der Konfiguration ausgewählt werden.

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

### 🌅 Automatische Astro-Steuerung über die Sun-Integration

Damit der Helfer **„Astro Rollladen“** nicht manuell geschaltet werden muss, gibt es zusätzlich eine passende Automation.

Diese Automation verwendet die in Home Assistant integrierte **Sun-Integration** und schaltet den Helfer `input_boolean.astro_rollladen` automatisch abhängig von Sonnenaufgang und Sonnenuntergang.

Dadurch erhält der eigentliche Rollladen-Blueprint automatisch die Information, ob sich die Rollladensteuerung im **Tag- oder Nachtmodus** befindet.

#### Funktionsweise

- 🌅 Bei Sonnenaufgang wird **Astro Rollladen** entsprechend auf Tagbetrieb geschaltet.
- 🌇 Bei Sonnenuntergang wird **Astro Rollladen** entsprechend auf Nachtbetrieb geschaltet.
- 🔄 Die Umschaltung erfolgt automatisch über die Home-Assistant-Sun-Integration.
- 🏠 Es ist keine zusätzliche Wetter- oder Cloud-Integration erforderlich.

Die dazugehörige Automation befindet sich hier:

[`automationen/blueprints/astro_rollladen.yaml`](https://github.com/ossilampe/Home-Automatisierung/blob/master/blueprints/astro_rollladen.yaml)

Diese Automation sollte zusätzlich zum Rollladen-Blueprint in Home Assistant eingerichtet werden, wenn der Helfer **Astro Rollladen** automatisch gesteuert werden soll.

> **Hinweis:** Der Blueprint selbst funktioniert mit dem Helfer `input_boolean.astro_rollladen`. Ob dieser Helfer manuell oder über die zusätzliche Astro-Automation geschaltet wird, spielt für den Blueprint keine Rolle.
