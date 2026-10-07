# Deine Unterlagen · Modul 2 · n8n-Werkstatt

## Was in den Ordnern liegt

| Ordner | Was drin ist |
|---|---|
| `01_Fall/` | der Fall, an dem du in diesem Modul arbeitest |
| `02_Daten/` | Anfragen, Tabellen und Daten, mit denen du arbeitest |
| `03_Workflows/` | zwei Workflow-Stände zum Importieren: der Start des Moduls und der Endstand |

## So arbeitest du damit

Die Spalte **Wann** in der Liste unten sagt dir, in welcher Sektion du eine Datei brauchst. Öffne sie erst dann.

- **Blätter (PDF)** gibt es meist zweimal: dunkel zum Lesen am Bildschirm, `-light` zum Ausdrucken.
- **Vorlagen (`.txt`)**: Kopie anlegen und die Kopie ausfüllen, die Vorlage bleibt leer.
- **Anfragen schicken:** Den fertigen Befehl für jede der acht Anfragen findest du in `02_Daten/ausleih-anfragen.md` direkt unter der Anfrage. Oben im Blatt steht, wie du deine Formular-Adresse einsetzt.
- **Einen Workflow importieren:** n8n → *Overview* → **Create workflow**, im neuen, leeren Workflow das Menü `⋯` neben dem Namen → **Import** → **From file**, danach **Publish**. Immer in einen neuen Workflow importieren, sonst liegt alles doppelt.

## Alle Dateien

| Datei | Wofür | Wann |
|---|---|---|
| [`02_Daten/ausleih-anfragen.csv`](02_Daten/ausleih-anfragen.csv) | die acht Anfragen ans IT-Postfach, roh | Eingang und Weiche; Einordnen mit Regeln |
| [`02_Daten/ausleih-anfragen.md`](02_Daten/ausleih-anfragen.md) | dieselben acht Anfragen zum Lesen | Eingang und Weiche; Einordnen mit Regeln |
| [`02_Daten/ausleih_vorgaenge-leer.csv`](02_Daten/ausleih_vorgaenge-leer.csv) | die Kopfzeile der Tabelle ausleih_vorgaenge, für Import CSV | Ablegen |
| [`01_Fall/fall-geraete-ausleihe.pdf`](01_Fall/fall-geraete-ausleihe.pdf) | der Lehr-Fall Geräte-Ausleihe | Vom Prozess zum Bauplan |
| [`01_Fall/fall-geraete-ausleihe-light.pdf`](01_Fall/fall-geraete-ausleihe-light.pdf) | dasselbe, heller Druck | Vom Prozess zum Bauplan |
| [`03_Workflows/ausleihe-m2-stand-ende-modul2.json`](03_Workflows/ausleihe-m2-stand-ende-modul2.json) | Stand der Ausleihe am Ende von Modul 2, zugleich Start von Modul 3 | nach Der Code-Node |
