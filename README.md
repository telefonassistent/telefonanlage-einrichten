# Telefonanlage mit dem Dr.wait Telefonassistenten verbinden

Anleitungen, um den [KI-Telefonassistenten von Dr.wait](https://www.drwait.de/telefonassistent) in die Telefonie einer Arztpraxis einzubinden. Die Praxis behält ihre Rufnummer, der Assistent übernimmt die Anrufe, die die Praxis an ihn weitergibt, und erhält dabei die Rufnummer des Anrufers.

## Zwei Wege

**A. Weiterleitung auf die Dr.wait-Rufnummer.** Dr.wait stellt Ihnen eine eigene Rufnummer für den Assistenten bereit. Sie leiten Anrufe beim Telefonanbieter oder in der Cloud-Telefonanlage auf diese Nummer um. Keine Zugangsdaten, kein Eingriff in die Anlage.

**B. Einbindung per SIP.** Ihre Telefonanlage meldet sich mit eigenen Zugangsdaten bei Dr.wait an und übergibt Anrufe direkt über das Internet. Die Anlage entscheidet, wann der Assistent übernimmt, zum Beispiel parallel, nach einer Wartezeit oder nur bei besetzt.

Beide Wege sind auch unter [Einrichtungsmöglichkeiten](https://www.drwait.de/d/docs/telefonassistent/einrichtung) beschrieben.

## Telefonanlagen in der Praxis (Weg B)

Jede Anlage hat eine eigene Anleitung. Ist Ihre Anlage nicht dabei, hilft die [allgemeine Anleitung](andere-anlagen.md) zusammen mit der Hersteller-Dokumentation zum Anlegen eines SIP-Providers. Die letzte Spalte nennt die Einstellung, mit der die Anlage die Rufnummer des Anrufers an den Assistenten weitergibt.

| Telefonanlage | Anleitung | Hersteller-Dokumentation | Rufnummer des Anrufers durchreichen |
| --- | --- | --- | --- |
| AVM FRITZ!Box | [fritzbox.md](fritzbox.md) | | „Rufnummer im Display- und Usernamen“ |
| 3CX | [3cx.md](3cx.md) | [SIP-Trunks](https://www.3cx.de/docs/adminhandbuch/sip-trunks/) | Outbound Parameters: `OriginatorCallerID` |
| Ansitel | [ansitel.md](ansitel.md) | | `Dial`-Option `o` |
| AGFEO ES / HyperVoice | [agfeo.md](agfeo.md) | [SIP-Trunk einrichten (PDF)](https://dect.agfeo.de/agfeo_web/DokuLib.nsf/ResolvRes.xsp?lu=0016) | CLIP no screening |
| Auerswald COMpact / COMmander | [auerswald.md](auerswald.md) | [VoIP-Anbieter verwalten](https://docs.auerswald.de/COMpact5000/Help_V24_de/Buch1/voip_anbieter_verwaltung_reference.html) | VoIP-Account: CLIP no screening |
| STARFACE | [starface.md](starface.md) | [Leitung für einen SIP-Provider](https://knowledge.starface.de/pages/viewpage.action?pageId=46565948) | Leitung > Erweiterte Einstellungen: CLIP No Screening |
| SwyxWare (Enreach) | [swyx.md](swyx.md) | [SIP-Trunk-Gruppe](https://help.enreach.com/cpe/15.00/Administration/Swyx/de-DE/help/chap_trunk_sip.19.4.html) | Trunk > Rufnummernsignalisierung: „Rufnummer des Anrufers signalisieren“ |
| Unify OpenScape Business / Telekom Octopus F | [telekom-octopus-unify.md](telekom-octopus-unify.md) | [SIP Trunk Configuration (PDF)](https://wiki.unify.com/images/5/57/OpenScape-Business-SIP-Trunk-Configuration.pdf) | Sprachgateway: CLIP no Screening „CLIP in From / trusted number in PAI“ |
| Telekom Digitalisierungsbox / bintec elmeg be.IP | [digitalisierungsbox.md](digitalisierungsbox.md) | [Bedienungsanleitung Digitalisierungsbox Premium 2](https://www.telekom.de/hilfe/downloads/bedienungsanleitung-digitalisierungsbox-premium-2) | |
| Mitel MiVoice Office 400 | [mitel.md](mitel.md) | [SIP-Provider bearbeiten](https://productdocuments.mitel.com/doc_finder/MiVoice_Office_400/7.1/en/WebAdmin-OLH_Std/Content/Editing_the_SIP_provider.html) | |
| Alcatel-Lucent OmniPCX Office / OXO Connect | [alcatel-oxo.md](alcatel-oxo.md) | [SIP-Trunk-Konfiguration (PDF)](https://www.al-enterprise.com/-/media/assets/internet/documents/ch-sunrise-r920-confgui-ed0a.pdf) | Feature Design: „CLI for external diversion“ = True |
| Panasonic KX-NS / KX-NSX | [panasonic.md](panasonic.md) | [SIP-Trunk](https://docs.connect.panasonic.com/pcc/support/pbx/manual/kx-ns/sip-trunk/index.html) | |
| innovaphone | [innovaphone.md](innovaphone.md) | [SIP Provider](https://wiki.innovaphone.com/index.php?title=Courseware:Advanced_-_SIP_Provider) | |
| pascom | [pascom.md](pascom.md) | [Amtsvorlagen](https://www.pascom.net/doc/de/pascom-trunk/templates/) | Ausgehende Rufe: CID-Nummer `${CALLERID(num)}` |
| Yeastar P-Series | [yeastar.md](yeastar.md) | [Register Trunk](https://help.yeastar.com/en/p-series-appliance-edition/administrator-guide/create-a-sip-register-trunk.html) | |
| Grandstream UCM | [grandstream.md](grandstream.md) | [SIP Trunks Guide](https://documentation.grandstream.com/knowledge-base/sip-trunks-guide/) | Trunk: „Keep Original CID“ |
| LANCOM (VoIP Call Manager) | [lancom.md](lancom.md) | [SIP-Leitungen](https://knowledgebase.lancom-systems.de/x/rz8sAg) | |
| FreePBX | [freepbx.md](freepbx.md) | [Trunks](https://sangomakb.atlassian.net/wiki/spaces/PG/pages/25690439) | Trunk: CID Options „Allow Any CID“ |
| Asterisk | [asterisk.md](asterisk.md) | [res_pjsip Beispiele](https://docs.asterisk.org/Configuration/Channel-Drivers/SIP/Configuring-res_pjsip/res_pjsip-Configuration-Examples/) | `Dial`-Option `o` |
| Avaya IP Office | [avaya.md](avaya.md) | | |
| Andere SIP-fähige Anlagen | [andere-anlagen.md](andere-anlagen.md) | | |

Ist eine Einstellung nicht angegeben, suchen Sie in der Anlage nach „Original Caller ID“, „CLIP no screening“ oder „Rufnummer des Anrufers übermitteln“ und prüfen Sie das Ergebnis mit dem Testanruf unten.

Ihre Anlage hängt an einem SIP-Trunk wie Telekom CompanyFlex SIP-Trunk, Vodafone IP-Anlagen-Anschluss, sipgate trunking oder easybell? Dann richten Sie Dr.wait als zusätzlichen Provider in der Anlage selbst ein.

## Cloud-Telefonanlagen und Anschlüsse (Weg A)

Bei Cloud-Telefonanlagen und Anschlüssen ohne eigene Anlage richten Sie im Kundenportal eine Rufumleitung auf die Rufnummer des Telefonassistenten ein, sofort, nach einer Wartezeit oder bei besetzt. Jeder Anbieter hat eine eigene Anleitung.

| Anbieter | Anleitung | Hilfe des Anbieters | Rufnummer des Anrufers bei Weiterleitung |
| --- | --- | --- | --- |
| Telekom Festnetz (Telefoniecenter) | [telekom-rufumleitung.md](telekom-rufumleitung.md) | [Anrufweiterleitungen](https://www.telekom.de/hilfe/internet-telefonie/telefonie/anrufweiterleitungen) | |
| Telekom CompanyFlex Cloud PBX | [telekom-cloud-pbx.md](telekom-cloud-pbx.md) | Anrufweiterleitung im Cloud-PBX-Portal | |
| easybell Cloud-Telefonanlage | [easybell.md](easybell.md) | [Rufweiterleitungen](https://www.easybell.de/hilfe/cloud-telefonanlage/antwort/rufweiterleitungen-in-der-cloud-telefonanlage-einrichten/) | [„Weiterleitung der Quellrufnummer“](https://www.easybell.de/hilfe/cloud-telefonanlage/antwort/anruferkennung-bei-weiterleitung-einstellen/) |
| NFON Cloudya | [nfon.md](nfon.md) | [Rufumleitung](https://www.nfon.com/de/service/dokumentation/handbuecher/cloudya/admin-portal/handbuch-admin-portal/c-das-portal-konfigurieren/3-bedienen/3-1-nebenstellen/3-1-1-telefonnebenstellen/3-1-1-6-rufumleitung) | „Angezeigte Nummer bei externer Rufumleitung“ = „Nummer des Anrufers“ |
| sipgate team | [sipgate.md](sipgate.md) | [Weiterleitungen einstellen](https://help.sipgate.de/cloud-telefonanlage/sipgate-nutzen/telefonie/wie-stelle-ich-weiterleitungen-ein) | |
| Placetel (Webex für Placetel) | [placetel.md](placetel.md) | [Anrufweiterleitungen im Webex-Client](https://www.placetel.de/hilfe/webex-fuer-placetel/anrufweiterleitungen-im-webex-client) | |
| 1&1 DSL / Glasfaser | [1und1.md](1und1.md) | [Rufumleitung einrichten](https://hilfe-center.1und1.de/rufumleitung-einrichten) | |
| 1&1 Business Phone | [1und1-business-phone.md](1und1-business-phone.md) | Weiterleitung auf externe Rufnummer im Kundenportal | |
| Vodafone Festnetz | [vodafone.md](vodafone.md) | Rufumleitung im Kundenportal oder per Tastencode | |
| O2 Business Digital Phone | [o2.md](o2.md) | Anrufweiterleitung (extern) im Portal | |
| Microsoft Teams Telefonie | [teams.md](teams.md) | [Anrufweiterleitung in Teams](https://support.microsoft.com/de-de/teams/calls-devices/call-forwarding-call-groups-and-simultaneous-ring-in-microsoft-teams) | |

Ob die Rufnummer des Anrufers bei der Weiterleitung erhalten bleibt, hängt vom Anbieter ab. Prüfen Sie es mit dem Testanruf unten. Kommt nur die Praxisnummer an, fragen Sie Ihren Anbieter nach „CLIP no screening“ für Weiterleitungen.

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
