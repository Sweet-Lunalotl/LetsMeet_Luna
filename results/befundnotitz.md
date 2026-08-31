# Akt 1

## Die Reise zur ersten Normalform
In der Spalte "Straße Nr, PLZ Ort" ist an drei Stellen nach der allen angaben noch ", Hansestadt" angehängt. Dies habe ich entfernt, da ich mir sehr sicher bin, dass diese Angabe keine Relevanz hat.

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