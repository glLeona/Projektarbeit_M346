# Tests und Testprotokoll

## Ziel
Nachweis, dass der Service:
- Trigger korrekt ausgeloest wird
- bekannte Persoenlichkeiten erkennt
- JSON korrekt im Out-Bucket speichert
- mehrfach ohne Fehler laeuft (Idempotenz Init, wiederholbare Tests)

## Testumgebung
- Datum/Zeit: 23.12.2025/16:00
- Testperson: Davina
- In-Bucket / Out-Bucket: **[eintragen]**
- Lambda Name: **[eintragen]**

## Testfälle (Tabelle)
| TC | Beschreibung | Input | Erwartet | Resultat | Screenshot | Fazit / Massnahmen |
|---:|---|---|---|---|---|---|
| 1 | Init erfolgreich (idempotent) | `./Scripts/init.sh` (2x) | Keine Fehler, Ressourcen vorhanden | [eintragen] | `screenshots/tc1-init.png` | [eintragen] |
| 2 | Celebrity erkannt | `./Scripts/test.sh <celebrity.jpg>` | JSON im Out-Bucket, Name + Confidence | Erfolgreich | `screenshots/tc2-celebrity.png` | [eintragen] |
| 3 | Keine Celebrity erkannt | `./Scripts/test.sh <unknown.jpg>` | JSON, Celebrities leer, UnrecognizedFaces > 0 | [eintragen] | `screenshots/tc3-unknown.png` | [eintragen] |
| 4 | Mehrfacher Test | TC2 dreimal | Jedes Mal neues JSON + korrekte Ausgabe | [eintragen] | `screenshots/tc4-repeat.png` | [eintragen] |

### Test 1
Testcase: 2

Bei diesem Test wurde ein Bild von Barack Obama hochgeladen. Als Resultat kam diese JSON-Ausgabe:
<img width="530" height="460" alt="image" src="https://github.com/user-attachments/assets/5347d691-41e6-49f7-91fc-8eeb8bd6d91b" />
Diese Person ist nicht Barack Obama.

Status: Nicht erfolgreich

### Test 2
Tstcase: 2

Bei diesem Test wurde erneut ein Bild von Steve Jobs hochgeladen. Als Resultat kam diese JSON-Ausgabe:
<img width="509" height="476" alt="image" src="https://github.com/user-attachments/assets/efab5d20-3a1e-4e8c-bdf6-88c0711449bf" />
Diese Person ist Steve Jobs.

Status: Erfolgreich


Ablage:
- `docs/screenshots/` (Dateinamen gemäss Tabelle)

## Beobachtungen / Erkenntnisse
- **[eintragen]**
