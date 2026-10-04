# Auerswald COMpact / COMmander

Einbindung per SIP (Weg B). Für Auerswald COMpact 4000/5000/5x00R und COMmander. Dr.wait wird im Konfigurationsmanager als zusätzlicher VoIP-Anbieter mit einem VoIP-Account angelegt.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [VoIP-Anbieter verwalten](https://docs.auerswald.de/COMpact5000/Help_V24_de/Buch1/voip_anbieter_verwaltung_reference.html)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. VoIP-Anbieter anlegen

**Konfigurationsmanager > Öffentliche Netze > VoIP > Anbieter > Neu**. Keine Vorlage eines anderen Anbieters verwenden.

| Einstellung | Wert |
| --- | --- |
| Name | `Dr.wait` |
| Registrar / Domain | `drwait.sip.twilio.com` |
| Art der Rufnummernübermittlung | P-Asserted-Identity (RFC 3325) |
| Codecs | G.711 a-law, G.711 u-law |

## 2. VoIP-Account anlegen

Unter **VoIP-Accounts** einen Account für den Anbieter `Dr.wait` anlegen:

| Einstellung | Wert |
| --- | --- |
| Benutzername | Ihr Dr.wait-Benutzername |
| Kennwort | Ihr Dr.wait-Kennwort |
| Rufnummer | Rufnummer des Telefonassistenten |

## 3. Route zur Rufnummer des Telefonassistenten

Anrufe an die **Rufnummer des Telefonassistenten** müssen über den neuen Dr.wait-Zugang gehen, unverändert, ohne Präfix und ohne abgeschnittene Ziffern. Der Anruf kommt dann bei `sip:<Rufnummer>@drwait.sip.twilio.com` an.

## Rufnummer des Anrufers durchreichen

Im VoIP-Account von Dr.wait **CLIP no screening** aktivieren. Beim Anbieter muss die Art der Rufnummernübermittlung auf P-Asserted-Identity oder P-Preferred-Identity stehen (Schritt 1).

## Anrufe an den Assistenten geben

Tragen Sie die Rufnummer des Telefonassistenten dort als Ziel ein, wo der Assistent übernehmen soll:

- als zusätzliches Mitglied der Gruppe, auf der die Praxisnummer klingelt (parallel),
- als Ziel bei Nichtannahme oder bei besetzt,
- als Taste im Sprachmenü,
- als zeitgesteuertes Ziel außerhalb der Sprechzeiten.

Zum Ausschalten nehmen Sie dieses Ziel wieder heraus.

## Test

1. Von einem internen Telefon die Rufnummer des Telefonassistenten wählen. Der Assistent sollte antworten.
2. Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt.
3. Im Posteingang prüfen, dass die Nummer des Mobiltelefons erscheint. Steht dort die Praxisnummer oder Ihr Benutzername, die Einstellung zur Rufnummer des Anrufers prüfen.

---

Fragen zur Einrichtung: [Dr.wait Support auf WhatsApp](https://wa.me/493012076512) (+49 30 12076512) · [Alle Anlagen](README.md)
