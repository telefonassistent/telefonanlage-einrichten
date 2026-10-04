# AVM FRITZ!Box

Einbindung per SIP (Weg B). Die FRITZ!Box legt den Telefonassistenten als zusätzliche Internetrufnummer an und leitet Anrufe an die Praxisnummer dorthin um.

**Ausführliche Anleitung mit allen Schritten:** [drwait.de/d/docs/telefonassistent/fritzbox](https://www.drwait.de/d/docs/telefonassistent/fritzbox)

Hier die Kurzfassung zum Nachschlagen.

## Internetrufnummer anlegen

**Telefonie > Eigene Rufnummern > Neue Rufnummer > Internetrufnummer**, Anbieter **Anderer Anbieter** (keine Vorlage verwenden).

| Feld | Wert |
| --- | --- |
| Rufnummer für die Anmeldung | Rufnummer des Telefonassistenten |
| Benutzername | Ihr Dr.wait-Benutzername |
| Authentifizierungsname | leer |
| Kennwort | Ihr Dr.wait-Kennwort |
| Registrar | `drwait.sip.twilio.com` |
| Proxy-Server | `drwait.sip.twilio.com` |

## Einstellungen der Internetrufnummer

Stift-Symbol an der neuen Rufnummer, dann **Rufnummernformat** und **Weitere Einstellungen** aufklappen.

| Einstellung | Wert |
| --- | --- |
| Landesvorwahl | Keine |
| Ortsvorwahl | Keine |
| Rufnummernunterdrückung (CLIR) | aus |
| Rufnummernübermittlung | **Rufnummer im Display- und Usernamen** |
| Rufnummer für die Anmeldung verwenden | aus |
| Anmeldung immer über eine Internetverbindung | an |

„Rufnummer im Display- und Usernamen“ sorgt dafür, dass der Assistent die Nummer des Anrufers sieht.

## Rufumleitung

**Telefonie > Rufbehandlung > Rufumleitung > Neue Rufumleitung**

- Anrufe an: die Praxisnummer
- Zielrufnummer: Rufnummer des Telefonassistenten, vollständig
- Abgangsnummer: die neue Internetrufnummer
- Art: **Sofort**, **Parallelruf** oder **Verzögert**

Mit dem Schalter **Aktiv** schalten Sie den Assistenten später ein und aus.

## Busy on Busy ausschalten

**Telefonie > Telefoniegeräte**, jedes Telefon der Praxisnummer öffnen, Reiter **Merkmale**, **Busy on Busy** deaktivieren.

## Ältere FRITZ!OS-Versionen (vor 7.50)

Die Menüs sind gleich aufgebaut. Schalten Sie vorher die erweiterte Ansicht ein (Drei-Punkte-Menü oben rechts bzw. Link „Ansicht: Standard“ am unteren Rand), sonst fehlen die Bereiche „Rufnummernformat“ und „Weitere Einstellungen“.
