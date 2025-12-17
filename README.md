# Projektarbeit_M346 Face Recognition Tool

## 1. Einleitung

#### 1.1 Projektüberblick

Diese Dokumentation dient zur Dokumentierung der Planung, Umsetzung und Evaluation eines Cloud-Services im Rahmen des Moduls 346 "Cloudlösung konzipieren und realisieren".

#### 1.2 Zielsetzung
Das Hauptziel dieses Projekts ist die erfolgreiche Implementierung eines Cloud-Services, der auf Amazon Web Services (AWS) basiert. Der Service soll die Erkennung von hochgeladenen Promi Fotos ermöglichen und als Rückmeldung den Namen ausgeben. Dies umfasst die Erstellung von AWS-Buckets, die Implementierung von Lambda-Funktionen für die Erkennung sowie die Integration von Infrastructure-as-Code (IaC)-Prinzipien und der Dokumentation über Git in Markdown.

## 2. Projektauftrag

#### 2.1 Ausgangslage

Um die Fertigkeiten mit der Cloud praktisch zu zeigen, findet im letzten Teil vom Modul 346 eine Projektarbeit in Dreiergruppen statt. Die Dreiergruppen können selbständig gewählt werden. Die Note gilt als Gruppennote und zählt doppelt im Modul 346.

#### 2.2 Ziele

Es sollen die folgenden Ziele in der Projektarbeit erreicht werden: 1. Ein Cloud-Service soll automatisch bekannte Persönlichkeiten auf Fotos erkennen. Die Details der Analyse werden dann entsprechend in einer JSON-Datei gespeichert. 2. Der Service soll mit allen erforderlichen Komponenten durch Ausführung eines Scripts von einem Windows oder Linux-Client aus im AWS Learner-Lab in Betrieb genommen werden. 3. Alle für die Inbetriebnahme benötigten Dateien und die zugehörige Dokumentation müssen in einem Git-Repository versioniert abgelegt werden. 4. Eine Markdown Dokumentation die den Aufbau des Services zeigt und die Inbetriebnahme beschreibt soll geschrieben werden. 5. Der Cloud-Service soll getestet werden, wobei alle Testfälle in der Dokumentation dokumentiert und mittels Screenshots protokolliert werden.

#### 2.3 Aufgabenstellung

Richten sie zwei S3 Buckets ein. Ein Eingabebucket für hochgeladene Bilder und ein Ausgabebucket für die Resultate. Wird ein Bild in den Eingabebucket hochgeladen, löst dies eine in C# geschriebene AWS-Lambda-Funktion aus. Diese analysiert das Bild und erkennt darauf enthaltene Personen. Die Analyseergebnis soll anschliessend als JSON-Datei im Ausgabebucket gespeichert werden.

#### 2.4 Planung und Organisation

Nach dem Klären des Projektauftrags werden die Dreiergruppen selbständig gebildet und der Lehrperson bekannt gegeben. Im Unterricht stehen 3x2 Lektionen Zeit zur Verfügung. Erstellen Sie regelmässige Commits in Ihrem Repository und arbeiten Sie in der Gruppe mit einzelnen individuellen UserAccounts vom jeweilig eingesetzten Git-Anbieter. Laden Sie Ihre Lehrperson ebenfalls in das Repository ein. Die Abgabe der Projektarbeit findet über die Angabe des Repositories statt. Nach dem Abgabedatum dürfen keine Änderungen mehr vorgenommen werden. Die Lehrperson beurteilt Ihre Arbeit aufgrund des Repositories, der Commits und der Dokumentation mit Hilfe der nachfolgenden Bewertungskriterien.

## 3. Aufgabeneinteillung

| Aufgabe                   |   Zugeteilt   |  Kommentar  |                                                                                              |
| ------------------------- | --------------| ----------- | -------------------------------------------------------------------------------------------- |
| Dokumentation             | Merve         |             |
| lambda-funktion           | Davina, Leona |             |

## 4. Vorgehen

### 4.1 Projektinitialisierung

#### 4.1.1 Teamzusammensetzung und Rollenverteilung

Die Bildung unseres Dreier-Teams erfolgte nach der Klärung des Projektauftrags. Jedes Teammitglied übernahm spezifische Verantwortlichkeiten, um eine effiziente Zusammenarbeit sicherzustellen.

### 4.2 Umsetzung

#### 4.2.1 AWS-Komponenten erstellen und konfigurieren

Die praktische Umsetzung begann mit der Erstellung und Konfiguration der erforderlichen AWS-Komponenten. Dies umfasste die Einrichtung von Buckets auf Amazon S3 sowie die Implementierung von Lambda-Funktionen für die Gesichtserkennung. 
<img width="1020" height="134" alt="image" src="https://github.com/user-attachments/assets/5986f60b-98f4-454a-8f75-089b0e457411" />
Ebenfalls wurde ein Github-Repository für den programmierten C# Code und die Markdown Dokumentation erstellt.

#### 4.2.2 Programmierung der Gesichtserkennung

Die Programmierung der Gesichtserkennugsfunktionalität erfolgte unter Verwendnung von C# in Visual Studio. Der Code wurde so gestaltet, das er genügend Kommentare fürs Verständnis erhält.
