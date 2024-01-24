### Audio in Text umwandeln (Erklärteil)

Für einen Grossteil der Sitzungen im Jahr 2022 und 2023 waren die Protokolle noch nicht vertextet, sondern pro Intervention während einer Sitzung ein Audiofile abgespeichert.

Entscheidung gegen zwei Automatisierungen:
* Weil die Audiolinks in einer unregelmässig verschachtelten Struktur vorlagen und nicht direkt mit der Seite geladen wurden, habe ich nach einem kurzen Versuch davon abgesehen, mit Selenium einen Sraper zu bauen. In 1.5 Stunden hatte ich alle Links kopiert.
* Ich habe die Audiolinks Whisper jeweils für *eine* Stadtratssitzung geschickt. Für die im Schnitt rund 80 Links brauchte Whisper ca. 1.5 Stunden, zumal er noch die Sprache detektieren musste (DE oder FR); bei schlechter Verbindung gab es immer wieder Unterbrüche, worauf ich den Prozess manuell nochmals ab dem breakpoint starten musste. Hätte ich über alle Files iteriert, wäre die Verbindung ziemlich schnell mal abgebrochen, und ich hätte immer wieder von manuellen breakpoints aus operieren müssen.

Hier ist das Jupyter Notebook, mit dem ich die Whisper API bedient habe, am Beispiel einer Stadtratssitzung.
