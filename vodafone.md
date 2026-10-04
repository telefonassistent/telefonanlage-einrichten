# Vodafone Festnetz

Weiterleitung auf die Dr.wait-Rufnummer (Weg A). Für Praxen mit einem Vodafone-Anschluss (DSL oder Kabel) ohne eigene Telefonanlage.

Sie brauchen nur die Rufnummer des Telefonassistenten von Dr.wait. SIP-Zugangsdaten sind nicht nötig.

## Einrichtung

Richten Sie die Rufumleitung im Vodafone-Kundenportal ein oder direkt am Telefon per Tastencode:

| Umleitung | Einschalten | Ausschalten |
| --- | --- | --- |
| sofort | `*21*<Rufnummer des Telefonassistenten>#` | `#21#` |
| bei Nichtannahme | `*61*<Rufnummer des Telefonassistenten>#` | `#61#` |
| bei besetzt | `*67*<Rufnummer des Telefonassistenten>#` | `#67#` |

Nutzen Sie eine eigene Telefonanlage am Vodafone-Anschluss (z. B. eine FRITZ!Box), richten Sie die Weiterleitung besser dort ein. Siehe [Alle Anlagen](README.md).

## Rufnummer des Anrufers

Ob Vodafone die Nummer des Anrufers bei Umleitungen überträgt, hängt vom Anschluss ab. Prüfen Sie es mit dem Testanruf. Bei Vodafone-Geschäftsanschlüssen für Telefonanlagen (IP-Anlagen-Anschluss) ist „CLIP no screening“ verfügbar.

## Ein- und ausschalten

Die Weiterleitung deaktivieren bzw. wieder aktivieren.

## Test

Von einem Mobiltelefon die Praxisnummer anrufen, bis der Assistent übernimmt. Im Posteingang muss die Nummer des Mobiltelefons erscheinen. Steht dort die Praxisnummer, fragen Sie Ihren Anbieter nach „CLIP no screening“ für Weiterleitungen.

---

Fragen zur Einrichtung: [Dr.wait Support auf WhatsApp](https://wa.me/493012076512) (+49 30 12076512) · [Alle Anlagen](README.md)
