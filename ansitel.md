# Ansitel

Einbindung per SIP (Weg B). Die Ansitel-Anlage bekommt eine SIP-Leitung zu Dr.wait, eine ausgehende Route auf die Rufnummer des Telefonassistenten und eine Weiterleitung, die über eine interne Rufnummer erreichbar ist.

## 0. Sicherung

Sichern Sie die aktuelle Konfiguration der Anlage, bevor Sie Änderungen vornehmen.

## 1. SIP-Leitung anlegen

**Routen > Leitungen > Neue SIP-Leitung**

| Feld | Wert |
| --- | --- |
| Protokoll (Treiber) | SIP |
| Providername | `drwait` |
| Host | `drwait.sip.twilio.com` |
| FromDomain | `drwait.sip.twilio.com` |
| Benutzername | Ihr Dr.wait-Benutzername |
| Passwort | Ihr Dr.wait-Kennwort |
| Insecure | `invite,port` |
| Codecs | G.711 a-law, G.711 u-law |
| Registrierung / Wählaufruf | leer |

## 2. Ausgehende Route

**Routen > Ausgehende Routen > Neue ausgehende Route**

- Name: `drwait`
- Präfix: `9`
- Wählplan (Rufnummer des Telefonassistenten einsetzen):

```
NoOp(Outgoing Route drwait - Input EXTEN: ${EXTEN})
Set(DIALNUM=${EXTEN})
Dial(SIP/drwait/<Rufnummer des Telefonassistenten>,60,oxtTrK)
Hangup()
```

Die Option `o` im `Dial`-Befehl übernimmt die Rufnummer des ursprünglichen Anrufers. Dadurch sieht der Assistent die Nummer des Patienten.

## 3. Weiterleitung

**Endpunkte > Weiterleitung > Neue Weiterleitung**

- Name: z. B. `drwaitforward`
- Ziel: `9` gefolgt von einer freien internen Rufnummer für den Assistenten, z. B. `9747`
- Präfix: `9`

## 4. Wählplan-Rufnummer

**Wählplan > Wählplan > Neue Rufnummer**

- Wählplanrufnummer: die interne Rufnummer aus Schritt 3, z. B. `747`
- Objekt: Weiterleitung `drwaitforward`
- alle anderen Felder leer

Über diese interne Rufnummer erreichen Sie den Assistenten nun von jedem Telefon. Leiten Sie Anrufe an die Praxisnummer (Gruppe, Sprachmenü oder Zeitsteuerung) auf diese Rufnummer weiter, damit der Assistent übernimmt.

## 5. Test

1. Konfiguration speichern.
2. Von einem internen Telefon die interne Rufnummer (z. B. `747`) wählen. Der Assistent sollte antworten.
3. Von einem Mobiltelefon die Praxisnummer anrufen und prüfen, dass im Posteingang die Nummer des Mobiltelefons erscheint.
