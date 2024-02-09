# sprachanalyse_sr_biel

*Welche Themen haben in den letzten 25 Jahren im Bieler Stadtrat viel zu reden gegeben? Wann hatten sie Konjunktur, wann sind sie wieder verschwunden? Um diese Frage zu beantworten, habe ich die Stadtratprotokolle 1999-2023 analysiert.*

## Vorgehen

### Daten beschaffen
Da die neuesten Protokolle nur als Audio-Aufnahmen verfügbar sind, die Protokolle vor 2002 nur in Papierform, wurde die Beschaffung der Daten in drei Schritte aufgeteilt:

* Die Protokolle von 2002-2021 sind alle als PDFs verfügbar. Die Stadtkanzlei hat sie mir per Mail / Webtransfer übermittelt. Danach habe ich mit der fitz-Python-Library mit diesem Code [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Text%20beschaffen/PDF-Protokolle%20extrahieren.ipynb] Text aus den PDFs extrahiert.
* Die Protokolle von 1999-2001 sind ausschliesslich auf Papier verfügbar. Ich habe sie im Stadtarchiv abfotografiert und mit tesseract den Text aus den Fotos extrahiert. Hier ist die command-line-Zeile sowie der Python-Code, um die einzelnen Seiten zu ganzen Textfiles zusammenzuführen [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Text%20beschaffen/Text%20aus%20Bildern%20herausholen.md].
* Ein Teil der Protokolle von 2022 und 2023 ist erst in Form von Audiofiles verfügbar. Ich habe die Audiofiles über die API von Whisper mit folgendem iPython-Skript [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Text%20beschaffen/Audio_to_text.ipynb] vertextet.

### Datenanalyse: Gescheiterte und geglückte Analysemethoden

Ursprünglicher Plan: Mit nltk die Textstrings tokenisieren, dann mit spacy und den vortrainierten deutschen und französischen Modellen die Token stemmen und dann die Substantive herausfischen, nach höchsten counts sortieren und manuell nachselektieren, um ihre Verwendungszahl 1999-2023 zu zeigen.

*Allerdings gab es Probleme, weshalb auf Plan C ausgewichen werden musste*

#### Plan A: Die Probleme mit Spacy
* die vortrainierten Modelle de und fr können nicht mit lokalen Spezifizitäten wie 'Westast', 'Expo', 'Agglolac', 'CTS' u. ä. umgehend; diese sind für die Bieler Politik aber gerade wichtig.
* bei den anderen Wörtern, die Spacy zwar stemmen konnte, kamen viel zu tiefe Zahlen heraus, als mit einer kurzen Volltextsuche in code clinic aufgefunden wurden.
* Der Bias war auch nicht für alle Wörter gleich, sodass wenigstens die relativen Frequenzveränderungen brauchbar gewesen wären

Hier [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/null_Urspruengliche_idee_mit_nltk_und_spacy.ipynb] ist die Skizze des Vorgehens auf einem Jupyter Notebook mit der ursprünglichen Idee.

Zwei Auswege:
* Plan B: Selbst ein llm auf lokale Spezifizitäten trainieren. Die Zeit dafür reichte allerdings nicht; ich versuche das in den nächsten Wochen/Monaten aber mit der fastai-Library und einem zugemieteten Server mit entsprechender GPU-Ausstattung und vorinstallierten packages
* Plan C: Manuell arbeiten

#### Plan C: Manuelles Vorgehen:
1. Die Strings nach Sprachen aufspalten und monatsweise als Textfiles abspeichern: [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/1_Sprachfilter.ipynb]

2. Die Strings mit nltk tokenisieren: 
3. Die ersten 1000 Wörter händisch durchsichten. Sofern von Interesse, in eine Liste aufnehmen. 
4. Die Liste von de nach fr übersetzen und allfällige Synonyme in der anderen Sprache berücksichtigen ('Verkehr' -> 'circulation', 'traffic')
5. Nach Wörtern und Komposita fischen: Beispiel: Nach 'budget' statt nach ' budget' suchen (weil sonst z. B. 'Budgetverhandlung' und 'négociation de budget' auf DE wie FRZ nicht gleich gezählt werden)

Code für Schritt 2, 3, 4, 5: [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/1_Sprachfilter.ipynb]

6. df erstellen mit Wort-/Kompositanennungen pro Monat und Plots erstellen: [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/3_plots_aus_frequenz.ipynb]

7. Fürs storytelling: suche der spannenden Begriffe in den jeweils spannenden Stadtratsprotokollen mit visual studio code

### Deklaration Mithilfe
Fürs Coden wurde immer wieder ChatGPT 3.5 konsultiert. Und der BT-Grafiker Michael Lüdi hat die Beschriftung der Grafiken (Namen Achsen, Legenden) Print-Vorlagenkonform gemacht.
