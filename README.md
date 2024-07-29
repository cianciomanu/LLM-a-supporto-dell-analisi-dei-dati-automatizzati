# LLM a supporto dell'analisi dei dati automatizzati
Data la grande potenzialità degli LLM ci siamo posti l’obiettivo di verificare in che modo questi possono intervenire nell’implementazione di una pipeline dell’elaborazione dei dati.

Questa repository contiene uno studio sul modo migliore in cui è possibile interagire con gli LLM.

## Pipeline 
1. Data Finding
2. Data Cleaning
3. Data Analysis
4. Data Visualization

## Divisione delle cartelle
Le cartelle sono divise in modo tale che sia possibile distinguire per ogni fase della pipeline i relativi prompt che sono stati utilizzati e le relative risposte che sono state ottenute.

## Dataset Utilizzati
Link ai dataset:
- Luoghi del turismo Sicilia: https://opendata.comune.palermo.it/ws.php?id=1208&fmt=xml
- Impianti di rifonimento: https://www.mimit.gov.it/images/exportCSV/anagrafica_impianti_attivi.csv
- Prezzo negli impianti di rifornimento: https://www.mimit.gov.it/images/exportCSV/prezzo_alle_8.csv

## Profili di prompting
- AUTONOMO: non si fornisce nessuna guida sul modo in cui svolgere un determinato compito; si vuole solamente che venga risolto.
- GUIDATO: viene fornito il modo in cui risolvere un problema in modo riassuntivo, utilizzando unua terminologia dettagliata
- ESPERTO / GUIDATO CON ESEMPI: anche qui viene fornito il modo in cui risolvere il problema, si utilizza una terminologia dettagliata e inizialmente vengono date delle direttive precise sulle risposte che vorremo ricevere, viene fornito molto contesto in modo tale che il problema possa risultare più chiaro. (<b>Utilizzo di fine tuning<b>)