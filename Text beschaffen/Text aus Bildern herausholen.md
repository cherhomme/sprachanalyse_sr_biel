### Text-aus-Bild-Extraktion

Weil die Stadtratsprotokolle für y<2002 nicht digital vorliegen, habe ich für drei Jahre alle Protokolle abfotografiert.

Dafür habe ich den OCR-Engine libtesseract verwendet [link a](https://github.com/tesseract-ocr/tesseract).

Für die rund 5250 Fotos habe ich folgenden Befehl in der Command Line ausgeführt:

```
~ % for x in ~/Desktop/downloads/*.png; do
	tesseract ${x} ${x}
done
```
