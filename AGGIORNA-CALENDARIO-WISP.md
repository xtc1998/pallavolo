# Procedura: aggiornamento calendario gare UISP

Quando viene richiesta l'esecuzione di questa procedura, aggiorna il calendario del progetto usando il foglio di calcolo
presente nel progetto, senza chiedere di nuovo le istruzioni qui specificate.

## File

- Calendario da aggiornare: `CalendarioOlimpia.html` (rispettare maiuscole e minuscole del nome effettivamente
  presente).
- Fonte: `UISP.xlsx`, se presente. In questo progetto il file corrispondente attualmente si chiama `UISP.xlsx`; usa
  quello se `UISP.xlsx` non esiste e contiene il calendario delle gare UISP/UISP. Non scegliere un altro foglio di
  calcolo se non è chiaramente la fonte corretta: in caso di dubbio, chiedi conferma.

## Regole di aggiornamento

1. Leggi il workbook e individua le partite della squadra Olimpia e i relativi avversari, date, orari e impianti. Usa il
   foglio del calendario gare e, se necessario, quello degli impianti per interpretare i dati.
2. Considera solo le partite UISP/UISP che sono già presenti nel calendario HTML e la cui data è **oggi o successiva**
   (data locale corrente). Non modificare partite passate, FIPAV o altri campionati.
3. Abbina le partite con prudenza usando squadre/avversario e altri dati identificativi disponibili. Aggiorna solo le
   righe HTML corrispondenti a partite identificabili senza ambiguità. Se la fonte manca, è illeggibile o una
   corrispondenza è incerta, non indovinare: segnala il problema e chiedi chiarimenti.
4. Per ogni partita corrispondente, aggiorna esclusivamente la data visualizzata e la data in `data-datetime`,
   mantenendo invariato l'orario già mostrato nel calendario. Il giorno della settimana visualizzato deve corrispondere
   alla nuova data.
5. Aggiorna il testo del luogo solo se differisce da quello indicato nel workbook. Quando il luogo cambia, aggiorna
   anche il collegamento Google Maps usando un URL di ricerca per il nuovo indirizzo
   (`https://www.google.com/maps/search/?api=1&query=...`), codificando correttamente il testo nell'URL e usando `&amp;`
   nell'HTML. Se la cella del luogo non aveva un link, aggiungi il link con la classe `map-link` e gli attributi
   coerenti con gli altri link del calendario. Non inventare indirizzi o coordinate: il link deve cercare il luogo
   fornito dal workbook.
6. Non modificare nient'altro: layout, CSS, formattazioni, struttura, script, filtri, intestazioni, nomi delle squadre,
   orari, campionati, distanze, altre partite e workbook sorgente devono rimanere invariati. In particolare, non
   riformattare o riscrivere l'intero HTML: limita le modifiche ai campi delle partite interessate e ai link dei luoghi
   cambiati.
7. Controlla il diff finale: deve contenere solo le modifiche di date e luoghi/link Maps delle gare UISP/UISP future.
   Verifica inoltre che le date visualizzate e `data-datetime` concordino e che i link Maps puntino al luogo aggiornato.

## Resoconto

Al termine, indica quali partite sono state aggiornate e quali date/luoghi sono cambiati. Se nessun dato è cambiato,
dichiaralo senza modificare il file.
