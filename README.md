# Projektarbeit_M346 Face Recognition Tool

## Inhaltsverzeichnis
1. [Einleitung](#1-einleitung)  
   1.1 [Projektüberblick](#11-projektüberblick)  
   1.2 [Zielsetzung](#12-zielsetzung)  
2. [Projektauftrag](#2-projektauftrag)  
   2.1 [Ausgangslage](#21-ausgangslage)  
   2.2 [Ziele](#22-ziele)  
   2.3 [Aufgabenstellung](#23-aufgabenstellung)  
   2.4 [Planung und Organisation](#24-planung-und-organisation)  
3. [Aufgabeneinteillung](#3-aufgabeneinteillung)  
4. [Vorgehen](#4-vorgehen)  
   4.1 [Projektinitialisierung](#41-projektinitialisierung)  
       4.1.1 [Teamzusammensetzung und Rollenverteilung](#411-teamzusammensetzung-und-rollenverteilung)  
   4.2 [Umsetzung](#42-umsetzung)  
       4.2.1 [AWS-Komponenten erstellen und konfigurieren](#421-aws-komponenten-erstellen-und-konfigurieren)  
       4.2.2 [Gesamtaufbau](#422-gesamtaufbau)  
       4.2.3 [Programmierung der Gesichtserkennung](#423-programmierung-der-gesichtserkennung)  
   4.3 [Dokumentation](#44-dokumentation)  
       4.3.1 [Strukturierung der Dokumentation](#441-strukturierung-der-dokumentation)  
       4.3.2 [Regelmässige Commits und Git-Nutzung](#442-regelmässige-commits-und-git-nutzung)  
   4.4 [Testdurchführung](#45-testdurchführung)  
       4.4.1 [Definition von Testfällen](#451-definition-von-testfällen)  
       4.4.2 [Durchführung der Tests und Protokollierung](#452-durchführung-der-tests-und-protokollierung)  
5. [Tests](#5-tests)
   5.1 [Testcase 1](#51-testcase-1)
   5.2 [Testcase 2](#52-testcase-2)
7. [Reflexion](#6-reflexion)  
   6.1 [Reflexion Davina](#61-reflexion-davina)  
   6.2 [Reflexion Leona](#62-reflexion-leona)  
   6.3 [Reflexion Merve](#63-reflexion-merve)  
8. [Anhang](#7-anhang)  
9. [Test Case](#8-test-case)  
10. [Quellen](#9-quellen)
   

## 1. Einleitung

#### 1.1. Projektüberblick

Diese Dokumentation dient zur Dokumentierung der Planung, Umsetzung und Evaluation eines Cloud-Services im Rahmen des Moduls 346 "Cloudlösung konzipieren und realisieren".

#### 1.2. Zielsetzung
Das Hauptziel dieses Projekts ist die erfolgreiche Implementierung eines Cloud-Services, der auf Amazon Web Services (AWS) basiert. Der Service soll die Erkennung von hochgeladenen Promi Fotos ermöglichen und als Rückmeldung den Namen ausgeben. Dies umfasst die Erstellung von AWS-Buckets, die Implementierung von Lambda-Funktionen für die Erkennung sowie die Integration von Infrastructure-as-Code (IaC)-Prinzipien und der Dokumentation über Git in Markdown.

## 2. Projektauftrag

#### 2.1. Ausgangslage

Um die Fertigkeiten mit der Cloud praktisch zu zeigen, findet im letzten Teil vom Modul 346 eine Projektarbeit in Dreiergruppen statt. Die Dreiergruppen können selbständig gewählt werden. Die Note gilt als Gruppennote und zählt doppelt im Modul 346.

#### 2.2. Ziele

Es sollen die folgenden Ziele in der Projektarbeit erreicht werden: 1. Ein Cloud-Service soll automatisch bekannte Persönlichkeiten auf Fotos erkennen. Die Details der Analyse werden dann entsprechend in einer JSON-Datei gespeichert. 2. Der Service soll mit allen erforderlichen Komponenten durch Ausführung eines Scripts von einem Windows oder Linux-Client aus im AWS Learner-Lab in Betrieb genommen werden. 3. Alle für die Inbetriebnahme benötigten Dateien und die zugehörige Dokumentation müssen in einem Git-Repository versioniert abgelegt werden. 4. Eine Markdown Dokumentation die den Aufbau des Services zeigt und die Inbetriebnahme beschreibt soll geschrieben werden. 5. Der Cloud-Service soll getestet werden, wobei alle Testfälle in der Dokumentation dokumentiert und mittels Screenshots protokolliert werden.

#### 2.3. Aufgabenstellung

Richten sie zwei S3 Buckets ein. Ein Eingabebucket für hochgeladene Bilder und ein Ausgabebucket für die Resultate. Wird ein Bild in den Eingabebucket hochgeladen, löst dies eine in C# geschriebene AWS-Lambda-Funktion aus. Diese analysiert das Bild und erkennt darauf enthaltene Personen. Die Analyseergebnis soll anschliessend als JSON-Datei im Ausgabebucket gespeichert werden.

#### 2.4. Planung und Organisation

Nach dem Klären des Projektauftrags werden die Dreiergruppen selbständig gebildet und der Lehrperson bekannt gegeben. Im Unterricht stehen 3x2 Lektionen Zeit zur Verfügung. Erstellen Sie regelmässige Commits in Ihrem Repository und arbeiten Sie in der Gruppe mit einzelnen individuellen UserAccounts vom jeweilig eingesetzten Git-Anbieter. Laden Sie Ihre Lehrperson ebenfalls in das Repository ein. Die Abgabe der Projektarbeit findet über die Angabe des Repositories statt. Nach dem Abgabedatum dürfen keine Änderungen mehr vorgenommen werden. Die Lehrperson beurteilt Ihre Arbeit aufgrund des Repositories, der Commits und der Dokumentation mit Hilfe der nachfolgenden Bewertungskriterien.

## 3. Aufgabeneinteillung

| Aufgabe                                                        |        Zugeteilt           |
| ---------------------------------------------------------------|--------------------------- |
| Dokumentation, Struktur, Programmier-Unterstützung             | Merve                      |
| lambda-funktion, Testing, Script                               | Davina, Leona              |

## 4. Vorgehen

### 4.1. Projektinitialisierung

#### 4.1.1. Teamzusammensetzung und Rollenverteilung

Die Bildung unseres Dreier-Teams erfolgte nach der Klärung des Projektauftrags. Jedes Teammitglied übernahm spezifische Verantwortlichkeiten, um eine effiziente Zusammenarbeit sicherzustellen.

### 4.2. Umsetzung

#### 4.2.1. AWS-Komponenten erstellen und konfigurieren

Die praktische Umsetzung begann mit der Erstellung und Konfiguration der erforderlichen AWS-Komponenten. Dies umfasste die Einrichtung von Buckets auf Amazon S3 sowie die Implementierung von Lambda-Funktionen für die Gesichtserkennung. 
<img width="1020" height="134" alt="image" src="https://github.com/user-attachments/assets/5986f60b-98f4-454a-8f75-089b0e457411" />
Ebenfalls wurde ein Github-Repository für den programmierten C# Code und die Markdown Dokumentation erstellt.

#### 4.2.2. Gesamtaufbau
```
┌─────────────┐      ┌──────────────┐      ┌─────────────────┐
│   Benutzer  │─────▶│  S3 In-Bucket │─────▶│ Lambda Funktion │
│  (Aufladen) │      │              │      │  (C# .NET 8)    │
└─────────────┘      └──────────────┘      └─────────────────┘
                            │                       │
                            │                       ▼
                            │              ┌─────────────────┐
                            │              │ AWS Erkennung   │
                            │              │(bekannte Person)│
                            │              └─────────────────┘
                            │                       │
                            ▼                       ▼
                     ┌──────────────┐      ┌────────────────┐
                     │ S3 Out-Bucket │◀─────│ JSON Resultat  │
                     └──────────────┘      └────────────────┘
```

#### 4.2.3. Programmierung der Gesichtserkennung

Die Programmierung der Gesichtserkennugsfunktionalität erfolgte unter Verwendnung von C# in Visual Studio. Der Code wurde so gestaltet, das er genügend Kommentare fürs Verständnis erhält.
Der unten gezeigte C# Code ist eine AWS Lambda-Funktion, die auf ein S3 Event reagiert:

```
public async Task<string?> FunctionHandler(S3Event evnt, ILambdaContext context)
{
    var s3Event = evnt.Records?[0].S3;
    if(s3Event == null)
    {
        return null;
    }

    try
    {
        var response = await this.S3Client.GetObjectMetadataAsync(s3Event.Bucket.Name, s3Event.Object.Key);
        return response.Headers.ContentType;
    }
    catch(Exception e)
    {
        context.Logger.LogInformation($"Error getting object {s3Event.Object.Key} from bucket {s3Event.Bucket.Name}. Make sure they exist and your bucket is in the same region as this function.");
        context.Logger.LogInformation(e.Message);
        context.Logger.LogInformation(e.StackTrace);
        throw;
    }
}
```

## 4.4. Dokumentation

### 4.4.1. Strukturierung der Dokumentation

Die Dokumentation wurde gemäss den Vorgaben in Markdown geschrieben. Die Struktur folgt den Leitfragen und Gütestufen des Projektauftrags, um eine klare und nachvollziehbare Dokumentation zu gewähleisten.

### 4.4.2. Regelmässige Commits und Git-Nutzung

Um eine effiziente Zusammenarbeit sicherzustellen, wurden regelmässig Commits im Git-Repository durchgeführt. Jede Person hat nach Angabe minimal einen Commit gemacht, sei es beim Programmieren oder beim Schreiben der Dokumentation. Die Git-Nutzung erstreckte sich über die gesamte Projektdauer.

## 4.5. Testdurchführung

### 4.5.1. Definition von Testfällen

Vor der Testdurchführung wurden klare Testfälle definiert, um die Funktionalität und Performance des Services sicherzustellen.

### 4.5.2. Durchführung der Tests und Protokollierung

Die Tests wurden durchgeführt und mittels Screenshots dokumentiert. Das Testprotokoll enthält Informationen zu Testzeitpunkten, Testpersonen und bietet aussagekräftige Fazits zu den Testergebnissen.

## 5. Tests
In diesem Projekt wurden verschiedene Tests durchgeführt, um sicherzustellen, dass die implementierte Cloudlösung den definierten Anforderungen entspricht. Die Tests umfassen sowohl manuelle als auch automatisierte Prüfungen, um die Zuverlässigkeit, Sicherheit und Funktionalität der Lösung sicherzustellen.

### 5.1 Testcase 1

| Test Nr.    | Name           | Tester    |
|:-----------:|:--------------:|:---------:|
| T1          | Barack Obama   | Davina    |

Testdatum: 22. Dezember 2025
Testperson: Davina
Testumgebung: AWS Learner Lab

Ablauf:

- Bild von Obama hochgeladen
- Fehlermeldung kam:

Fehlermeldung Cloud Shell:
```
fatal error: An error occurred (404) when calling the HeadObject operation: Key "Test.jpg.json" does not exist
```

Fehlermeldung Cloud Watch:
```
Error: .NET binaries for Lambda function are not correctly installed in the /var/task directory of the image when the image was built. The /var/task directory is missing the required .deps.json file.
```
Status: Nicht erfolgreich
Bemerkungen: Es gibt keine JSON-Datei zurück.

### 5.2 Testcase 2

| Test Nr.    | Name           | Tester    |
|:-----------:|:--------------:|:---------:|
| T2          | Script         | Davina    |

Testdatum: 22. Dezember 2025
Testperson: Davina
Testumgebung: AWS Learner Lab

Status:
Das Skript kann ausgeführt werden, jedoch kommt keine JSON-Datei am Ende.

## 6. Reflexion

#### 6.1. Reflexion Davina

##### Lernerfahrung:
Bei diesem Projekt habe ich gelernt, wie Gesichtserkennung mit AWS Rekognition funktioniert und wie ein technischer Ablauf von der Bilderfassung bis zur Auswertung aufgebaut ist. Da keine Dokumentation zur Verfügung gestellt wurde, musste ich mir die benötigten Informationen selbstständig aus dem Internet zusammensuchen. Dies war teilweise anspruchsvoll, hat mir jedoch geholfen, meine Recherchefähigkeiten zu verbessern und technische Inhalte besser zu verstehen. Außerdem konnte ich mein Wissen über cloudbasierte Services und deren Einsatz im Bereich der Gesichtserkennung erweitern.

##### Zusammenarbeit:
Die Zusammenarbeit in der Gruppe war gut. Wir haben die Aufgaben klar aufgeteilt, wobei ein Teil der Gruppe für die praktische Umsetzung mit AWS Rekognition zuständig war und der andere Teil für die Dokumentation. Trotz dieser Aufteilung haben wir uns regelmässig ausgetauscht, Zwischenergebnisse überprüft und uns gegenseitig unterstützt. So konnten wir sicherstellen, dass sowohl die praktische Arbeit als auch die Dokumentation korrekt und verständlich umgesetzt wurden.

##### Zeitdruck und Herausforderung:
Zu Beginn des Projekts gab es einige Schwierigkeiten, da zunächst unklar war, wie AWS Rekognition genau funktioniert und welche Schritte notwendig sind, um die Aufgabe umzusetzen. Da keine Dokumentation vorhanden war, musste erst recherchiert und ausprobiert werden, was viel Zeit in Anspruch nahm. Dadurch entstand zusätzlicher Zeitdruck, was teilweise stressig war. Mit zunehmendem Verständnis und durch den Austausch im Team wurde die Vorgehensweise jedoch klarer. So konnten die Aufgaben strukturierter bearbeitet und Probleme gemeinsam gelöst werden, was den Arbeitsprozess deutlich erleichtert hat.

#### 6.2. Reflexion Leona

##### Lernerfahrung:

##### Zusammenarbeit:

##### Zeitdruck und Herausforderung:

#### 6.3. Reflexion Merve

##### Lernerfahrung:
Das Projekt hat meine Kenntnisse in Cloud-Technologien, insbesondere AWS, erweitert. Ich habe gelernt, wie man effizient S3-Buckets einrichtet, Lambda-Funktionen konfiguriert und CloudFormation für die automatisierte Bereitstellung verwendet. Obwohl ich mich mehrheitlich mit der Dokumentation beschäftigt habe, habe ich trotzdem vieles zur Verknüpfung der einzelnen Komponente in AWS gelernt. Ich hätte es noch gut gefunden, wenn wir im Unterricht ähnliche Aufgabenstellungen erhalten hätten, damit wir beim ersten Anblick nicht schokiert wären und direkt mit der Umsetzung beginnen könnten.

##### Zusammenarbeit:
Die Zusammenarbeit fand ich gut. Wir hatten keine Unklarheiten, wer was machen sollte, da wir es im vorhinein gut abgesprochen hatten. Natürlich haben wir uns gegenseitig immer unterstützt.

##### Zeitdruck und Herausforderung:
Am Anfang dachten wir, dass wir genügend Zeit haben, weshalb wir uns nicht gestresst gefühlt haben. Im Laufe des Projekts kamen dann Schwierigkeiten und wir verloren somit Zeit bei der Programmierung als auch der Dokumentation. Am Ende kamen wir dann ins Stress und merkten, dass wir uns von Anfang an deutlich mehr mit dem Thema hätten befassen sollen.

## 7. Anhang

## 9. Quellen
