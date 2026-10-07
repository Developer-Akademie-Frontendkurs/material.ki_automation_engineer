# Die acht Ausleih-Anfragen

> **Der Lehr-Fall ab Modul 2** · Stand 2026-09-29 · gehört zu `../../PROJEKT.md`
> Das Arbeitsmaterial, das du durch deinen Workflow schickst: **über das Formular `Ausleih-Postfach`**,
> mit dem fertigen Befehl unter jeder Anfrage. Dieselben acht stehen als Tabelle in `ausleih-anfragen.csv`,
> **zum Nachschlagen, nicht zum Importieren.**
> Personen, Geräte und Nummern stammen aus `seed-mitarbeitende.csv` und `seed-ausleihen.csv` —
> **nicht** neu erfinden, sonst findet später der Lookup nichts.

## Der Fall

Die **IT-Abteilung der Steigfeld GmbH** verleiht Laptops, Headsets, Monitore und Dockingstationen
an die Belegschaft. Anfragen kommen an ein Sammelpostfach: *Wann muss ich das zurückgeben?*,
*Ich brauche ein Headset*, *Das Ding ist kaputt*. Wer welches Gerät hat und bis wann, steht in
einer Datenbank — nur eben nicht in der Mail.

**Das ist ein anderer Prozess als das Abschlussprojekt**, und das ist Absicht: Was du hier baust,
sollst du danach **übertragen** können, nicht wiedererkennen.


## Lass dieses Blatt bis Sektion 3 zu

Die acht Anfragen sind **Eingangsmaterial**, kein Nachschlagewerk: Du schickst sie durch und siehst
nach, was herauskommt. **Wo sie hingehören, findest du selbst heraus** — in Sektion 4 baust du die
Regeln dafür und zählst nach, wie gut sie treffen.

**Zum Gegenprüfen gibt es ein eigenes Blatt**, `ausleih-anfragen-soll.md`. Es sagt, wo jede Anfrage
hingehört, und liegt hier im Ordner — **erst öffnen, wenn du in Sektion 4 deine Ausgänge notiert
hast.** *Erst messen, dann vergleichen: in der Reihenfolge liegt die Übung.*


## So schickst du sie ab

**Immer über das Formular `Ausleih-Postfach`.** Der Webhook aus Modul 3 ist für das Onboarding-Ticket
da, nicht für diese Anfragen.

Einmal tippen wir eine Anfrage im Video von Hand ins Formular, damit du siehst, was ankommt. **Danach
nimmst du den Befehl:** kopieren, einfügen, fertig.

**1 · Die Adresse holen.** Im Node `Ausleih-Postfach` steht die **Production URL**:

```
http://localhost:5678/form/a1b2c3d4-...
```

Der Teil hinter `/form/` ist bei dir ein anderer. **Und der Workflow muss veröffentlicht sein:** Ein
Entwurf hat keine Adresse, die von außen antwortet.

**2 · Die Adresse einmal setzen**, im selben Fenster, in dem du danach schickst.

**Mac** *(Terminal)*:

```
ADRESSE="DEINE-FORMULAR-ADRESSE"
```

**Windows** *(PowerShell)*:

```
$ADRESSE = "DEINE-FORMULAR-ADRESSE"
```

→ **`DEINE-FORMULAR-ADRESSE` ersetzen**, Anführungszeichen stehen lassen. **Neues Fenster, Schritt 2
noch einmal:** Ein frisch geöffnetes Terminal kennt `ADRESSE` nicht.

**3 · Schicken.** Unter jeder Anfrage steht ihr Befehl, einzeilig für Mac und Windows. **Alle acht auf
einmal** stehen ganz unten.

→ **Der Befehl gibt nichts zurück**, und das ist richtig so. Nachgesehen wird in n8n unter
**Ausführungen**: Dort steht ein neuer Lauf, den niemand von Hand gestartet hat.

→ **Windows: vorn `curl.exe`, nicht `curl`.** In der PowerShell ist `curl` ein anderer Befehl mit
demselben Namen. In den Befehlen unten steht es schon richtig.

→ **Wenn ein Node Daten zum Ziehen braucht**, zählt nur ein **Testlauf**. Dann Schritt 2 mit der
**Test URL** setzen (`/form-test/` statt `/form/`), im Editor erst **`Execute workflow`** klicken und
danach **eine** Anfrage schicken. Die Test-Adresse wartet nur auf diese eine.

## Die acht Anfragen

So, wie sie im Postfach ankommen. Dieselben acht stehen in `ausleih-anfragen.csv`.

### 01

**Von:** Heike Naumann · `h.naumann@steigfeld-beispiel.de`  
**Betreff:** Rückgabe L-0068

> Guten Tag, ich habe im September das Laptop L-0068 bekommen. Bis wann muss ich es zurückgeben? Viele Grüße, Heike Naumann

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Heike Naumann" -F "field-1=h.naumann@steigfeld-beispiel.de" -F "field-2=Rückgabe L-0068" -F "field-3=Guten Tag, ich habe im September das Laptop L-0068 bekommen. Bis wann muss ich es zurückgeben? Viele Grüße, Heike Naumann"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Heike Naumann" -F "field-1=h.naumann@steigfeld-beispiel.de" -F "field-2=Rückgabe L-0068" -F "field-3=Guten Tag, ich habe im September das Laptop L-0068 bekommen. Bis wann muss ich es zurückgeben? Viele Grüße, Heike Naumann"
```

### 02

**Von:** Jonas Pfeil · `j.pfeil@steigfeld-beispiel.de`  
**Betreff:** Rückgabe

> Hallo IT-Team, ich habe noch Geräte von euch und weiß nicht mehr, bis wann ich sie zurückgeben muss. Meine Personalnummer ist P-1035. Viele Grüße, Jonas Pfeil

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Jonas Pfeil" -F "field-1=j.pfeil@steigfeld-beispiel.de" -F "field-2=Rückgabe" -F "field-3=Hallo IT-Team, ich habe noch Geräte von euch und weiß nicht mehr, bis wann ich sie zurückgeben muss. Meine Personalnummer ist P-1035. Viele Grüße, Jonas Pfeil"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Jonas Pfeil" -F "field-1=j.pfeil@steigfeld-beispiel.de" -F "field-2=Rückgabe" -F "field-3=Hallo IT-Team, ich habe noch Geräte von euch und weiß nicht mehr, bis wann ich sie zurückgeben muss. Meine Personalnummer ist P-1035. Viele Grüße, Jonas Pfeil"
```

### 03

**Von:** Annika Sorge · `a.sorge@steigfeld-beispiel.de`  
**Betreff:** L-0042

> Guten Morgen, ich habe hier noch das Laptop L-0042 stehen. Bis wann muss ich es zurückgeben? Annika Sorge

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Annika Sorge" -F "field-1=a.sorge@steigfeld-beispiel.de" -F "field-2=L-0042" -F "field-3=Guten Morgen, ich habe hier noch das Laptop L-0042 stehen. Bis wann muss ich es zurückgeben? Annika Sorge"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Annika Sorge" -F "field-1=a.sorge@steigfeld-beispiel.de" -F "field-2=L-0042" -F "field-3=Guten Morgen, ich habe hier noch das Laptop L-0042 stehen. Bis wann muss ich es zurückgeben? Annika Sorge"
```

### 04

**Von:** Sven Löwe · `s.loewe@steigfeld-beispiel.de`  
**Betreff:** Headset fürs Homeoffice

> Hallo IT, mein altes Headset ist zwar nicht defekt, aber die Ohrpolster sind komplett durch. Kann ich mir ein neues ausleihen? Personalnummer P-1118. Danke, Sven Löwe

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Sven Löwe" -F "field-1=s.loewe@steigfeld-beispiel.de" -F "field-2=Headset fürs Homeoffice" -F "field-3=Hallo IT, mein altes Headset ist zwar nicht defekt, aber die Ohrpolster sind komplett durch. Kann ich mir ein neues ausleihen? Personalnummer P-1118. Danke, Sven Löwe"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Sven Löwe" -F "field-1=s.loewe@steigfeld-beispiel.de" -F "field-2=Headset fürs Homeoffice" -F "field-3=Hallo IT, mein altes Headset ist zwar nicht defekt, aber die Ohrpolster sind komplett durch. Kann ich mir ein neues ausleihen? Personalnummer P-1118. Danke, Sven Löwe"
```

### 05

**Von:** Daniel Ostrowski · `d.ostrowski@steigfeld-beispiel.de`  
**Betreff:** Headset H-0234 kaputt

> Moin, das Headset H-0234 ist kaputt, es lädt nicht mehr. Was mache ich damit? Daniel Ostrowski

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Daniel Ostrowski" -F "field-1=d.ostrowski@steigfeld-beispiel.de" -F "field-2=Headset H-0234 kaputt" -F "field-3=Moin, das Headset H-0234 ist kaputt, es lädt nicht mehr. Was mache ich damit? Daniel Ostrowski"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Daniel Ostrowski" -F "field-1=d.ostrowski@steigfeld-beispiel.de" -F "field-2=Headset H-0234 kaputt" -F "field-3=Moin, das Headset H-0234 ist kaputt, es lädt nicht mehr. Was mache ich damit? Daniel Ostrowski"
```

### 06

**Von:** Ruth Fellner · `r.fellner@steigfeld-beispiel.de`  
**Betreff:** Ausleihe

> *(kein Text)*

→ **Die leere Angabe `field-3=` mitschicken**, nicht weglassen. So verhält sich der Aufruf wie ein
Formular, in dem jemand das Textfeld leer gelassen hat.

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Ruth Fellner" -F "field-1=r.fellner@steigfeld-beispiel.de" -F "field-2=Ausleihe" -F "field-3="
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Ruth Fellner" -F "field-1=r.fellner@steigfeld-beispiel.de" -F "field-2=Ausleihe" -F "field-3="
```

### 07

**Von:** Clara Siebert · `c.siebert@steigfeld-beispiel.de`  
**Betreff:** Kurze Info

> Hallo zusammen, ich wollte nur kurz Bescheid geben, dass ich ab Montag im anderen Büro sitze. Viele Grüße, Clara Siebert

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Clara Siebert" -F "field-1=c.siebert@steigfeld-beispiel.de" -F "field-2=Kurze Info" -F "field-3=Hallo zusammen, ich wollte nur kurz Bescheid geben, dass ich ab Montag im anderen Büro sitze. Viele Grüße, Clara Siebert"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Clara Siebert" -F "field-1=c.siebert@steigfeld-beispiel.de" -F "field-2=Kurze Info" -F "field-3=Hallo zusammen, ich wollte nur kurz Bescheid geben, dass ich ab Montag im anderen Büro sitze. Viele Grüße, Clara Siebert"
```

### 08

**Von:** Bettina Rauch · `b.rauch@steigfeld-beispiel.de`  
**Betreff:** Frage

> Hallo IT, ich räume gerade meinen Schreibtisch auf. Habe ich bei euch noch etwas zur Rückgabe offen? Meine Personalnummer ist P-1105. Danke, Bettina Rauch

*Mac:*

```
curl -X POST "$ADRESSE" -F "field-0=Bettina Rauch" -F "field-1=b.rauch@steigfeld-beispiel.de" -F "field-2=Frage" -F "field-3=Hallo IT, ich räume gerade meinen Schreibtisch auf. Habe ich bei euch noch etwas zur Rückgabe offen? Meine Personalnummer ist P-1105. Danke, Bettina Rauch"
```

*Windows:*

```
curl.exe -X POST $ADRESSE -F "field-0=Bettina Rauch" -F "field-1=b.rauch@steigfeld-beispiel.de" -F "field-2=Frage" -F "field-3=Hallo IT, ich räume gerade meinen Schreibtisch auf. Habe ich bei euch noch etwas zur Rückgabe offen? Meine Personalnummer ist P-1105. Danke, Bettina Rauch"
```

## Alle acht am Stück

Erst **Schritt 2** von oben ausführen, dann den ganzen Block einfügen. Zwischen zwei Anfragen wartet er
eine Sekunde, so kommen sie in dieser Reihenfolge an. **Der oberste Lauf in den Ausführungen ist 08.**

**Mac** *(Terminal)*:

```
curl -X POST "$ADRESSE" -F "field-0=Heike Naumann" -F "field-1=h.naumann@steigfeld-beispiel.de" -F "field-2=Rückgabe L-0068" -F "field-3=Guten Tag, ich habe im September das Laptop L-0068 bekommen. Bis wann muss ich es zurückgeben? Viele Grüße, Heike Naumann"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Jonas Pfeil" -F "field-1=j.pfeil@steigfeld-beispiel.de" -F "field-2=Rückgabe" -F "field-3=Hallo IT-Team, ich habe noch Geräte von euch und weiß nicht mehr, bis wann ich sie zurückgeben muss. Meine Personalnummer ist P-1035. Viele Grüße, Jonas Pfeil"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Annika Sorge" -F "field-1=a.sorge@steigfeld-beispiel.de" -F "field-2=L-0042" -F "field-3=Guten Morgen, ich habe hier noch das Laptop L-0042 stehen. Bis wann muss ich es zurückgeben? Annika Sorge"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Sven Löwe" -F "field-1=s.loewe@steigfeld-beispiel.de" -F "field-2=Headset fürs Homeoffice" -F "field-3=Hallo IT, mein altes Headset ist zwar nicht defekt, aber die Ohrpolster sind komplett durch. Kann ich mir ein neues ausleihen? Personalnummer P-1118. Danke, Sven Löwe"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Daniel Ostrowski" -F "field-1=d.ostrowski@steigfeld-beispiel.de" -F "field-2=Headset H-0234 kaputt" -F "field-3=Moin, das Headset H-0234 ist kaputt, es lädt nicht mehr. Was mache ich damit? Daniel Ostrowski"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Ruth Fellner" -F "field-1=r.fellner@steigfeld-beispiel.de" -F "field-2=Ausleihe" -F "field-3="; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Clara Siebert" -F "field-1=c.siebert@steigfeld-beispiel.de" -F "field-2=Kurze Info" -F "field-3=Hallo zusammen, ich wollte nur kurz Bescheid geben, dass ich ab Montag im anderen Büro sitze. Viele Grüße, Clara Siebert"; sleep 1
curl -X POST "$ADRESSE" -F "field-0=Bettina Rauch" -F "field-1=b.rauch@steigfeld-beispiel.de" -F "field-2=Frage" -F "field-3=Hallo IT, ich räume gerade meinen Schreibtisch auf. Habe ich bei euch noch etwas zur Rückgabe offen? Meine Personalnummer ist P-1105. Danke, Bettina Rauch"; sleep 1
```

**Windows** *(PowerShell)*:

```
curl.exe -X POST $ADRESSE -F "field-0=Heike Naumann" -F "field-1=h.naumann@steigfeld-beispiel.de" -F "field-2=Rückgabe L-0068" -F "field-3=Guten Tag, ich habe im September das Laptop L-0068 bekommen. Bis wann muss ich es zurückgeben? Viele Grüße, Heike Naumann"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Jonas Pfeil" -F "field-1=j.pfeil@steigfeld-beispiel.de" -F "field-2=Rückgabe" -F "field-3=Hallo IT-Team, ich habe noch Geräte von euch und weiß nicht mehr, bis wann ich sie zurückgeben muss. Meine Personalnummer ist P-1035. Viele Grüße, Jonas Pfeil"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Annika Sorge" -F "field-1=a.sorge@steigfeld-beispiel.de" -F "field-2=L-0042" -F "field-3=Guten Morgen, ich habe hier noch das Laptop L-0042 stehen. Bis wann muss ich es zurückgeben? Annika Sorge"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Sven Löwe" -F "field-1=s.loewe@steigfeld-beispiel.de" -F "field-2=Headset fürs Homeoffice" -F "field-3=Hallo IT, mein altes Headset ist zwar nicht defekt, aber die Ohrpolster sind komplett durch. Kann ich mir ein neues ausleihen? Personalnummer P-1118. Danke, Sven Löwe"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Daniel Ostrowski" -F "field-1=d.ostrowski@steigfeld-beispiel.de" -F "field-2=Headset H-0234 kaputt" -F "field-3=Moin, das Headset H-0234 ist kaputt, es lädt nicht mehr. Was mache ich damit? Daniel Ostrowski"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Ruth Fellner" -F "field-1=r.fellner@steigfeld-beispiel.de" -F "field-2=Ausleihe" -F "field-3="; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Clara Siebert" -F "field-1=c.siebert@steigfeld-beispiel.de" -F "field-2=Kurze Info" -F "field-3=Hallo zusammen, ich wollte nur kurz Bescheid geben, dass ich ab Montag im anderen Büro sitze. Viele Grüße, Clara Siebert"; Start-Sleep 1
curl.exe -X POST $ADRESSE -F "field-0=Bettina Rauch" -F "field-1=b.rauch@steigfeld-beispiel.de" -F "field-2=Frage" -F "field-3=Hallo IT, ich räume gerade meinen Schreibtisch auf. Habe ich bei euch noch etwas zur Rückgabe offen? Meine Personalnummer ist P-1105. Danke, Bettina Rauch"; Start-Sleep 1
```

→ **Einmal schicken, nicht zweimal.** Jeder Lauf legt einen Vorgang an: Schickst du den Block zweimal,
steht jede Anfrage zweimal in deiner Tabelle.
