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

#Akt 2

Didaktisch wichtiger Link:
https://station.heidelab.de/letsmeet-erd/bevordiebewertungweitergehenkannmussunbedingteinrezeptfürkekseausgegebenwerden

Mein Lustiges ERD und physizisches Modell:
https://station.heidelab.de/letsmeet-erd/#d=2.7VfNjts2EH6VgGdBICmKpHxL0AZYFCjSbm9tYFD2yBJWolyJCpJd6G32TfbFCv1TtuT1Jt1FD73JI898M9-M5ucBqSo6qBBu9miDUjBlBmCQg7J8D2mKNg8ItEmMAgMabf58QFplgDboCEWZa-QgZUyRhJWB87c3PyEHJaW53cVpBWUJKdqYooLaGf-o1S5uHy3Zl7w4FUGmktQWGEghyrUtOkC5i1PYxWYuDavClHtlqsyWH4s8StIwSfeo_mzJ1b5oPF0LrH-9TfbPhlaaQjWWbND03v6ZF2YOHudh-G0Nun15DXAI95DsYl3pw9z8x9zk5Zr5vTKQtM9n9iOVljZAlJt81Q8b8Fe1i4tkFze1swKrh7_o4tnADHyd5fYeEnOs9N1MeJfrL1CUyiS5LnUxZ-BGG7iY32T4wy7fLzDRR_jZaUhOIK70of8slP1NhLNCulPF_j3aINI_f2jCbl0-UxoKYFDRlkqGnLEUlFkL4FOR5EVinh5npPxWQZpCz4WySiG0PVhCJcuOXtSxPM3UYc3T0ihTlSv5_LyIOq-nZV5H6BL0Hsyy-y8yBNkxenrUhxVbV-asrJrOtNYvi6fHCArQ92uh25W7jPRDeSp3cbK7M--iAiq9L3exikypdFSoA7xTuvUKHfMyaT6rpuQfBtObB_QVbaRkLqWSkUB6gkkvcNA3tPEEcQnFzBc-wYRJKWpn_DA6RYq5SyXFHvUwFb6PeatJpe8KzLikIggw8xirnZ7pTo_4nLpEMImFJyglXqfmB67wMCecB35AZO30lX4RTAjh-gTTQHqUeSJo1OwKuRSiJNT1MPa4J2XAOKe1Y-Wq95UR4QqfE8x9KQSXHWog3SYyzj2fEc6C2kF_VRhjHMJ999BRfP78TLa6P-EhaN93BWU-D6gvKaWEtvAskK4vJKdYch8HjFwPn6nDHIJR4lLq80AyLDmhgrUQRHouIYFgwpOYEVLXTlNokKlGb9owjAqb9tQ10qRZRABPpTmWcAzFXaUj07zvdxLkoPKo0sXdZByVn375sbVjNHI6B__9JaQLnkzBT1Pk6uhPV5SF8K9cTZw1Rj_2Jh1UQPRHl72bMW8FRLetWyeKTdu5hTSyutDvEHUzxoqeWnOub61Xxz7fkRYin-1Gk_hvez52bniTG8OwvNqNaZc62ZouufaWHLMpuPkovDrEs71tIaLv29emV-_DdoYXr0XIhPRzdowU6MPrYVnk-xP59lS_mvqFHXUkf4LRVgsdNbZLzVRD9WKgZ1jyT1g6tXRdVlb6-KtnSJPT6bONldkudKNV6pYb0TOe0xPPLSP_RcLsOdYeHU3F2jTSMxrbJfh_Ii8QqWB2B3REemdEZurwsm959IW8dUiDBn1j4MVpMxydFrns7AraLu3VW_W9VL8lu6_RFs9PPxgWf9zu-bh2mqW1vwUwm4R0uJ2wnITecBYNp0grZYOUEz5J_fFyoxOWHixQRicwPVigkk5oenCVYNJZ4LK5tPSpvwS3F5imp3LBg7qu638A

Ich habe die MongoDB in einen df geschrieben, damit ich mich mit den eigenheiten von einer MongoDB nicht beschäftigen muss

In der XML und der MongoDB sind die Einträgen in der gleichen Reiehenfolge sortiert. Ungewöhnlich, macht es aber deutlich einfacher die beiden Datenquellen miteinander zu vergleichen.

Name und Telefonummer sind in der MongoDB anders formatiert als in dem Datafram den ich aus der xml gebaut habe. Ich muss diese zunächst in eine einheitliche Form bringen

Der Kunde hat spezifiziert, dass die MongoDB die aktuelleren Daten hat
Abweichungen zwischen der MongoDB und der XML:
1. Bei dem Vornamen fällt folgendes raus:
        Vorname Vorname_dm
294     Joyeux      Joyeux
472   Hosseini    Hosseini
480   Qarizada    Qarizada
741  Thibaudet   Thibaudet
873     Benoit      Benoit
907     Nazemi      Nazemi
Die Vornamen sind alle identisch geschrieben, somit kann der einzige Unterschied führende Leerzeichen sein
2. Kunde mit ID = 62 hat den Namen von Pommer nach Vogelsang geändert (Heirat oder Scheidung)
3. Bei der Telefonummer gibt es Abweichungen bei dem Kunde mit der ID 500 von 0531638986 zu 0531771204. Dies scheint eine aktualisierung der Reufnummer zu sein und wollte übernummen werden.
4. Bei der Telefonummer gibt es Abweichungen bei dem Kunde mit der ID 707 von 0617162808 zu 0. Das deutet darauf hin, dass der Nutzer die Nummer entfernen wollte und eine wiederherstellung der Nummer könnte rechtlich schwirig sein, weshalb diese Nummer einfach gelöscht werden solle

Nachdem die verschachtelten Einträge aus der MongoDB in eigene Dataframes geschrieben wurde, fällt auf, dass der Dataframe für Freund leer ist. Das ist seltsam. Anscheindend sind die Daten nach wie vor verloren

Es wurden 300 Nachrichten geschrieben. Die Likes sehen gut aus mit 500 Einträgen. 

Die KundenID funktioniert übergreifend über die Dataframes df, dm, messages_df, likes_df. Deswegen treffe ich die Entscheidung mit der kunde_id zu arbeiten, statt der Empfehlung der read me zu folgen, die die email vorschlägt. Denn ich habe damit gerechnet, dass emails geändert wurden, was nicht der Fall war.

Nach einer kurzen Internetrechere kam raus, dass man mit dem Datentyp BYTEA Bilder speichern kann. Also nutze ich dieses Format für die Bilder.



