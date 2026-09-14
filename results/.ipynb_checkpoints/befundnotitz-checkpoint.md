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

Mein Lustiges ERD und physizisches Modell:
https://station.heidelab.de/letsmeet-erd/#d=2.7VfNjts2EH6VgGdBICmKpHxL0QZYFCjSbm9tYND2yBJWolyKCpJd6G32TfbFCv1ZlC3ZTtNd9NCbPNbMN_PNaH6ekKrivdrA3Q6tUAa2zAEs8lBe7CDL0OoJgbapVWBBo9UfT0irHNAKHcCUhUYeUtaadFNZOP_37kfkobS099skq6AsIUMrayqoveOLWm2T9tGRfS7MqQhylWauwEIGcaFd0R7KbZLBNrFT6aYyttwpW-Wu_GCKOM02abZD9SdHrnam8XQpsP7vdbq7GlppjWosuaDZo_uzMHYKnhSbzdcl6PbPW4A38AjpNtGV3k_NfyhsUS6Z3ykLaft8Zj9WWekCxIUtFv1wAX9R28Sk26SpnQVYPbyizdXALHyZ5PYRUnuo9MNE-FDoz2BKZdNCl9pMGbjTFi7mNx1e2Ba7GSb6CD95DckpJJXe95-Fcr-JzaSQHpTZvUcrRPrnH5qwW5fPlIYCGFS0o5Ij71gKyi4F8NGkhUnty_OElF8ryDLouVBOKWxcD-ZQybyjF3UcT3O1X_K0tMpW5UI-P82iTutpntcjdAl6B3be_W8yBPkhfnnW-wVbN-asrJrOtNQvzctzDAb041LobuXOI31Xnsptkm4f7LvYQKV35TZRsS2Vjo3awzulW6_QoSjT5rNqSv5pML16Ql_QSkrmUyoZiWQgmAwiD31Fq0AQn1DMQhESTJiUovaOH0anSDH3qaQ4oAGmIgwxbzWpDH2BGZdURBFmAWO11zPd6ZGQU58IJrEIBKUk6NTCyBcB5oTzKIyIrL2-0i-CCSH8kGAayYCyQESNmlshl0KUhPoBxgEPpIwY57T2nFz1vjIifBFygnkoheCyQ42k30TGeRAywllUe-jPCmOMN_DYPXQUnz9fyVb3Eh6CDkNfUBbyiIaSUkpoC88i6YdCcoolD3HEyO3wudpPIRglPqUhjyTDkhMqWAtBZOATEgkmAokZIXXtNYUGuWr0xg3Dqk3TnrpGmjaLCOCxNI8lnIB5qHRsm__7nQR5qDyobHY3OY7Kjz9_39pxNHI6B__9JaQLnozBj1Pk5uhPV5SZ8PvVZK2rPAdzbUPxloj90Fv2kIH49y6Jd8f0GYjvW-9OFJvucw9Z7DSj3yDuRo1DAnXGXd9hb6ZguirNEDBZkUbxX-6Y7NwIRjeGmXmzG-NKdbI8XXLtLTlmY3DTiXhziDetZFXTDxOV2UrvL4X-ftPObPNakY9IP-WHWIHevx6Ww3I4suxO8Zs5ntlJ57rR5LVzmkeHtNNcj0rruTarobrBpTOsK5SGJ5TOGLstiwt9_tUzqsnpdFonyq5n2tQigfMd6orn9MRzx8h_kTB3zrVHSVPhLo30jMZ2Sf6fyAtEKpjcCR2RwRmRudp_2xd99IW8dUiDBn1j4NlRNRylDrns7Epaz-3da_VPqX5Ldl-jLZ6fhjAcBri9A3DtNUttfytgNgrpcFthOQqD4WwaTpVWygYpJ3yUhsfLjo5YerBAGR3B9GCBSjqi6cFVgklngcvmEtOn_hLcXmiansoFj-q6rv8G

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

Das Profilbild darf leer sein. Falls jemand einen Account öffnet und kein gutes Foto zur Hand hat.
Die quelle bei Hobby darf leer sein. Es dient nur zur dokumentation.

Folgendes hat nicht funktioniert
DLL_FREUNDE="""
CREATE TABLE freunde (
    person_id1 int REFERENCES kunde (kunde_id),
    person_id2 int REFERENCES kunde (kunde_id),
    CONSTRAINT pk_freunde PRIMARY KEY (kunde_id, kunde_id)
)
"""
Da der Fremdschlüssen nicht aus den gleichen Spalten bestehen darf, habe ich einen neuen PK eingeführt
