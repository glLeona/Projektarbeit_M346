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
| TC | Beschreibung | Input | Erwartet | Resultat | Fazit / Massnahmen |
|---:|---|---|---|---|---|
| 1 | Init erfolgreich (idempotent) | `./Scripts/init.sh` (2x) | Keine Fehler, Ressourcen vorhanden | Erfolgreich | init.sh funktioniert erfolgreich |
| 2 | Celebrity erkannt | `./Scripts/test.sh <celebrity.jpg>` | JSON im Out-Bucket, Name + Confidence | Erfolgreich | Celebrity wurde zuerst nicht erkannt, später schon |
| 3 | Keine Celebrity erkannt | `./Scripts/test.sh <unknown.jpg>` | JSON, Celebrities leer, UnrecognizedFaces > 0 | Erfolgreich | Test war erfolgreich |
| 4 | Mehrfacher Test | TC2 dreimal | Jedes Mal neues JSON + korrekte Ausgabe | Erfolgreich | Neues JSON wurde jedesmal neu erstellt mit korrekter Ausgabe |

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

## Test 3
Testcase: 3

Bei diesem Test wurde ein Bild von einem Hund hochgeladen. Als Resultat kamm diese JSON-Ausgabe:
<img width="693" height="241" alt="image" src="https://github.com/user-attachments/assets/2a4d22c5-f0a8-41e0-9265-5feb834c5f67" />


Status: Erfolgreich

## Test 4
Testcase: 1

Bei diesem Test wurde getestet, ob das init.sh erfolgreich durchgeführt wird:
<img width="745" height="320" alt="image" src="https://github.com/user-attachments/assets/f82531ac-f6a1-4e1c-b0d3-b69e3bac4109" />


Status: Erfolgreich

## Beobachtungen / Erkenntnisse
Als erstes hat die Celebrity-Erkennung nicht funktioniert und es kam statt Barack Obama, Madelyn Dunham. Als wir es ein paar Minuten später nochmals versucht haben, kam die richtige Ausgabe. 
