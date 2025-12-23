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
       4.2.1 [Architektur](#421-architektur)  
       4.2.2 [Voraussetzungen (Client)](#422-voraussetzungen-(client))  
       4.2.3 [Quickstart (vollautomatisiert)](#423-quickstart-(vollautomatisiert))
       4.2.4 [Konfiguration (optional per ENV)](#424-konfiguration-(optional-per-env))
       4.2.5 [Ergebnisformat (JSON)](#425-ergebnisformat-(json))
       4.2.6 [Repository-Inhalt](#426-repository-inhalt)
6. [Dokumentation](#44-dokumentation)  
   5.1 [Strukturierung der Dokumentation](#441-strukturierung-der-dokumentation)  
   5.2 [Regelmässige Commits und Git-Nutzung](#442-regelmässige-commits-und-git-nutzung)  
7. [Tests und Protokolle](#45-tests-und-protokolle)  
8. [Reflexion](#6-reflexion)   
9. [Anhang](#7-anhang)
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

Ein FaceRecognition-Service erkennt bekannte Persoenlichkeiten auf Fotos, die in ein S3 In-Bucket hochgeladen werden. Eine AWS Lambda Funktion wird per S3 Trigger ausgeloest, ruft AWS Rekognition (RecognizeCelebrities) auf und speichert die Analyse als JSON in einem S3 Out-Bucket.

#### 2.3. Aufgabenstellung

Richten sie zwei S3 Buckets ein. Ein Eingabebucket für hochgeladene Bilder und ein Ausgabebucket für die Resultate. Wird ein Bild in den Eingabebucket hochgeladen, löst dies eine in C# geschriebene AWS-Lambda-Funktion aus. Diese analysiert das Bild und erkennt darauf enthaltene Personen. Die Analyseergebnis soll anschliessend als JSON-Datei im Ausgabebucket gespeichert werden.

#### 2.4. Planung und Organisation

Nach dem Klären des Projektauftrags werden die Dreiergruppen selbständig gebildet und der Lehrperson bekannt gegeben. Im Unterricht stehen 3x2 Lektionen Zeit zur Verfügung. Erstellen Sie regelmässige Commits in Ihrem Repository und arbeiten Sie in der Gruppe mit einzelnen individuellen UserAccounts vom jeweilig eingesetzten Git-Anbieter. Laden Sie Ihre Lehrperson ebenfalls in das Repository ein. Die Abgabe der Projektarbeit findet über die Angabe des Repositories statt. Nach dem Abgabedatum dürfen keine Änderungen mehr vorgenommen werden. Die Lehrperson beurteilt Ihre Arbeit aufgrund des Repositories, der Commits und der Dokumentation mit Hilfe der nachfolgenden Bewertungskriterien.

## 3. Aufgabeneinteilung

| Aufgabe                                                        |        Zugeteilt           |
| ---------------------------------------------------------------|--------------------------- |
| Dokumentation, Struktur, Programmier-Unterstützung             | Merve                      |
| Lambda-Funktion, Testing, Script                               | Davina, Leona              |

## 4. Vorgehen

### 4.1. Projektinitialisierung

#### 4.1.1. Teamzusammensetzung und Rollenverteilung

Die Bildung unseres Dreier-Teams erfolgte nach der Klärung des Projektauftrags. Jedes Teammitglied übernahm spezifische Verantwortlichkeiten, um eine effiziente Zusammenarbeit sicherzustellen.

### 4.2. Umsetzung

#### 4.2.1. Architektur

- S3 In-BUcket: Upload von JPG/PNG
- Lambda (C# / .NET 8): Verarbeitung + Rekognition
- S3 Out-Bucket: JSON-Resultat pro Bild

Siehe: docs/architecture.md

#### 4.2.2. Voraussetzungen (Client)

- AWS Learner Lab Credentials in der Shell aktiv (AWS CLI v2 muss funktionieren)
  - Test: aws sts get-caller-identify
- dotnet SDK 8
- Git geklont > git clone https://github.com/glLeona/Projektarbeit_M346.git
- Bild-Datei (nur für test.sh)

Windows:
- via WSL oder Git Bash

#### 4.2.3. Quickstart (vollautomatisiert)
```
chmod +x Scripts/init.sh Scripts/test.sh
./Scripts/init.sh
./Scripts/test.sh <pfad/zum/bild.jpg>
```

#### 4.2.4. Konfiguration (optional per ENV)
```
export AWS_REGION="eu-central-1"
export PROJECT_PREFIX="m346-facerec"
export IN_BUCKET="m346-facerec-<account>-in"
export OUT_BUCKET="m346-facerec-<account>-out"
export LAMBDA_NAME="m346-facerec-lambda"
```

#### 4.2.5. Ergebnisformat (JSON)

Die Lambda-Funktion schreibt eine JSON-Datei mit unter anderem:
- SourceImage.Bucket, SourceImage.Key
- Celebrities[]: Name, MatchConfidence, Id, Urls
- UnrecognizedFaces
- ProcessedAtUtc

Beispiel-Ausgabe (gekürzt):
```
{
  "SourceImage": { "Bucket": "…", "Key": "…" },
  "Celebrities": [
    { "Name": "…", "MatchConfidence": 99.9, "Id": "…", "Urls": ["…"] }
  ],
  "UnrecognizedFaces": 0,
  "ProcessedAtUtc": "2025-12-23T00:00:00Z"
}
```
#### 4.2.6. Repository-Inhalt

- Function.cs – Lambda Handler (gegeben, unveraendert)
- Scripts/init.sh – vollautomatische Inbetriebnahme (idempotent)
- Scripts/test.sh – vollautomatischer Test inkl. JSON Download + Output
- infra/ – IAM Trust + Policy Template + generiertes S3 Notification JSON
- docs/ – Dokumentation (Architektur, Tests, Reflexion)
  
## 5. Dokumentation

### 5.1. Strukturierung der Dokumentation

Die Dokumentation wurde gemäss den Vorgaben in Markdown geschrieben. Die Struktur folgt den Leitfragen und Gütestufen des Projektauftrags, um eine klare und nachvollziehbare Dokumentation zu gewähleisten.

### 5.2. Regelmässige Commits und Git-Nutzung

Um eine effiziente Zusammenarbeit sicherzustellen, wurden regelmässig Commits im Git-Repository durchgeführt. Jede Person hat nach Angabe minimal einen Commit gemacht, sei es beim Programmieren oder beim Schreiben der Dokumentation. Die Git-Nutzung erstreckte sich über die gesamte Projektdauer.

## 6. Tests und Protokolle

- Testfälle + Screenshots: docs/tests.md

## 7. Reflexion

- Reflexion pro Teammitglied: docs/reflection.md

## 8. Quellen
Amazon Web [What is Amazon EC2](https://www.w3schools.com/whatis/whatis_aws_ec2.asp) 23.12.2025

Markdown Guide [Getting Started | Markdown Guide](https://www.markdownguide.org/getting-started/) 23.12.2025
