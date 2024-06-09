# HTTP-Protokoll

## Lernziele
- Ich kann erläutern für was die Abkürzung HTTP steht und wofür es entwickelt wurde.
- Ich kann die Bestandteile einer URL zerlegen und benennen.
- Ich kann einen Seiten-Aufruf mit Request und Response erklären.
- Ich kann die Bestandteile einer HTTP-Anfrage benennen.
- Ich kann die Bestandteile einer HTTP-Antwort benennen.
- Ich kann fünf verschiedene Übertragungs-Methoden nennen und den Unterschied von GET und POST erklären.
- Ich kann die Standard-Ports eines Webservers nennen.
- Ich kann die wichtigsten Status Codes erklären.
- Ich kann den korrekten Content-Type von Requests und Responses evaluieren und setzen.

## URL (Uniform Resource Locator)
Dient dazu, Ressource eindeutig zu kennzeichnen und zu addressieren. <br>
Aufbau:
![Aufbau url](url.png)

Schema:<br>
ist notwendig, kennzeichnet Protokoll
http, https, mailto, ftp und andere möglich
nach Protokoll kommt "://" welche Protokoll von Domäne trennt

Domäne:<br>
Kann alternativ auch IP stehen, da Domäne Alias für IP ist

Port:<br>
nicht angegeben
standartmässig 80 für http, 443 für https 
Auch möglich, dass Webserver anderen Port verwendet, dann muss er angegeben werden

Pfad:<br>
Alle Dateien in Ordnerstruktur abgelegt, mit Pfad navigieren zu der entsprechenden Datei
HTML Dateien haben .html oder .htm$
Andere auch möglich, speziell für dynamische Seiten
Wenn Dateiname beim Pfad weggelassen wird automatisch index.html geliefert
Bei dynamischen Applikationen stammt Pfad in URL oft nicht mit Dateiablage auf dem Server überein

Argumente:<br>
Ein Weg, Daten an Server zu übermitteln
Server muss so eingerichtet sein, dass Daten auch empfangen werden wenn nicht werden Daten ignoriert
Argumente immer in Key Value Pairs übertragen, werden mit & getrennt
? kennzeichnet Start der Argumente

Anker:<br>
wird mit dem a Tag gesetzt
Wenn Anker in URL angehängt, springt Seite direkt zum Anker
Anker hat immer das Zeichen # vorne

## Geschichte HTTP
Entwicklung von Hypertext Transfer Protocol eng mit entwickling von Hypertext Markup Language zusammen. HTTP bezeichnet Protokoll, HTML bezeichnet Dokument also Inhalt
- 1989: HTTP mit HTML und Konzept von URLs entwickelt
- 1996: HTTP 1.0 publiziert, Schwachstelle ist das jedes Objekt neue Verbindung benötigt und Verbindungsaufbau langsam
- 1999: HTTP 1.1 zusammen mit HTML eingeführt und Verbingsungsprobleme gelöst, auch Daten senden nicht nur empfangen
- 2015: mehrere Anfragen zusammenfassen, Antwortzeiten kürzer und zusätzliche Erweiterungen
- 2018: noch nicht published

## Funktion HTTP
### TCP Kommunikation
Auf TCP aufgebaut, verwendet Kommunikationsmodell mit Requests und Responses
Jeder request und Response sendet Nachrichten mit Header und Body
![TCP Kommunikation](TCP.png)

### HTTP Kommunikation
Applikationsschicht, definiert welche Inhalte Nachrichten haben
Header: <br>
Protokoll Informationen und HTTP Header 
Nachrichten Header von TCP entspricht nicht dem HTTP header aber HTTP Header ist Teil des Nachrichten headers
![HTTP Kommunikation](HTTP.png)

### HTTP Request
![HTTP Request](BestandteileRequest.png)

### HTTP Response
![HTTP Response](BestandteileResponse.png)

### Status Code
In jeder response vorhanden, sagt aus ob Anfrage erfolgreich war oder nicht
200 OK: Anfrage erfolgreich <br>
404 Not Found: Ressource nicht gefunden (falscher Pfad?) <br>
500 Internal Server Error: Bei dynamischen Seiten welche Fehler werfen<br>

### Headers
Viele Headers für requests und reponses und auch inoffizielle

Request Headers:<br>
- accept: Eine komma-separierte Liste mit Inhalten, die der Client akzeptieren wird, z.B. "text/html;q=0.9,image/avif,image/webp,image/apng,/;q=0.8,application/signed-exchange;v=b3;q=0.9"
- accept-encoding: Codierung und Verschlüsselung, z.B. "gzip, deflate, br"
- accept-language: Liste von Sprachen, z.B. "en-US,en;q=0.9,de;q=0.8"
- cache-control:  Caching (Zwischenspeicher)-Regeln, z.B. "max-age=0"
- content-length: Länge des Inhalts in bytes, falls einer mitgeschickt wird, z.B. "34"
- content-type: Typ des Inhalts, falls einer mitgeschickt wird, z.B. "application/x-www-form-urlencoded"
- cookie: Alle cookies, die gesetzt sind, z.B. "_ga=GA1.2.699450697.1631599704; _gid=GA1.2.719813276.1640619849; _gat=1"
- Referer: Welche URL auf diese Seite weitergeleitet hat, falls weitergeleitet wurde, z.B. "https://www.tbz.ch"
- user-agent: Eine Zeichenkette, die den Client identifiziert, z.B. "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36"

Response Headers:<br>
- cache-control: Anweisung an den Client/Browser wie die Seite mit dem Cache umgehen soll, z.B. "no-cache, no-store, max-age=0, must-revalidate"
- content-encoding: Kompressionstyp, der verwendet wurde, z.B. "br"
- content-type: Inhaltstyp und Textcodierung, der geschickt wird, z.B. "text/html; charset=UTF-8"
- ate: Datum der Antwort, z.B. "Mon, 27 Dec 2021 15:44:21 GMT"
- expires: Datum an dem der Inhalt nicht mehr gültig ist. Wird oft auf das gleiche Datum gesetzt, wie der Header date, damit nichts im Cache gespeichert wird, z.B. "Mon, 27 Dec 2021 15:44:21 GMT"

### Request Methoden
Oft auch als Verb bezeichnet, ist ein Set von Methoden welche bei Anfragen verwendet werden
Methoden werden auf Seite vom Server gesteuert
Client kann jede URL mit beleibigen Methode aufrufen aber server antwortet nicht auf alle

GET: Daten nur in der URL übermitteln, Body ist leer
POST: Sendet Daten an Server, Request Body verwendet 
PUT: Beim erstellen oder aktualisieren verwendet, Request Body wird mitgegeben
DELETE: Objekt löschen, request body leer, response body kann inhalt haben
OPTIONS: um herauszufinden welche Methoden URL unterstützt, Request und Response body leer
HEAD: Wenn nur Header Informationen gewollt, Request und Response Body leer

### Inhaltstypen (Content Type)
![ContentType](Inhaltstypen.png)

### HTTPS (Hypertext Transfer Protocol Secure)
basiert auf HTTP und erweitert Protokoll um Sicherheitsschicht, erlaubt es Daten mit TLS und SSL verschlüsslung zu erweitern

