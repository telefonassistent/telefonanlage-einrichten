# Asterisk

Einbindung per SIP (Weg B). Konfiguration mit `res_pjsip`. Für Anlagen mit grafischer Oberfläche auf Asterisk-Basis (FreePBX, pascom, STARFACE) die jeweilige Anleitung verwenden.

Sie brauchen die vier Zugangsdaten von Dr.wait: SIP-Domain `drwait.sip.twilio.com`, Benutzername, Kennwort und die Rufnummer des Telefonassistenten. Grundlagen und Begriffe: [Übersicht](README.md#zugangsdaten-für-weg-b).

Hersteller-Dokumentation: [res_pjsip Configuration Examples (englisch)](https://docs.asterisk.org/Configuration/Channel-Drivers/SIP/Configuring-res_pjsip/res_pjsip-Configuration-Examples/)

## 0. Sicherung

Sichern Sie die Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. pjsip.conf

```ini
[drwait]
type=registration
outbound_auth=drwait-auth
server_uri=sip:drwait.sip.twilio.com
client_uri=sip:<Benutzername>@drwait.sip.twilio.com
retry_interval=60

[drwait-auth]
type=auth
auth_type=userpass
username=<Benutzername>
password=<Kennwort>

[drwait]
type=aor
contact=sip:drwait.sip.twilio.com

[drwait]
type=endpoint
context=from-drwait
disallow=all
allow=alaw,ulaw
outbound_auth=drwait-auth
aors=drwait
```

Kein `from_user` am Endpoint setzen. Sonst steht bei jedem Anruf der Benutzername statt der Nummer des Anrufers im `From`-Header.

## 2. Wählregel

```ini
exten => _X.,1,Dial(PJSIP/<Rufnummer des Telefonassistenten>@drwait,60,o)
```

Oder als feste Nebenstelle, die Ihre Gruppe oder Ihr Sprachmenü anwählt.

## Rufnummer des Anrufers durchreichen

Die Option `o` im `Dial`-Befehl übernimmt die Caller ID des ursprünglichen Anrufers für den Anruf zu Dr.wait. Prüfen Sie mit `pjsip show registrations`, dass die Registrierung steht.

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
