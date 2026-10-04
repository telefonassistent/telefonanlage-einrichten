# LANCOM (VoIP Call Manager)

Einbindung per SIP (Weg B). LANCOM-Router mit VoIP Call Manager können Dr.wait als zusätzliche SIP-Leitung führen.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [SIP-Leitungen](https://knowledgebase.lancom-systems.de/x/rz8sAg)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. SIP-Leitung anlegen

In **LANconfig > VoIP Call Manager > Leitungen > SIP-Leitungen > Hinzufügen**.

| Einstellung | Wert |
| --- | --- |
| Registrar / Server / Domain | `drwait.sip.twilio.com` |
| Benutzername / Authentifizierungs-ID | Ihr Dr.wait-Benutzername |
| Kennwort | Ihr Dr.wait-Kennwort |
| Registrierung | aktiv |
| Port / Transport | `5060`, UDP |
| Codecs | G.711 a-law (PCMA), G.711 u-law (PCMU) |

## 2. Route zur Rufnummer des Telefonassistenten

Im **Call-Router** eine Regel anlegen, die Anrufe an die Rufnummer des Telefonassistenten auf die Dr.wait-Leitung schickt. Anrufe an die **Rufnummer des Telefonassistenten** müssen über den neuen Dr.wait-Zugang gehen, unverändert, ohne Präfix und ohne abgeschnittene Ziffern. Der Anruf kommt dann bei `sip:<Rufnummer>@drwait.sip.twilio.com` an.

## Rufnummer des Anrufers durchreichen

Die Hersteller-Dokumentation nennt dafür keine eigene Einstellung. Suchen Sie im Dr.wait-Zugang bzw. in der Leitung nach „CLIP no screening“, „Original Caller ID“ oder „Rufnummer des Anrufers übermitteln“ und aktivieren Sie sie. Bei weitergeleiteten Anrufen muss im SIP-Header `From` die Nummer des Anrufers stehen, nicht die Praxisnummer und nicht der Benutzername.

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
