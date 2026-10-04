# easybell Cloud-Telefonanlage

Weiterleitung auf die Dr.wait-Rufnummer (Weg A). Der Assistent wird in der easybell Cloud-Telefonanlage als externes Endgerät angelegt und der Praxisnummer zugeordnet. Zugangsdaten für SIP brauchen Sie dafür nicht, nur die Rufnummer des Telefonassistenten.

## 1. Anmelden

Unter [login.easybell.de](https://login.easybell.de/login) anmelden und zur **Cloud-Telefonanlage** wechseln.

## 2. Externes Endgerät anlegen

Neben **Endgeräte** auf **Hinzufügen** klicken.

| Feld | Wert |
| --- | --- |
| Name | `Dr.wait Assistent` |
| Endgeräteart | Externes Endgerät |
| Rufnummer | Rufnummer des Telefonassistenten |

**Speichern.**

## 3. Endgerät der Praxisnummer zuordnen

Bei der Praxisnummer auf das **Zahnrad** klicken, zu **Endgeräte** scrollen, Zahnrad neben **Zugeordnete Endgeräte** und `Dr.wait Assistent` von **Verfügbare Endgeräte** nach **Zugeordnete Endgeräte** ziehen. **Speichern.**

Ab jetzt klingelt der Assistent bei Anrufen an die Praxisnummer mit. Richten Sie das am besten außerhalb der Sprechzeiten ein.

## 4. Anrufbeantworter und Rufweiterleitungen prüfen

In den Einstellungen der Praxisnummer unter **Eingehende Telefonie** auf das Zahnrad neben **Anrufbeantworter/Rufweiterleitungen** klicken. Ist eine erweiterte Rufweiterleitung aktiv, auf **Einfache Ansicht** wechseln, **Keine Aktion** wählen und speichern. Ein aktiver Anrufbeantworter nimmt Anrufe sonst an, bevor der Assistent sie erreicht.

## 5. Rufnummer des Anrufers weitergeben

Unter **Anrufbehandlung** die Option **Anruferkennung bei Weiterleitung** auf **Weiterleitung der Quellrufnummer** stellen und speichern. Dann sieht der Assistent die Nummer des Patienten und nicht die Praxisnummer. Siehe auch die [easybell-Hilfe zur Anruferkennung](https://www.easybell.de/hilfe/cloud-telefonanlage/antwort/anruferkennung-bei-weiterleitung-einstellen/).

## Ein- und ausschalten

Das Endgerät `Dr.wait Assistent` zurück zu **Verfügbare Endgeräte** ziehen und eine vorherige Rufweiterleitung wieder aktivieren.

## Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen.
