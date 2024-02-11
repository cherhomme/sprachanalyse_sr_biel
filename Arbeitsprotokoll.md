# Arbeitsprotokoll CAS-Arbeit Jérôme Léchot

*Hinweis: Ausser vom 26.-28.1. keine ganzen Arbeitstage, sondern jeweils ein paar Stunden.*

### 2. Dezember

Recap von Plottis Jupyter Notebooks zur Sprachanalyse. Studium der Spacy-library und des dortigen Kurses, um mit dem Matcher manuell Elemente herauszufischen und vortrainierte llms zu trainieren. Problem: Schlecht erklärt, unklar, ob man das einfach so kann auf dem eigenen Rechner.

### 3. Dezember
Herunterladen aller verfügbaren PDFs der Stadtratssitzungen von der webpage der Stadt Biel (https://www.biel-bienne.ch/de/protokolle.html/752). Problem: Nur bis 2013. Per Mail alle digitalisierten SR-Protokolle angefordert. Sie reichen bis 2002, dann muss man ins Stadtarchiv.
Mail an Stadtarchiv mit Bitte um Termin, um SR-Protokolle abzufotografieren.

### 15. Dezember
Abfotografieren von 5250 Seiten, Jahre 2001, 2000, 1999. So macht es mit 1999 und 2023 ein Vierteljahrhundert. Mehr war nicht zu bewerkstelligen wegen Rückenschmerzen und Zeitrestriktion.

### 16. Dezember
Suche nach einer Möglichkeit, den Text aus Fotos zu extrahieren, wie das ja auch das iPhone kann. Tesseract ist bereits auf meinem osx vorinstalliert. Erster Test, dann ocr-en aller 5250 Fotos zu Textfiles.

### 17. Dezember
Die einzelnen .txt-Files pro Foto zu jeweils ganzen Monaten zusammenfassen mit Python.

### 2. Januar
Test mit einem Stadtratsprotokoll und dem Skript [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/null_Urspruengliche_idee_mit_nltk_und_spacy.ipynb]. Grundsätzlich scheint es zu funktionieren, aber es kommen nicht die relevanten Wörter heraus ('Gemeinderat'), ausserdem werden beide Sprachen noch gemeinsam behandelt, ('conseil municipal'), was nicht sinnvoll ist.

### 4. Januar
Weitere Versuche mit obigem Skript während des Vertiefungstags am MAZ; Suche nach einem Sprachfilter, wie er hier [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Textanalyse%20und%20Grafiken/1_Sprachfilter.ipynb] dann verwendet wurde.

### 5. Januar
Manueller Download der Audio-URLs für die nicht schon verschriftlichten Protokolle der Stadtratssitzungen von 2022 und 2023. Mailverkehr mit der Stadt über fehlende Protokolle im November und Dezember 2023.
Erster Test mit der Whisper-API, um die Audiofiles zu Text zu verarbeiten.

### 14. - 17. Januar
Das Whisper-Skript [https://github.com/cherhomme/sprachanalyse_sr_biel/blob/main/Text%20beschaffen/Audio_to_text.ipynb] dauert pro Stadtratssitzung zwischen 45 Minuten und 2 Stunden. Skript immer wieder für eine Sitzung durchlaufen lassen; bei Fehlermeldungen nochmals ab den URLs, die nicht mehr transkribiert wurden.

### 26. - 28. Januar
Erst enthusiastisches Vorgehen mit nltk, spacy um die ganzen Textfiles zu stemmen und Nomina herauszufischen. Hat geklappt auf DE und auf FR - aber nur dem Augenschein nach. Die counts für 'budget' beispielsweise sind viel zu tief, wie ein Vergleich mit der Volltextsuche in visual studio code zeigt. Auch mit dem Matcher kommen viel zu tiefe Zahlen raus. Und bei den Spezifika für Biel funktionierte Spacy auch nicht und liess sich auch nicht anpassen. (Es kann sein, dass ich es einfach nicht hinkriegte mit dem manuellen Ergänzen, obwohl es möglich wäre. Aber dann blieb immer noch die zu tiefe Zahl bei Wörtern, die Spacy offenbar nur manchmal richtig herausfischte.) Die gescheiterten Versuche sind hier [https://github.com/cherhomme/sprachanalyse_sr_biel/tree/main/Textanalyse%20und%20Grafiken/failed_scripts]

Daher Aufgabe dieses Plans und zurück zu manuellem String-Fischen / Fischen mit Regex, manuelles erstellen von Filtern mit spannenden Wörtern in beiden Sprachen, erstellen von Plots mit gleitendem Mittel.

### 6.,7. Februar
Schreiben des Artikels (Tel. mit Grünen-Präsident, Volltextsuche in Stadtratsprotokollen), letzte Anpassungen bei den Plots, Seitenplanung mit Grafiker, Gegenlesen durch Redaktions-Kollege.
