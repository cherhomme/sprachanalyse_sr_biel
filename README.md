# sprachanalyse_sr_biel

*Welche Themen haben in den letzten 25 Jahren im Bieler Stadtrat viel zu reden gegeben? Wann hatten sie Konjunktur, wann sind sie wieder verschwunden? Um diese Frage zu beantworten, habe ich die Stadtratprotokolle 1999-2023 analysiert.*

## Vorgehen

### Daten beschaffen
Da die neuesten Protokolle nur als Audio-Aufnahmen verfügbar sind, die Protokolle vor 2002 nur in Papierform, wurde die Beschaffung der Daten in drei Schritte aufgeteilt:

* Die Protokolle von 2002-2021 sind alle als PDFs verfügbar. Die Stadtkanzlei hat sie mir per Mail / Webtransfer übermittelt. Danach habe ich mit der fitz-Python-Library mit folgendem [Code](url) Text aus den PDFs extrahiert.
* Die Protokolle von 1999-2001 sind ausschliesslich auf Papier verfügbar. Ich habe sie im Stadtarchiv abfotografiert und mit tesseract den Text aus den Fotos extrahiert.
* Ein Teil der Protokolle von 2022 und 2023 ist erst in Form von Audiofiles verfügbar. Ich habe die Audiofiles über die API von Whisper vertextet.

Die Codes zur Datenbeschaffung: ([sprachanalyse_sr_biel/Text beschaffen/](https://github.com/cherhomme/sprachanalyse_sr_biel/tree/main/Text%20beschaffen)).

#### Datenanalyse: Gescheiterte und geglückte Analysemethoden



**Text aus PDFs**
