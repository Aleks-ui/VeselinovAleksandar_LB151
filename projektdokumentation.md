# Projekt-Dokumentation

Veselinov

| Datum | Version | Zusammenfassung                                              |
| ----- | ------- | ------------------------------------------------------------ |
| 04.01.2023      | 0.0.1   | Erarbeitung der Kapitel 0 bis 2 |
|11.02.2023| 0.0.2   |Kapitel 2 bis 4 erarbeiten|
|18.02.2023| 0.0.3   |Kapitel 5 GUI erstellt|
|06.02.2023| 0.0.4   |Kapitel 5 bis 7 erarbeitet und programmiert|
|13.02.2023| 0.0.5   |an der Implementierung gearbeitet|
|20.02.2023| 0.0.6   |Implementierung des Projekts, restliche Kapitel durchgeführt (7 bis 9)|
|27.02.2023| 1.0.0   |Code so viel wie möglich verfeinert und Readme.md File erstellt.|

# 0 Ihr Projekt

Im Projekt geht es darum ein Glücksrad-Spiel mittels einer Webapplikation zu implementieren. Im Spiel soll es darum gehen ein Wort, welches in einem Gitter abgebildet wird, zu erraten. Jedes Wort den man erraten soll entspricht zu einer zufälligen Kategorie, damit der Spieler sich beim Erraten orientieren kann. Damit der Spieler das Wort auflöst, muss er entsprechend den Glücksrad drehen. Pro erratenen Buchstaben aus dem Lösungswort, wird dem Spieler ein bestimmter Geldbetrag gutgeschrieben, je nach Wahrscheinlichkeit des Buchstaben. Falls der erratene Buchstabe nicht im Lösungswort enthalten ist, verliert er ein Leben (insg. drei Leben) und das Spiel ist beendet. 

# 1 Analyse

* Tier 1 (Presentation): Highscore-Liste, Spiel-Gitter, Glücksrad mit Feldern.
* Tier 2 (Webserver): Eingabe der Konsonanten, Vokalen oder Wörter, Erdrehen des Glücksrades.
* Tier 3 (Application Server): Erratenen Buchstaben/Wort mit Lösungswort vergleichen, Guthaben entsprechend erhöhen bei Gewinn, bei Kauf von Vokalen Guthaben senken, Lebenspunkte entnehmen.
* Tier 4 (Dataserver): Speicherung der Lösungswörter, Rangliste-Daten, Wahrscheinlichkeit der Felder mit entsprechendem Betrag.

# 2 Technologie

Als Programmiersprache werde ich Java verwenden, um die Darstellung, sowie die Eingabe und Validierung der Daten zu ermöglichen. Damit ich die Daten wie gewünscht speichere, werde ich eine mySQL-Datenbank aufsetzen und diese mit Java verknüpfen und dort all die Daten einfügen bzw. auslesen oder abändern etc.

# 3 Datenbank

Es können sich anfangs Administratoren bzw. Spieler anmelden, wobei die Anmeldedaten vom Spieler nach dem Anmelden in die Datenbank gespeichert werden, damit diese bei der Highscore-Liste aufgerufen und angezeigt werden können. Damit Rätselwörter angelegt werden können wird es eine Schnittstelle zwischen dem Admin und der Datenbank geben, wobei er sich dazu entscheiden kann neue Wörter anzulegen mit der entsprechenden Kategorie oder löschen. Beim Spiel wird das eingegebene Wort mit dem zu erratenden Wort aus der Datenbank verglichen und anschliessend zurückgegeben, ob es falsch oder richtig ist. Alles andere wird vom Webserver/Application-Server übernommen. 

# 4.1 User Stories

✍️ Formulieren Sie klare Anforderungen in der Form von User Stories (*„als … möchte ich … damit …“*) und zu jeder Anforderung mindestens einen dazugehörigen Testfall (in Kapitel 4.2). 

✍️ Formulieren Sie weitere, eigene Anforderungen und Testfälle, wie Sie Ihre Applikation erweitern möchten. Geben Sie diesen statt einer Nummer einen Buchstaben (`A`, `B`, etc.)

| US-№ | Verbindlichkeit | Typ  | Beschreibung                       |
| ---- | --------------- | ---- | ---------------------------------- |
| 1    |Muss|Funktional| Als ein Administrator möchte ich die Eigenschaft besitzen für das Einfügen und Löschen, damit das Spiel flexibler und lediglich Up-To-Date ist.  |
| 2    |Muss|Funktional| Als ein Benutzer möchte ich mich anmelden können, damit mein High-Score mit den anderen verglichen wird. |
| 3    |Muss|Qualität| Als ein Spieler möchte ich die Spieleigenschaften auf dem Screen angezeigt bekommen, damit ich weiss wie viel Leben, Geld, etc. mir übrig bleibt. |
| 4    |Muss|Funktional| Als ein Spieler möchte ich bei Eingabe ein Resultat erhalten, damit ich weiss ob die Eingabe richtig oder falsch war. |
| 5    |Muss|Qualität| Als ein Spieler möchte ich die Kategorie des Wortes ansehen, damit die Erratung des Wortes leichter fällt. |
| 6    |Muss|Funktional| Als ein Kandidat möchte ich bei der Suche einen Spielernamen eingeben können, damit die Suche schneller und effizienter geht für das Filtrieren. |
| 7    |Muss|Randbedingung| Als ein Administrator möchte Hacking-Lücken mit Lösungen vermindern, damit das Spiel nicht von Hacker angegriffen oder korrupt wird.  |

✍️ Jede User Story hat eine ganzzahlige Nummer (1, 2, 3 etc. oder Zahl), eine Verbindlichkeit (Muss oder Kann?), und einen Typ (Funktional, Qualität, Rand). 

# 4.2 Testfälle

| TC-№ | Vorbereitung | Eingabe | Erwartete Ausgabe |
| ---- | ------------ | ------- | ----------------- |
| 1.1  |Programm ist gestartet. Man ist als Administrator angemeldet.|1. Bei Menü des Admins auf 'Show all Word Items' gehen, 2. Rätselwort 'Das ist ein Test' auf Button "Entfernen" drücken, 3. Auf Button 'Rätselwort hinzufügen' den Rätselwort 'Scooby-Doo' eingeben und anschliessend auf bestätigen.|Die Datenbank führt den entsprechenden Code aus, um den Rätselwort zu löschen und das andere hinzuzufügen --> Beim Spielen wird das Rätselwort erscheinen.|
| 1.2  |Programm ist gestartet. Man ist als Admin angemeldet|1. Auf 'Rangliste bearbeiten' drücken, 2. Gewünschten Spieler aus der Liste auswählen und anschliessend auf Löschen drücken.|Datenbank führt Befehl aus und der Spieler wird bei der Anzeige der Rangliste ausgeblendet bzw. nicht mehr angezeigt.|
| 2.1  |Programm ist gestartet. Man ist als Spieler angemeldet|1. Auf 'Rangliste ansehen' drücken, 2. Auf Button 'Mein Platz ausgeben' drücken.|Datenbank führt Befehl aus und es wird ein Fenster ausgegeben mit dem Ranglisten-Platz bei dem man sich befindet.|
| 3.1  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken.|Im Spiel werden seit dem Anfang die benötigten Hinweise wie Leben, Geldbetrag, etc. angezeigt.|
| 3.2  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken, 2. Solange spielen, bis man beim Rad 'Geldbetrag x' erhalten hat, 3. Eingabe für Wort auswählen und anschliessend 'Falsche Antwort' eingeben.|Man verliert sein Leben wenn man eine falsche Antwort getätigt hat.|
| 4.1  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken, 2. Solange spielen, bis man beim Rad 'Geldbetrag x' erhalten hat, 3. Eingabe für Wort auswählen und anschliessend 'Nicht richtig' eingeben.|Das Spiel gibt aus, dass die Eingabe falsch war.|
| 5.1  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken, 2. Oben rechts den Kategorienamen ablesen.|Das Spiel gibt aus, um welche Kategorie sich das Wort handelt und man verliert einen bestimmten Geldbetrag dazu.|
| 6.1  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Rangliste anzeigen' drücken, 2. Bei Button 'Such-Filter' drücken, 3. Spielername 'Bob' eingeben und suchen.|Das Programm gibt den gesuchten Speieler Bob aus und zeigt seinen Geldbetrag-Highscore an.|
| 7.1  |Programm ist gestartet. Man befindet sich beim Login|1. SQL-Injection beim Namen eingeben (damit es denkt, dass man ein Admin wäre letztendlich), 2. Bei Button 'Anmelden' drücken|Die Datenbank erkennt, dass es um eine SQL-Injection handelt und führt den ganzen Teil als String aus, aufgrund des Prepared-Statement. --> Man ist als Spieler trotzdem angemeldet.|

# 5 Prototyp

Siehe Quellcode.


# 6 Implementation

| User Story | Datum | Beschreibung |
| ---------- | ----- | ------------ |
| 1        |06.02.2023|Ich habe eine Datenbank mittels MySQL erstellt, damit der Admin die Spielwörter und Spieler einfügen bzw. löschen kann.|
| 2        |06.02.2023|Login erstellt, bei dem der Score auf 0 gesetzt wird (weil man noch keine Runde erspielt hat) und jeder Spieler sehen kann was ihr High-Score ist, um sich mit den anderen zu vergleichen.|
| 3        |13.02.2023|Ich habe das XHTML des Spiels einigermassen umgesetzt, damit noch das Leben des Spielers, den Betrag, das versteckte Wort, etc. angezeigt wird.|
| 4        |13.02.2023|Für die Umsetzung habe ich geplant ein Input-Dialogfeld zu gestalten, damit der User einen Buchstaben eingeben kann und verglichen wird, ob es im versteckten Wort vorkommt. Wenn ja: Buchstabe wird in den Linien eingesetzt, wenn nein: Spieler verliert Lebenspunkte.|
| 5        |20.02.2023|Dies wird auch im XHTML ausgegeben des Spiels. Es wird bei der Backing-Bean die Kategorie herausgeholt und gesetzt.|
| 6        |20.02.2023|Such-Filter erstellen mit einem Query, damit dann bei der Seite die gewünschte Daten ausgegeben werden.|
| 7        |27.02.2023|Beim Login SQL-Injection Lösung implementieren (alles wird ansonsten mit JPA konfiguriert).|

# 7 Projektdokumentation

| US-№ | Erledigt? | Entsprechende Code-Dateien oder Erklärung |
| ---- | --------- | ----------------------------------------- |
| 1    | ja |Siehe bei Web-Pages/spiel oder Web-Pages/user die XHTML-Seiten. Die Daten werden mittels JPA in den Java-Klassen gespeichert und bleiben dort enthalten.|
| 2  |ja|Wurde erstellt, aber funktioniert nicht richtig, da man sich bei der Eingabe bei Web-Pages/user/Create.xhtml immer einloggen kann.|
| 3  |ja|bei Web-Pages/user/game.xhtml sieht man Output-Texts, die die Werte von GluecksspielBean aufnehmen und dort anzeigen lassen.|
| 4  |Nein|Die Eingabe, damit der User das Wort erraten kann konnte ich nicht umsetzen, da ich nicht genügend Zeit übrig hatte. Jedoch habe ich im GluecksspielBean die Logik umgesetzt --> mit findString() und findChar() schauen die Methoden, ob die Inputs der Buchstaben/Wörter mit denen des versteckten Wortes übereinstimmen. Falls ja, dann wird das Wort eingesetzt, falls nein verliert man einen Lebenspunkt.|
| 5  |Ja|Noch nicht ausprobiert ob es funktioniert. Beim Spielcontroller wird mit getRandomWord() ein Wort aus der Datenbank geholt und beim Bean weitergegeben als verstecktes Wort (gleichzeitig wird auch die Kategorie des Wortes im Bean gesetzt).|
| 6  |Nein|Nice-To-Have konnte ich nicht erstellen, da mir die Zeit fehlte.|
| 7  |Ja|Bei Spiel- und User-Controller verwende ich eine Mischung aus JPA und JDBC. Für die Erstellung der Werte benutze ich den Entity-Manager, welches mir ermöglicht die Daten direkt in die Datenbank zu speichern. JDBC hilft mir nur mit den Querys, die ich erstellt habe, um bspw. ein zufälliges Wort rauszupicken oder beim Login zu schauen, ob es den User gibt, den man eingegeben hat bei der Login-Seite.|

# 8 Testprotokoll


| TC-№ | Datum | Resultat | Tester |
| ---- | ----- | -------- | ------ |
| 1.1  |27.02.2023|NOK|  Aleksandar Veselinov  |
| 1.2  |27.02.2023|  Teilweise OK        |Aleksandar Veselinov|
| 2.1  |27.02.2023|NOK|  Aleksandar Veselinov  |
| 3.1  |27.02.2023|OK|  Aleksandar Veselinov  |
| 3.2  |27.02.2023|NOK|  Aleksandar Veselinov  |
| 4.1  |27.02.2023|NOK|  Aleksandar Veselinov  |
| 5.1  |27.02.2023|OK|  Aleksandar Veselinov  |
| 6.1  |27.02.2023|NOK|  Aleksandar Veselinov  |
| 7.1  |27.02.2023|Teilweise OK|  Aleksandar Veselinov  |

Fazit: Da das Spiel nicht vollständig implementiert wurde, fehlen einige Features. Man kann sich registrieren und immer einloggen wann man möchte. Die Wörter-Liste wird nicht korrekt angezeigt. Das Spiel ist noch teilweise unvervollständigt (GUI-Elemente gibt es teilweise, jedoch wurde die Logik vollständig umgesetzt).

# 9 `README.md`

ReadMe.md File ist abgelegt innerhalb des Projektes (LB-Bewertung).
[ReadMe.md](https://github.com/Aleks-ui/VeselinovAleksandar_LB151/files/10838754/ReadMe.md)


# 10 Allgemeines

- [x] Ich habe die Rechtschreibung überprüft
- [x] Ich habe überprüft, dass die Nummerierung von Testfällen und User Stories übereinstimmen
- [x] Ich habe alle mit ✍️ markierten Teile ersetzt

# Quellcode als Zip-File
[LB_151_Gluecksspiel.zip](https://github.com/Aleks-ui/VeselinovAleksandar_LB151/files/10838781/LB_151_Gluecksspiel.zip)

