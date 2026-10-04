# innovaphone (z. B. IP411)

Einbindung per SIP (Weg B). In der innovaphone-Anlage braucht der Assistent drei Teile: ein SIP-Interface im Gateway, eine Trunk Line in der PBX und einen Fork an den Benutzern, bei denen die Praxisnummer klingelt.

## 0. Sicherung

Modul **PBX > Export**, Format **XML**, **Download**.

## 1. SIP-Interface im Gateway

Modul **Gateway > SIP**, ein freies Interface öffnen.

| Feld | Wert |
| --- | --- |
| Name | `Dr.wait` |
| Account | `<Benutzername>@drwait.sip.twilio.com` |
| Username | Ihr Dr.wait-Benutzername |
| Password / Retype | Ihr Dr.wait-Kennwort |
| General Coder Preference | G711A |
| Local Network Coder | G711A |
| Number Mapping (Called) | Called Party in user part of URI |
| Number Mapping (Calling) | CGPN in user part of URI |
| Gatekeeper-Protokoll | H.323 |
| Gatekeeper Address | `127.0.0.1` |
| Name (Registrierung an der PBX) | z. B. `Dr.wait Trunk` |
| Password / Retype (PBX) | frei wählbar, wird in Schritt 2 wieder gebraucht |

**OK.** Ist das Interface richtig eingerichtet, zeigt die Übersicht die aufgelöste Adresse von `drwait.sip.twilio.com`.

## 2. Trunk Line in der PBX

Modul **PBX > Objects > Trunk Line > new**

Bereich **General**:

- Description, Long Name, Name, Display Name: z. B. `Dr.wait Trunk`
- Hardware Id: derselbe Name wie im SIP-Interface (Schritt 1, „Name“)
- Number: eine freie Rufnummer, z. B. `8`. Sie dient später als Präfix für den Fork.
- Password / Retype: dasselbe Kennwort wie in Schritt 1 (PBX)

Bereich **Trunk**: in allen Rufnummernfeldern dieselbe Number wie unter General eintragen. Alle anderen Felder bleiben leer. **OK.**

## 3. Benutzer für den Assistenten

Modul **PBX > Objects > User > new**

- Description, Long Name, Name, Display Name: z. B. `Dr.wait Assistent`
- Hardware Id: eindeutig, nicht dieselbe wie in Schritt 2
- Number: eine freie interne Rufnummer, nicht dieselbe wie in Schritt 2

Die Reiter User, License, Apps und DECT bleiben unverändert.

## 4. Fork einrichten

Modul **PBX > Objects > User > show**. Bei jedem Benutzer, der auf die Praxisnummer klingelt (Zentrale, Empfangstelefone) und beim Benutzer aus Schritt 3 in der Spalte **Fork** auf **+** klicken und als Nummer eintragen:

```
<Number der Trunk Line><Rufnummer des Telefonassistenten>
```

Beispiel: Trunk Line `8`, Assistent `0705115630XX` ergibt `80705115630XX`. Über das Präfix wählt die Anlage die Trunk Line zu Dr.wait, die Anrufe klingeln dann parallel beim Assistenten.

## Ein- und ausschalten

Den Fork an den Benutzern entfernen bzw. wieder anlegen.

## Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen. Danach die Konfiguration erneut exportieren.
