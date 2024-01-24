### Text-aus-Bild-Extraktion

Weil die Stadtratsprotokolle für y<2002 nicht digital vorliegen, habe ich für drei Jahre 1999, 2000 und 2001 alle Protokolle abfotografiert.

Dafür habe ich den OCR-Engine libtesseract verwendet [link a](https://github.com/tesseract-ocr/tesseract).

Für die rund 5250 Fotos habe ich folgenden Befehl in der Command Line ausgeführt:

```
~ % for x in ~/Desktop/downloads/*.png; do
	tesseract ${x} ${x}
done
```

Die txt.-Files pro Foto habe ich dann, gruppiert nach Daten, in Python zu einem Textfile zusammengeführt.

```
import os
from pathlib import Path

input_directory = "/Users/j/Desktop/Stadtratsprotokolle_1999-2003_text"
output_directory = "/Users/j/Desktop/monatliche_protokolle_99-03"

txt_files = sorted(Path(input_directory).glob('*-*.txt'))

# Create a dictionary to group files based on the common ending pattern "...<numbers>-<numbers>.txt"
grouped_files = {}

# Group files based on the common ending pattern
for file_path in txt_files:
    file_name = file_path.name

    # Extract the common ending pattern "...<numbers>-<numbers>.txt"
    common_ending = file_name.split('Protokoll-')[-1].split('.')[0]
    #print(common_ending)
    #Add the file to the corresponding group in the dictionary
    grouped_files.setdefault(common_ending, []).append(file_path)

# Iterate through the groups and merge files within each group based on the ascending number in the beginning
for common_ending, file_paths in grouped_files.items():
    # Sort files within each group based on the ascending number in the beginning
    sorted_files = sorted(file_paths, key=lambda x: int(x.name.split('IMG_')[1].split('SR')[0]))

    # Create the output file for each group
    output_filename = os.path.join(output_directory, f"merged_{common_ending}.txt")

    # Merge the content of files within each group into the output file
    with open(output_filename, 'w') as output_file:
        for file_path in sorted_files:
            with open(file_path, 'r') as input_file:
                output_file.write(input_file.read())
```
