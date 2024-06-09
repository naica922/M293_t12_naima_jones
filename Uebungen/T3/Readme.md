### T3 Übungen

## Übung 1 - Requests und Responses analysieren
Öffnen sie eine beliebige Seite (z.B. https://www.tbz.ch) und verwenden sie die DevTools (im Netzwerk-Reiter), um die verschiedenen Requests zu analysieren. Sie können die verschiedenen Request-Typen (z.B. Dokument, JS, CSS, etc) auch filtern.
Schauen sie sich von verschiedenen Typen, sowohl die Requests als auch die Responses und dann jeweils den Header und den Body. Forschen sie nach, wenn etwas unklar ist.
Vergleichen sie die Header, speziell die Inhaltstypen.

Request Header: Accept: text/html
Response Header: Content-Type: text/html
Body: HTML-Dokument

Request Header: Accept: text/css
Response Header: Content-Type: text/css
Body: CSS-Styles

## Übung 2 - Port
Ändern sie den Port einer URL manuell. Versuchen sie die Standard-Ports zusätzlich anzugeben. Anschliessend versuchen sie einen anderen beliebigen Port. Was geschieht?

Wenn ich https://www.tbz.ch:443 angebe, ladet die Seite normal aber wenn ich https://www.tbz.ch:80 anfgebe geht es nicht auch https://www.tbz.ch:8080 funktioniert nicht

## Übung 3 - Anker
Auf dieser Gitlab-Seite gibt es viele Anker. Schaffen sie es die URL so zu ändern, dass sie direkt zu den Übungen springen?
TIPP: Die Anker sind in den Titel gesetzt.

## Übung 4 - POST vs GET
Rufen sie dieses Formular auf und starten sie die DevTools. Tätigen sie folgende Einstellungen
Laden sie nun die Seite neu
Schicken sie das Formular ab, damit sie einen zweiten Eintrag im Netzwerk-Reiter sehen.

Tasks:
Analysieren sie die beiden Requests. Ein GET-Request, welcher das Formular liest. Ein POST-Request, welcher die Formular-Daten an den Server schickt und eine Antwort erhält.
Was ist die Antwort im Post-Request?
Drücken sie nun F5, was die Seite neu lädt. Sie kriegen eine Bestätigungsnachricht. Was bedeutet diese?
Was bedeutet die Einstellung "Preserve log", die wir in den DevTools gemacht haben? Testen sie den Unterschied.
Was bedeutet die Einstellung "Doc", die wir in den DevTools (unter Filter) gemacht haben? Testen sie den Unterschied und aktivieren sie wieder "All".

Die Antwort im POST-Request könnte z.B. eine Bestätigungsmeldung oder die Daten sein.
Die Bestätigungsnachricht nach F5 zeigt an, dass die Seite die Daten erneut senden will. A
Das passiert, weil der Browser versucht, den letzten Vorgang (den POST-Request) zu wiederholen.
Die Einstellung "Preserve log" in den DevTools bewirkt, dass die Netzwerkaktivitäten im Log erhalten bleiben, auch wenn die Seite neu geladen wird. Ohne diese Einstellung werden die Log-Einträge bei jedem Neuladen gelöscht.
Die Einstellung "Doc" filtert die angezeigten Netzwerkaktivitäten, sodass nur Dokument-Requests angezeigt werden.