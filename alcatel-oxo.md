# Alcatel-Lucent OmniPCX Office / OXO Connect

Einbindung per SIP (Weg B). Dr.wait wird mit dem Konfigurationsprogramm OMC als zusätzlicher SIP-Zugang angelegt.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [Beispielkonfiguration SIP-Trunk (PDF, englisch)](https://www.al-enterprise.com/-/media/assets/internet/documents/ch-sunrise-r920-confgui-ed0a.pdf)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. SIP-Zugang anlegen

In OMC:

1. **Voice over IP > VoIP Parameters**: SIP-Grundeinstellungen prüfen.
2. **External Lines > List of Accesses / Trunk Groups**: einen Zugang für Dr.wait anlegen.
3. **Numbering > ARS > Gateway Parameters** bzw. **ARS SIP Accounts**: Gateway `drwait.sip.twilio.com` und das SIP-Konto eintragen.

| Einstellung | Wert |
| --- | --- |
| Registrar / Server / Domain | `drwait.sip.twilio.com` |
| Benutzername / Authentifizierungs-ID | Ihr Dr.wait-Benutzername |
| Kennwort | Ihr Dr.wait-Kennwort |
| Registrierung | aktiv |
| Port / Transport | `5060`, UDP |
| Codecs | G.711 a-law (PCMA), G.711 u-law (PCMU) |

## 2. Route zur Rufnummer des Telefonassistenten

Anrufe an die **Rufnummer des Telefonassistenten** müssen über den neuen Dr.wait-Zugang gehen, unverändert, ohne Präfix und ohne abgeschnittene Ziffern. Der Anruf kommt dann bei `sip:<Rufnummer>@drwait.sip.twilio.com` an.

## Rufnummer des Anrufers durchreichen

In OMC unter **System Miscellaneous > Feature Design**:

- **CLI for external diversion** = True
- **CLI is diverted party** = False

Dann überträgt die Anlage bei weitergeleiteten Anrufen die Nummer des Anrufers und nicht die eigene.

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
