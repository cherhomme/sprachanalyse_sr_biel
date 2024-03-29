### Beschreibung des Vorgehens

Zuerst wollte ich mit nltk die Textstrings tokenisieren, dann mit spacy und den vortrainierten deutschen und französischen Modellen die Token stemmen und dann die Substantive herausfischen.

Die Probleme mit Spacy
* die vortrainierten Modelle de und fr können nicht mit lokalen Spezifizitäten wie 'Westast', 'Expo', 'Agglolac', 'CTS' u. ä. umgehend; diese sind für die Bieler Politik aber gerade wichtig.
* bei den anderen Wörtern, die Spacy zwar stemmen konnte, kamen viel zu tiefe Zahlen heraus, als mit einer kurzen Volltextsuche in code clinic aufgefunden wurden.
* Der Bias war auch nicht für alle Wörter gleich, sodass wenigstens die relativen Frequenzveränderungen brauchbar gewesen wären

Hier ist der [Link](sprachanalyse_sr_biel/Textanalyse und Grafiken/Urspruengliche_idee_mit_nltk_und_spacy.ipynb) auf ein Jupyter Notebook mit der ursprünglichen Idee.

Zwei Lösungen:
* Selbst ein llm auf lokale Spezifizitäten trainieren. Die Zeit dafür reichte allerdings nicht; ich versuche das in den nächsten Wochen/Monaten aber mit der fastai-Library und einem zugemieteten Server mit entsprechender GPU-Ausstattung. Hier wird helfen, dass ich bereits einen Korpus von 6,7 Millionen Wörtern habe.
* Manuell arbeiten

Das manuelle Vorgehen:
1. Die Strings nach Sprachen aufspalten und monatsweise als Textfiles abspeichern
2. Die Strings mit nltk tokenisieren
3. Die ersten 1000 Wörter händisch durchsichten. Sofern von Interesse, in eine Liste aufnehmen.
4. Die Liste von de nach fr übersetzen und allfällige Synonyme in der anderen Sprache berücksichtigen ('Verkehr' -> 'circulation', 'traffic')
5. Nach Wörtern und Komposita fischen: Beispiel: Nach 'budget' statt nach ' budget' suchen (weil sonst z. B. 'Budgetverhandlung' und 'négociation de budget' auf DE wie FRZ nicht gleich gezählt werden)
6. df erstellen mit Wort-/Kompositanennungen pro Monat und Plots erstellen
