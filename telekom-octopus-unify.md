# Telekom Octopus F / Unify OpenScape Business

Einbindung per SIP (Weg B). Die Octopus-F-Anlagen der Telekom basieren auf Unify OpenScape Business, die Menüs sind gleich. Der Assistent wird als zusätzlicher Internet-Telefonie-Provider angelegt und als externes Ziel in die Gruppe aufgenommen, die Ihre Praxisanrufe annimmt.

Sie brauchen administrativen Zugang zur Anlage. Falls Sie ihn nicht haben, fordern Sie ihn bei der Telekom bzw. Ihrem Anlagenbetreuer an.

## 0. Sicherung

**Datensicherung > OK & Weiter**. Die Sicherung dauert einige Minuten und erscheint danach unter **Backup-Sets**.

## 1. Dr.wait als Internet-Telefonie-Provider anlegen

**Einrichtung > Zentrale Telefonie > Internet-Telefonie > Bearbeiten**. Die erste Seite unverändert mit **OK & Weiter** bestätigen, dann unter **Anderer Provider > Hinzufügen**:

| Feld | Wert |
| --- | --- |
| Provider-Name | `Dr.wait` |
| Gateway Domain Name | `drwait.sip.twilio.com` |
| IP-Adresse / Host-Name | `drwait.sip.twilio.com` |
| Port | `5060` |
| Reregistration-Intervall am Provider | `600` |
| Proxy | `drwait.sip.twilio.com` |

**OK & Weiter**, dann die Zugangsdaten:

| Feld | Wert |
| --- | --- |
| Registrierungsnummer | Ihr Dr.wait-Benutzername |
| Autorisierungsname | Ihr Dr.wait-Benutzername |
| Kennwort (2×) | Ihr Dr.wait-Kennwort |
| Rufnummer | Rufnummer des Telefonassistenten |

Nach **OK & Weiter** zeigt die Anlage den Verbindungsstatus. Ein grünes Feld bedeutet, dass die Registrierung bei Dr.wait geklappt hat.

## 2. Leitungen zuweisen

Erneut **Internet-Telefonie > Bearbeiten**, Haken bei **Dr.wait** setzen, **OK & Weiter** und mindestens eine Leitung zuweisen. Für gleichzeitige Anrufe beim Assistenten entsprechend mehr. Die folgenden Seiten mit **OK & Weiter** durchklicken und mit **Beenden** abschließen.

## 3. Rufnummer des Anrufers durchreichen

**Experten-Modus > Telefonie > Sprachgateway**, unter **Internet-Telefonie Service Provider** den Eintrag **Dr.wait** wählen und **Erweiterte SIP-Provider Daten anzeigen** aktivieren.

- **CLIP no Screening support:** `CLIP in From / trusted number in PAI`

**Übernehmen.** Ohne diese Einstellung sieht der Assistent die Praxisnummer statt der Nummer des Anrufers.

## 4. Assistent in die Gruppe aufnehmen

**Experten-Modus > Telefonie > Kommende Rufe**, links die Gruppe wählen, die Anrufe an die Praxisnummer annimmt, dann **Mitglied hinzufügen**:

| Feld | Wert |
| --- | --- |
| Rufnummer | Externes Ziel |
| Richtung | Dr.wait |
| Externes Ziel | Rufnummer des Telefonassistenten |

**Übernehmen.** Der Assistent klingelt nun mit der Gruppe. Je nach Gruppentyp (parallel, linear, mit Verzögerung) übernimmt er sofort oder erst, wenn niemand abnimmt.

## 5. DSP für die Dr.wait-Richtung

**Experten-Modus > Leitungen/Vernetzung > Richtung**, **Dr.wait** wählen, **Richtungsparameter ändern**, Haken bei **immer DSP benutzen**, **Übernehmen**.

## Ein- und ausschalten

Unter **Kommende Rufe > Mitglieder anzeigen** das externe Ziel Dr.wait aus der Gruppe entfernen bzw. wieder hinzufügen.

## Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen.
