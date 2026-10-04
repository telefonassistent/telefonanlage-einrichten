# pascom

Einbindung per SIP (Weg B). In pascom wird Dr.wait als generisches SIP-Amt angelegt, der Assistent als externes Gerät, das über dieses Amt erreicht wird.

## 0. Sicherung

**Appliance > Datenbanksicherung > Ausführen**. Optional Mitschnitte, Faxe und Voicemails einschließen. Nach Abschluss erscheint ein Link zur Sicherungsdatei.

## 1. SIP-Amt anlegen

**Gateways > Ämter > Hinzufügen > Generisches SIP-Amt**

| Feld | Wert |
| --- | --- |
| Bezeichnung | `Dr.wait` |
| Benutzername | Ihr Dr.wait-Benutzername |
| Passwort | Ihr Dr.wait-Kennwort |
| Server | `drwait.sip.twilio.com` |
| Präfix eing. Nummer | leer (vorhandenen Wert löschen) |

**Speichern.**

## 2. Ausgehende Rufe über das Amt

**Gateways > Ämter**, Amt **Dr.wait** wählen, **Bearbeiten**, Reiter **Ausgehende Rufe > Hinzufügen > Rufweiterleitung**:

- In-Prefix: leer
- Ziel: Rufnummer des Telefonassistenten
- CID-Nummer: `${CALLERID(num)}`

`${CALLERID(num)}` übergibt die Rufnummer des ursprünglichen Anrufers, sodass der Assistent die Nummer des Patienten sieht. **Speichern.**

## 3. Gerät für den Assistenten

**Geräteliste > Hinzufügen > Via Amt: Beliebiges externes Telefon**

- Name: z. B. `drwait-assistent`
- Rufnummer: Rufnummer des Telefonassistenten

**Speichern.**

## 4. Gerät zuweisen

**Benutzerliste**, den Benutzer bzw. die Gruppe wählen, auf der Anrufe an die Praxisnummer klingeln, **Bearbeiten** und das Gerät `drwait-assistent` hinzufügen. **Speichern** und die Konfiguration mit dem grünen Pfeil **übernehmen**.

## Ein- und ausschalten

Das Gerät `drwait-assistent` aus dem Benutzer bzw. der Gruppe entfernen oder wieder hinzufügen.

## Fehlerbehebung

Prüfen Sie in der Kommandozeile der pascom-Weboberfläche den Registrierungsstatus der SIP-Ämter. Ist das Amt `Dr.wait` nicht registriert, Benutzername, Passwort und Server im Amt prüfen.

## Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen.
