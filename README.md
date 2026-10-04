# Telefonanlage mit dem Dr.wait Telefonassistenten verbinden

Anleitungen, um den [KI-Telefonassistenten von Dr.wait](https://www.drwait.de/telefonassistent) in die Telefonie einer Arztpraxis einzubinden. Die Praxis behält ihre Rufnummer, der Assistent übernimmt die Anrufe, die die Praxis an ihn weitergibt, und erhält dabei die Rufnummer des Anrufers.

## Zwei Wege

**A. Weiterleitung auf die Dr.wait-Rufnummer.** Dr.wait stellt Ihnen eine eigene Rufnummer für den Assistenten bereit. Sie leiten Anrufe beim Telefonanbieter oder in der Cloud-Telefonanlage auf diese Nummer um. Keine Zugangsdaten, kein Eingriff in die Anlage.

**B. Einbindung per SIP.** Ihre Telefonanlage meldet sich mit eigenen Zugangsdaten bei Dr.wait an und übergibt Anrufe direkt über das Internet. Die Anlage entscheidet, wann der Assistent übernimmt, zum Beispiel parallel, nach einer Wartezeit oder nur bei besetzt.

Beide Wege sind auch unter [Einrichtungsmöglichkeiten](https://www.drwait.de/d/docs/telefonassistent/einrichtung) beschrieben.

## Anleitungen für Weg B

| Telefonanlage | Anleitung |
| --- | --- |
| AVM FRITZ!Box | [fritzbox.md](fritzbox.md) |
| 3CX | [3cx.md](3cx.md) |
| Ansitel | [ansitel.md](ansitel.md) |
| Andere SIP-fähige Anlagen | [andere-anlagen.md](andere-anlagen.md) |

Für Weg A richten Sie bei Ihrem Telefonanbieter oder in Ihrer Cloud-Telefonanlage eine Rufumleitung auf die Rufnummer des Telefonassistenten ein, sofort, nach einer Wartezeit oder bei besetzt.

## Zugangsdaten für Weg B

| Bezeichnung | Wert |
| --- | --- |
| SIP-Domain (Registrar / Proxy) | `drwait.sip.twilio.com` |
| Benutzername | individuell, z. B. `meinepraxis` |
| Kennwort | wird Ihnen persönlich mitgeteilt |
| Rufnummer des Telefonassistenten | individuell, z. B. `0705115630XX` |

Für Weg A brauchen Sie nur die Rufnummer des Telefonassistenten.

Der Telefonassistent sollte vorher unter [Einstellungen > Telefonassistent](https://app.drwait.de/s/ivr) aktiviert und mit dem Testmodus geprüft sein.

## Worauf es bei jeder SIP-Anlage ankommt

1. **Anmeldung (Registrierung)** an `drwait.sip.twilio.com` mit Benutzername und Kennwort.
2. **Ziel** jeder Weiterleitung ist die Rufnummer des Telefonassistenten, also `sip:<Rufnummer>@drwait.sip.twilio.com`.
3. **Rufnummer des Anrufers durchreichen.** Im SIP-Header `From` muss die Nummer des Patienten stehen, nicht die Praxisnummer und nicht der Benutzername. Nur dann kann der Assistent Patienten zuordnen, SMS senden und Rückrufnummern korrekt ablegen.
4. **Codecs** G.711 a-law und G.711 u-law.

## Vor und nach der Einrichtung

- **Sicherung:** Sichern Sie die Konfiguration Ihrer Anlage vor der ersten Änderung. Damit kommen Sie jederzeit zum Ausgangszustand zurück.
- **Anrufbeantworter:** Ein aktiver Anrufbeantworter oder eine bestehende Rufumleitung nimmt Anrufe oft an, bevor der Assistent sie erreicht. Schalten Sie ihn für den Test aus.
- **Test:** Rufen Sie die Praxisnummer von einem Mobiltelefon an. Der Assistent sollte antworten, und im [Posteingang](https://www.drwait.de/d/docs/posteingang) sollte die Nummer des Mobiltelefons erscheinen. Steht dort die Praxisnummer oder der Benutzername, ist Punkt 3 noch nicht erfüllt.
- **Ein- und ausschalten:** Jede Anleitung beschreibt, welcher Schalter den Assistenten später wieder aus dem Anrufweg nimmt, ohne die Einrichtung zu verlieren.

## Hilfe

Ihre Anlage fehlt oder die Einrichtung klappt nicht? Schreiben Sie uns: [Dr.wait Support auf WhatsApp](https://wa.me/493012076512) (+49 30 12076512). Korrekturen und Ergänzungen zu den Anleitungen nehmen wir gerne als Issue oder Pull Request entgegen.

---

Ein Projekt von [Dr.wait](https://www.drwait.de/) · [Über Dr.wait](https://github.com/drwait/overview)
