# Akt 1

## Die Reise zur ersten Normalform
In der Spalte "Straße Nr, PLZ Ort" ist an drei Stellen nach der allen angaben noch ", Hansestadt" angehängt. Dies habe ich entfernt, da ich mir sehr sicher bin, dass diese Angabe keine Relevanz hat.

Alle Datentypen sind Objekte (nicht gut).

Bei 10 Einträgen fehlen die Hobbies, sonst sind die Daten vollständig.

Telefonnummern sind nicht einheitlich formatiert. Gibt weder 0800 noch 0900 Nummern. Kürzeste Telefonummer (sowas wie Klammern, Leerzeichen, Minus etc. mitgezaählt) hat 4 Stellen nach der Vorwahl. Ungewöhnlich kurz. Vielleicht eine alte Festnetznummer.  Kunde Sagt, validierung, dass es ein Mensch ist. Daraus folgt -> Telefonummer müssen unique sein, was validiert werden konnte.

E-Mails sind unique, keine Dopplungen.

"Interessiert an" hat die Werte ['w', 'm', 'mw']. "mw" ist kein Sinnvoller Werte. Und die Spalte für Geschlecht hat die Werte ['m', 'w', 'nb']. Problem: Es gibt kein Interessiert an 'nb'.

Die Spalte für die Hobbys ist einfach nur wild...

Geburtsdatum ist kein Datum.