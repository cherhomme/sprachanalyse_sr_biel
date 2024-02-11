# Arbeitsprotokoll CAS-Arbeit Jérôme Léchot

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

