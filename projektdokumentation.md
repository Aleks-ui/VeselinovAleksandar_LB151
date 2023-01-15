# Projekt-Dokumentation

Veselinov

| Datum | Version | Zusammenfassung                                              |
| ----- | ------- | ------------------------------------------------------------ |
| 04.01.2023      | 0.0.1   | Erarbeitung der Kapitel 0 bis 2 |
|       | 0.0.2   |                                                              |
|       | 0.0.3   |                                                              |
|       | 0.0.4   |                                                              |
|       | 0.0.5   |                                                              |
|       | 0.0.6   |                                                              |
|       | 1.0.0   |                                                              |

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
| 4    |Muss|Funktional| Als ein Spieler möchte ich bei Eingabe ein Resultat erhalten, ob die Eingabe richtig oder falsch war. |
| 5    |Muss|Qualität| Als ein Spieler möchte ich die Kategorie des Wortes ansehen, damit die Erratung des Wortes leichter fällt. |
| 6    |Muss|Funktional| Als ein Administrator möchte ich Highscore-Einträge löschen, damit die Datenbank nicht von redundanten/unnötigen Daten Platz verbraucht wird.  |
| 7    |Muss|Funktional| Als ein Kandidat möchte ich bei der Suche einen Spielernamen eingeben können, damit die Suche schneller und effizienter geht für das Filtrieren. |
| 8    |Muss|Randbedingung| Als ein Administrator möchte Hacking-Lücken mit Lösungen vermindern, damit das Spiel nicht von Hacker korrupt oder angegriffen wird.  |

✍️ Jede User Story hat eine ganzzahlige Nummer (1, 2, 3 etc. oder Zahl), eine Verbindlichkeit (Muss oder Kann?), und einen Typ (Funktional, Qualität, Rand). 

# 4.2 Testfälle

| TC-№ | Vorbereitung | Eingabe | Erwartete Ausgabe |
| ---- | ------------ | ------- | ----------------- |
| 1.1  |Programm ist gestartet. Man ist als Administrator angemeldet.|1. Bei Menü des Admins auf 'Rätselwörter bearbeiten' gehen, 2. Rätselwort 'Das ist ein Test' auf Button "Entfernen" drücken, 3. Auf Button 'Rätselwort hinzufügen' den Rätselwort 'Scooby-Doo' eingeben und anschliessend auf bestätigen.|Die Datenbank führt den entsprechenden Code aus, um den Rätselwort zu löschen und das andere hinzuzufügen --> Beim Spielen wird das Rätselwort erscheinen.|
| 1.2  |Programm ist gestartet. Man ist als Admin angemeldet|1. Auf 'Rangliste bearbeiten' drücken, 2. Gewünschten Spieler aus der Liste auswählen und anschliessend auf Löschen drücken.|Datenbank führt Befehl aus und der Spieler wird bei der Anzeige der Rangliste ausgeblendet bzw. nicht mehr angezeigt.|
| 2.1  |Programm ist gestartet. Man ist als Spieler angemeldet|1. Auf 'Rangliste ansehen' drücken, 2. Auf Button 'Mein Platz ausgeben' drücken.|Datenbank führt Befehl aus und es wird ein Fenster ausgegeben mit dem Ranglisten-Platz bei dem man sich befindet.|
| 3.1  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken.|Im Spiel werden seit dem Anfang die benötigten Hinweise wie Leben, Geldbetrag, etc. angezeigt.|
| 3.2  |Programm ist gestartet. Man ist als Spieler angemeldet und befindet sich beim Menü|1. Auf 'Spielen' drücken, 2. Solange spielen, bis man beim Rad 'Geldbetrag x' erhalten hat, 3. Eingabe für Wort auswählen und anschliessend 'Falsche Antwort' eingeben.|Man verliert sein Leben wenn man eine falsche Antwort getätigt hat.|


✍️ Die Nummer hat das Format `N.m`, wobei `N` die Nummer der User Story ist, die der Testfall abdeckt, und `m` von `1` an nach oben gezählt. Beispiel: Der dritte Testfall, der die zweite User Story abdeckt, hat also die Nummer `2.3`.

# 5 Prototyp

✍️ Erstellen Sie Prototypen für das GUI (Admin-Interface und Quiz-Seite).

# 6 Implementation

✍️ Halten Sie fest, wann Sie welche User Story bearbeitet haben

| User Story | Datum | Beschreibung |
| ---------- | ----- | ------------ |
| ...        |       |              |

# 7 Projektdokumentation

| US-№ | Erledigt? | Entsprechende Code-Dateien oder Erklärung |
| ---- | --------- | ----------------------------------------- |
| 1    | ja / nein |                                           |
| ...  |           |                                           |

# 8 Testprotokoll

✍️ Fügen Sie hier den Link zu dem Video ein, welches den Testdurchlauf dokumentiert.

| TC-№ | Datum | Resultat | Tester |
| ---- | ----- | -------- | ------ |
| 1.1  |       |          |        |
| ...  |       |          |        |

✍️ Vergessen Sie nicht, ein Fazit hinzuzufügen, welches das Test-Ergebnis einordnet.

# 9 `README.md`

✍️ Beschreiben Sie ausführlich in einer README.md, wie Ihre Applikation gestartet und ausgeführt wird. Legen Sie eine geeignete Möglichkeit (Skript, Export, …) bei, Ihre Datenbank wiederherzustellen.

# 10 Allgemeines

- [ ] Ich habe die Rechtschreibung überprüft
- [ ] Ich habe überprüft, dass die Nummerierung von Testfällen und User Stories übereinstimmen
- [ ] Ich habe alle mit ✍️ markierten Teile ersetzt
