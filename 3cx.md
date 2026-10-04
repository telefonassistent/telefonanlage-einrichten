# 3CX

Einbindung per SIP (Weg B). 3CX bekommt einen zusätzlichen SIP-Trunk zu Dr.wait. Eine ausgehende Regel schickt Anrufe an die Rufnummer des Telefonassistenten über diesen Trunk, und die Praxis entscheidet, an welcher Stelle Anrufe dorthin weitergeleitet werden.

Die Menünamen entsprechen 3CX Version 20. In älteren Versionen heißen einige Punkte anders (z. B. „Signalisierungsgruppen“ statt „Ring Groups“), die Einstellungen sind dieselben.

## 0. Sicherung

**Admin > Backup** (bzw. **Sichern/Wiederh.**), vollständige Sicherung mit Kennwort anlegen.

## 1. SIP-Trunk anlegen

**Admin > Voice & Chat > Add Trunk**

- Country: **Generic**
- Provider: **Generic VoIP Provider**

| Feld | Wert |
| --- | --- |
| Name | `drwait` |
| Registrar / Server | `drwait.sip.twilio.com` |
| Authentication ID (SIP User ID) | Ihr Dr.wait-Benutzername |
| Authentication password | Ihr Dr.wait-Kennwort |
| Main Trunk No | Rufnummer des Telefonassistenten |

Unter **Codecs** G.711 a-law und G.711 u-law aktivieren. Speichern.

## 2. Rufnummer des Anrufers durchreichen

Im Trunk `drwait` unter **Outbound Parameters**:

| Parameter | Wert |
| --- | --- |
| To: User Part | `CalledNum` |
| From: User Part | `OriginatorCallerID` |
| From: Display Name | `OriginatorCallerID` |

Falls Ihre Version stattdessen eine Option **Outbound Caller ID** anbietet: **Use original Caller ID** bzw. **Pass through**, keine feste Nummer.

## 3. Ausgehende Regel

**Outbound Rules > Add**

| Feld | Wert |
| --- | --- |
| Rule Name | `drwait` |
| Calls to numbers starting with prefix | Rufnummer des Telefonassistenten |
| Strip digits | `0` |
| Prepend | leer |
| Route 1 | Trunk `drwait` |

## 4. Anrufe an den Assistenten geben

Wählen Sie, an welcher Stelle der Assistent übernimmt.

**Klingelgruppe (empfohlen).** Öffnen Sie die Ring Group, auf die Ihre Praxisnummer eingeht (Eingehende Regeln / DID zeigen, welche das ist). Stellen Sie **Destination if no answer** auf **Forward to external number** mit der Rufnummer des Telefonassistenten. Die Praxistelefone klingeln zuerst, der Assistent übernimmt, wenn niemand abnimmt. Die Klingeldauer der Gruppe bestimmt die Wartezeit.

**Digital Receptionist.** Für eine Taste im Sprachmenü als Aktion **Transfer to external number** mit der Rufnummer des Telefonassistenten wählen.

**Einzelne Nebenstelle.** In der Weiterleitung der Nebenstelle als Ziel die Rufnummer des Telefonassistenten eintragen.

Zum Ausschalten nehmen Sie die Weiterleitung aus der Klingelgruppe, dem Menü oder der Nebenstelle wieder heraus.

## 5. Test

1. Von einem internen Telefon die Rufnummer des Telefonassistenten wählen. Der Assistent sollte antworten.
2. Von einem Mobiltelefon die Praxisnummer anrufen und bis zur Weiterleitung warten.
3. Im Posteingang prüfen, dass die Nummer des Mobiltelefons erscheint und nicht die Praxisnummer.

## Fehlerbehebung

| Problem | Lösung |
| --- | --- |
| Trunk registriert sich nicht | Benutzername und Kennwort prüfen. Details unter **Admin > Event Log**. |
| Kein oder einseitiges Audio | G.711 a-law und u-law im Trunk aktivieren. |
| Anruf geht nicht über den Trunk | Ausgehende Regel prüfen: Präfix gleich der Rufnummer des Telefonassistenten, Route Trunk `drwait`. |
| Assistent sieht die Praxisnummer statt der Anrufernummer | Outbound Parameters aus Schritt 2 prüfen. |
