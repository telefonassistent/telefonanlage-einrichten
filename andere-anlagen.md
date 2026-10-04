# Andere SIP-fähige Telefonanlagen

Jede Telefonanlage, die einen zusätzlichen SIP-Provider (SIP-Trunk, SIP-Amt, Internetrufnummer) aufnehmen kann, lässt sich mit dem Dr.wait Telefonassistenten verbinden. Die Begriffe unterscheiden sich je nach Hersteller, die Schritte sind immer dieselben.

## 1. SIP-Provider anlegen

| Einstellung | Wert |
| --- | --- |
| Registrar / Server / Domain | `drwait.sip.twilio.com` |
| Outbound-Proxy | `drwait.sip.twilio.com` (oder leer) |
| Port / Transport | `5060`, UDP |
| Benutzername / Authentifizierungs-ID | Ihr Dr.wait-Benutzername |
| Kennwort | Ihr Dr.wait-Kennwort |
| Registrierung | aktiv |
| Codecs | G.711 a-law (PCMA), G.711 u-law (PCMU) |

Verwenden Sie die Vorlage **Generischer Provider**, **Anderer Anbieter** o. ä., keine Vorlage eines anderen Telefonanbieters.

## 2. Ausgehende Route

Anrufe an die **Rufnummer des Telefonassistenten** über diesen Provider leiten. Die Rufnummer unverändert übergeben, ohne Präfix und ohne abgeschnittene Ziffern. Der Anruf muss bei `sip:<Rufnummer>@drwait.sip.twilio.com` ankommen.

## 3. Rufnummer des Anrufers durchreichen

Die wichtigste Einstellung. Bei weitergeleiteten Anrufen muss die Anlage die Nummer des **ursprünglichen Anrufers** senden, nicht die eigene Praxisnummer und nicht den Benutzernamen. Typische Bezeichnungen:

- „Original Caller ID“, „Pass through“, „OriginatorCallerID“
- „CLIP no Screening“
- „Rufnummer im Display- und Usernamen“
- bei Asterisk-basierten Anlagen: `${CALLERID(num)}` bzw. Option `o` beim `Dial`

Rufnummernformat ohne automatisch vorangestellte Landes- oder Ortsvorwahl.

## 4. Weiterleitung

An der Stelle, an der der Assistent übernehmen soll, als Ziel die Rufnummer des Telefonassistenten über den neuen Provider eintragen:

- als zusätzliches Mitglied einer Gruppe (parallel klingeln),
- als Ziel bei Nichtannahme oder bei besetzt,
- als Taste in einem Sprachmenü,
- als zeitgesteuertes Ziel außerhalb der Sprechzeiten.

Prüfen Sie, dass „Besetzt bei Besetzt“ (Busy on Busy) für die Praxisnummer aus ist, sonst erreicht ein zweiter Anrufer den Assistenten nicht.

## 5. Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen. Steht dort die Praxisnummer oder der Benutzername, Schritt 3 prüfen.

Ihre Anlage soll eine eigene Anleitung bekommen? Schreiben Sie uns per [WhatsApp](https://wa.me/493012076512) oder legen Sie ein Issue an.
