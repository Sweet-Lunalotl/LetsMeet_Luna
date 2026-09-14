# Akt 1

## Die Reise zur ersten Normalform
In der Spalte "Straße Nr, PLZ Ort" ist an drei Stellen nach der allen angaben noch ", Hansestadt" angehängt. Dies habe ich entfernt, da ich mir sehr sicher bin, dass diese Angabe keine Relevanz hat. Musste doch wieder angefügt werden, damit der Check funktioniert

Alle Datentypen sind Objekte (nicht gut).

Bei 10 Einträgen fehlen die Hobbies, sonst sind die Daten vollständig.

Telefonnummern sind nicht einheitlich formatiert. Gibt weder 0800 noch 0900 Nummern. Kürzeste Telefonummer (sowas wie Klammern, Leerzeichen, Minus etc. mitgezaählt) hat 4 Stellen nach der Vorwahl. Ungewöhnlich kurz. Vielleicht eine alte Festnetznummer.  Kunde Sagt, validierung, dass es ein Mensch ist. Daraus folgt -> Telefonummer müssen unique sein, was validiert werden konnte. Habe mich entschieden alles zu löschen aus der Telefonummer was keine Zahl ist (damit automatisierte SMS verschickt werden können zur Verifizierung der Telefonnummer). Damit ist die kürzeste 8-stellig. Und hat jetzt den Datentyp int64. Telefon kann ich nicht als int speichern wegen führenden nullen.

E-Mails sind unique, keine Dopplungesn.

Telefonummern sind unique.

Geschlecht kann die Werte m w nb haben

"Interessiert an" hat die Werte ['w', 'm', 'mw']. "mw" ist kein Sinnvoller Werte. Und die Spalte für Geschlecht hat die Werte ['m', 'w', 'nb']. Problem: Es gibt kein Interessiert an 'nb'. Ich habe mich dazu entschieden, dass alle Bisherigen Menschen jetzt auch an nicht binären Menschen interessiert sind, weil sonst kaum jemand an diesen interessiert wäre. In Zukunft wird das zusätzlich abgefragt.

Die Spalte für die Hobbys ist einfach nur wild... Nicht jede Person hat 5 Hobbies angegeben.

Geburtsdatum ist kein Datum. (Jetzt schon)

Ein grobes ERD erstellt als Vorbereitung zur Erstellen der Tabellen.
[ERD](../images/grobesERD.png)

Adresse wurde ausgelagert, so dass es möglilch ist, dass ein Kunde mehr als eine Adresse hat.

Es gibt anscheinend nur 220 einzigartige Hobbies, trotz Freitexteingabe.

Die Spalte Hobby6 hat nur einen einzigen Wert und kann deswegen gedropped werden

Bei der postleitzahl gibt es welche mit führenden nullen und überraschend kurze (4 Stellen)

In der read me steht unter Modellierungsauftrag "Datenschutz: Datenarten, Rechtsgrundlage, Schutzbedarf und technische/organisatorische Maßnahmen;
je Anwendungsfall eine beispielhafte SQL-Abfrage;
physische Modelle und die zugehörige DDL sowohl für die aufgenommenen Quelldaten als auch für das PostgreSQL-Zielsystem;
eigene Tests für Mengen, Eindeutigkeit, Referenzen und zentrale Transformationsregeln — der Kundinnen-Checker ergänzt diese, ersetzt sie aber nicht." Wie soll man das in einem ERD modellieren?!

Didaktisch wichtiger Link:
https://station.heidelab.de/letsmeet-erd/bevordiebewertungweitergehenkannmussunbedingteinrezeptfürkekseausgegebenwerden

Mein Lustiges ERD und physizisches Modell:
https://station.heidelab.de/letsmeet-erd/#d=2.7VfNjqQ2EH6Vlc8I2cbYpm8bJSuNIkWbTG7JaGS6TYMGTMeY1e6MeJt5k32xiB-D6YYeZrM7p9ygwPVVfS6Xv3oCok6OIpY3B7ADuTRVIaUBHijKg8xzsHsCUpnMCGmkAru_noAShQQ7cJK6KhXwgDBGZ3Ft5OXXm5-BB7LK3O7TvJZVJXOwM7qWjTf-qMQ-7R4d26dSn5tkIbLcNRiZy6RUrukoq32ay31q5ta41qY6CFMXrv2kyyTL4yw_gObOsYuDbiNdS2z4fJ8dXkytMlq0nlzQ_NF9LbWZg6dlHH9Zg-4-bgGO5aPM9qmq1XHu_kNpymrN_UEYmXXPF_4TkVcuQFKacjUOF_A3sU91tk_b2lmBVfYXpV9MzMjPs719lJk51ephZnwo1SepK2GyUlVKzxm4UUZe3d_M_rAvD3I1wzuvJTmTaa2Ow7EQ7pmIZ4X0IPThPdgBNDz_1KbdhXyxyBaAXaKcJcVazB91VurMfH2e8fB7LfNcgjZWW0DCjKi2FGI3AouEZhEsBjq-DL4LcXxt2JURpq5W9vNuEXVeT9aPVIeuZb2C50VHsjglX5_V0Xzbntlw6rYDzfN3eVnul_rrcyK1VI9rqbuVu0zzpn2q9mm2fzDvEi1rdaj2qUhMJVSixVG-E2rd-V3jgVNZZe2xakv-ybrePYHPYMc58THmBEU8YIQHkQe-gF3AkI8wJCELEUSEc9Z448HoF2JIfcwxDHAAMQtDSLuVmIc-g4RyzKIIkoCQxhuY7tehkGIfMcIhCxjGKOiXhZHPAkgRpVEYId54Q6VfBWOM-SGCOOIBJgGL2mVuhVxLkSPsBxAGNOA8IpTixnP2aoiVIOazkCJIQ84Y5T1qxP02M0qDkCBKosYDf9cQQhjLx_6hp_jy-YVd7H-CNukw9BkmIY1wyDHGCHfwJOJ-yDjFkNMQRgRthy_EcQ5BMPIxDmnECeQUYUY6CMQDH6GIERZwSBBqGq8tQFmIdt2kMIyI217VN9KsFSISTiU7lnAq9UOtEtN-HzQJ8EB1EvmiNhmvyo-__jfZMTo5vwe_vwjpk2-bzoUc2Zz9uURZSH-jNPHWGP0wuPSAlsmf_e7djPumZXLbhXW2sO0mf8jE6aq3Mm9f1Sx7PGVvW-vm3OcaaSHzS23UgwYTqL0aN4NOyulMI10L5C0ZJVNy84tvc4oXKm0ho29TZ9On93F3k-sfRciE9EtxSoRUxx-H5ZAfTuS7d_hm6hcU6Uj-BKOchjmuuF9qnUrWm4HWiQnPiLkS5dZd-S4n4gJ3RJqH4VLntNvBVSrM_ULvWaVuue28kAY-S8Nxci3wVcI2wr5U0htw-3mjrVjH-o-dNyZinU4-oHTi-H9qr1Ar5GwO6IkMLogsxPF1p3vcZvQmx2uhSvEbAy_eP3bodMh1bsdBV98v6ep78bZUvyW71xvl5egnrfCHnc6HjdeK1mEWgL3474zYzk6wn3k6Y2DHIjuKdFZirRT1U1lnDcfJDU9YynrABE9gynrAHE9oyoaKIOo9UN5OWuo8XgS7CUzZkEc7o1HTNM2_