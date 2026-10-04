# STARFACE

Einbindung per SIP (Weg B). Für STARFACE als Appliance, VM oder Cloud. Dr.wait wird als zusätzliche SIP-Provider-Leitung mit eigenem Providerprofil angelegt.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [Leitung für einen SIP-Provider konfigurieren](https://knowledge.starface.de/pages/viewpage.action?pageId=46565948)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. Leitung anlegen

**Admin > Leitungen**, Reiter **Leitungen**, neue Leitung für einen SIP-Provider anlegen. Da Dr.wait kein vordefiniertes Providerprofil hat, ein **eigenes Providerprofil** anlegen.

| Einstellung | Wert |
| --- | --- |
| Registrar / Server / Domain | `drwait.sip.twilio.com` |
| Benutzername / Authentifizierungs-ID | Ihr Dr.wait-Benutzername |
| Kennwort | Ihr Dr.wait-Kennwort |
| Registrierung | aktiv |
| Port / Transport | `5060`, UDP |
| Codecs | G.711 a-law (PCMA), G.711 u-law (PCMU) |

Nach dem Speichern sollte die Leitung den Status **Registered** zeigen.

## 2. Route zur Rufnummer des Telefonassistenten

Anrufe an die **Rufnummer des Telefonassistenten** müssen über den neuen Dr.wait-Zugang gehen, unverändert, ohne Präfix und ohne abgeschnittene Ziffern. Der Anruf kommt dann bei `sip:<Rufnummer>@drwait.sip.twilio.com` an.

## Rufnummer des Anrufers durchreichen

In der Leitung unter **Erweiterte Einstellungen** **CLIP No Screening** aktivieren.

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
