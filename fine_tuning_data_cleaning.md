# Fine tuning data cleaning

## Commento sull'utilizzo
Bisogna adattare i valori tra parentesi quadre che sono presenti nell'elenco numerato alle esigenze specifiche, cioè: `[nome_colonna]`, `[metodo_specifico]`, `[nome_colonna_date]`, `[elenco_colonne]`, `[nuovi_nomi]`, `[nome_colonna_da_normalizzare]`, `[metodo_di_normalizzazione]`, `[nome_nuova_colonna]`, `[colonna1]`, `[colonna2]`, e `[metodo_combinazione]`.

---

Data la seguente tabella di dati in formato [formato], esegui le seguenti operazioni di data cleaning utilizzando la libreria Pandas in Python, seguendo queste linee guida:

1. **Rimuovi tutte le righe duplicate.**
2. **Gestisci i valori mancanti** nella colonna `[nome_colonna]` sostituendoli con `[metodo_specifico]`;
3. **Standardizza il formato delle date** nella colonna `[nome_colonna_date]` al formato YYYY-MM-DD;
4. **Rinomina le seguenti colonne** `[elenco_colonne]` in `[nuovi_nomi]`;
5. **Controllo delle stringhe con espressioni regolari** nelle seguenti colonne `[elenco_colonne]`;
6. **Normalizza i valori** nella colonna `[nome_colonna_da_normalizzare]` utilizzando `[metodo_di_normalizzazione]`;
7. **Estrai e crea una nuova colonna** `[nome_nuova_colonna]` combinando le informazioni delle colonne `[colonna1]` e `[colonna2]` attraverso `[metodo_combinazione]`;
8. Implementa il **multithreading** per ottimizzare l'elaborazione parallela dei dati, utilizzando il modulo concurrent.futures o threading. Identifica le funzioni che possono essere eseguite in parallelo e gestisci la loro esecuzione con un ThreadPoolExecutor, impostando max_workers in base alle capacità del sistema. Proteggi le risorse condivise con meccanismi di locking per evitare condizioni di gara.

**Direttive per l'implementazione del codice:**

- **Suddividi il codice in funzioni specifiche**: ogni passaggio sopra elencato dovrà essere implementato in una funzione dedicata. Questo aiuta a mantenere il codice organizzato, leggibile e facilita il riutilizzo del codice.
- **Commenta ogni funzione**: ogni funzione dovrà essere accompagnata da commenti che ne descrivano lo scopo, i parametri in ingresso, il valore di ritorno e qualsiasi dettaglio rilevante per la comprensione del codice.
- **Ottimizza le funzioni per efficienza**: assicurati che le funzioni siano algoritmicamente efficienti, minimizzando il numero di passaggi computazionali dove possibile e utilizzando le funzionalità di Pandas in modo efficace per gestire grandi volumi di dati.
- **Favorisci la leggibilità e la manutenibilità del codice**: il codice dovrà essere scritto in modo chiaro e mantenibile, con nomi di variabili significativi e una struttura che faciliti eventuali modifiche o estensioni future del progetto.

**Esempio di struttura del codice:**

```python
import pandas as pd

def remove_duplicates(df):
    """
    Rimuove le righe duplicate dal DataFrame.
    
    :param df: DataFrame da cui rimuovere le duplicate.
    :return: DataFrame senza duplicati.
    """
    # Codice per rimuovere le duplicate
    return df_deduplicated

# Definisci qui altre funzioni seguendo lo schema sopra.

def main():
    # Carica i dati
    # Applica le funzioni per il data cleaning
    # Salva o visualizza i dati puliti

if __name__ == '__main__':
    main()
```

Le colonne del file sono:`[nome_colonne]`
La parte iniziale del file sul quale effettuare data cleaning è:`[porzione del file da analizzare]`
Questo approccio assicura che il codice sia ben organizzato e facile da mantenere o estendere.

---
## Approfondimento
**Punto 2: Gestione dei valori mancanti**, per gestione dei valori mancanti non si intende semplicemente andare a rimuovere una riga che non ha un certo valore, ma piuttosto andare ad aggiungere un valore per quella colonna. 
Per fare questo possiamo utilizzare:

1. sostituzione con un valore fisso specificato: utile per sostituire i valori mancanti con un valore di default che ha senso nel contesto dei tuoi dati. 
`[metodo_specifico]` =  `fixed = x`

2. sostituzione con la media, mediana o moda: adatto per dati numerici, dove sostituire i valori mancanti con la media, mediana o moda delle altre osservazioni può preservare la struttura generale dei dati. 
`[metodo_specifico]` =  `['mean', 'median', 'mode']`

3. interpolazione: Consigliato per sequenze temporali o dati ordinati, dove i valori mancanti possono essere stimati in base ai valori circostanti.   
`[metodo_specifico]` = `interpolate`

4. Utilizzo di un modello: complesso ma potente, prevede l'addestramento di un modello per predire i valori mancanti basandosi sulle altre caratteristiche dei dati. 
`[metodo_specifico]` = `model`.

**Punto 5: normalizza i valori**, utile soprattutto quando si lavora con algoritmi di machine learning che presuppongono dati su scale simili, ma non solo. 
Le varie tecniche sono:
1. Min-Max Scaling: questa tecnica scala e trasla i dati in modo che si adattino in un range prefissato, tipicamente (0, 1) o (-1, 1). È utile quando si desidera mantenere le distribuzioni sparse dei dati. 
`[metodo_di_normalizzazione]` =  `Min-Max Scaling`.
2. Standardizzazione (Z-score Normalization): rimuove la media e scala i dati alla varianza unitaria. Questo metodo è ideale quando i dati seguono una distribuzione normale.  
`[metodo_di_normalizzazione]` =  `z_score_normalization`.
3. Normalizzazione per Massimo Assoluto: scala i dati dividendoli per il valore massimo assoluto. È utile per dati che devono essere mantenuti all'interno di un range ma non necessariamente limitati a (0, 1) o (-1, 1). 
`[metodo_di_normalizzazione]` =  `max_abs_scaling`.
4. Normalizzazione Robusta (Robust Scaling): scala i dati utilizzando la mediana e l'intervallo interquartile, riducendo l'impatto degli outlier. Questo metodo è preferibile quando i dati contengono outlier o sono distribuiti non normalmente. 
`[metodo_di_normalizzazione]` =  `robust_scaling`.

Se i dati provengono da un file **xml** allora è conveniente specificare anche il nome della root.