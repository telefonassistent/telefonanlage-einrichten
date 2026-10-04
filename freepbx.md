# FreePBX

Einbindung per SIP (Weg B). Dr.wait wird als PJSIP-Trunk angelegt.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [Trunks (englisch)](https://sangomakb.atlassian.net/wiki/spaces/PG/pages/25690439)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. Trunk anlegen

**Connectivity > Trunks > Add Trunk > Add SIP (chan_pjsip) Trunk**

Reiter **General**:

| Einstellung | Wert |
| --- | --- |
| Trunk Name | `drwait` |
| Outbound CallerID | leer |
| CID Options | **Allow Any CID** |

Reiter **pjsip Settings**:

| Einstellung | Wert |
| --- | --- |
| Username | Ihr Dr.wait-Benutzername |
| Secret | Ihr Dr.wait-Kennwort |
| Authentication | Outbound |
| Registration | Send |
| SIP Server | `drwait.sip.twilio.com` |
| SIP Server Port | `5060` |
| Codecs | ulaw, alaw |

Im Reiter **Advanced** das Feld **From User** leer lassen. Sonst steht bei jedem Anruf Ihr Benutzername statt der Nummer des Anrufers im `From`-Header.

## 2. Outbound Route

**Connectivity > Outbound Routes > Add Outbound Route**, Dial Pattern = Rufnummer des Telefonassistenten, Trunk Sequence = `drwait`.

## Rufnummer des Anrufers durchreichen

Im Trunk **CID Options** = **Allow Any CID** (Schritt 1). Dann reicht FreePBX bei weitergeleiteten externen Anrufen die Nummer des Anrufers durch.

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
