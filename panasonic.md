# Panasonic KX-NS / KX-NSX

Einbindung per SIP (Weg B). Dr.wait wird über die virtuelle SIP-Karte der Anlage (V-SIPGW) als zusätzlicher SIP-Zugang angelegt.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [SIP-Trunk (englisch)](https://docs.connect.panasonic.com/pcc/support/pbx/manual/kx-ns/sip-trunk/index.html)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. SIP-Zugang anlegen

Auf der virtuellen SIP-Karte (**V-SIPGW16**) einen freien Port öffnen, **Port Property**, und die Reiter **Main**, **Account** und **Register** ausfüllen.

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
