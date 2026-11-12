# Procedura: aggiornamento calendario gare UISP

Quando viene richiesta l'esecuzione di questa procedura, aggiorna il calendario del progetto usando il foglio di calcolo
presente nel progetto, senza chiedere di nuovo le istruzioni qui specificate.

## File

- Calendario da aggiornare: `CalendarioOlimpia.html` (rispettare maiuscole e minuscole del nome presente).
- Fonte: `UISP.xlsx`, se presente. Se non è disponibile o non contiene chiaramente il calendario UISP, non scegliere un
  altro file senza conferma.

## Regole di aggiornamento

1. Leggi il workbook e individua le partite della squadra Olimpia e i relativi avversari, date, orari e impianti. Usa il
   foglio del calendario gare e, se necessario, il foglio degli impianti.
2. Considera solo le partite UISP già presenti nel calendario HTML la cui data è **oggi o successiva**, usando la data
   locale corrente. Non modificare partite passate, FIPAV o altri campionati.
3. Abbina le partite con prudenza, usando squadre/avversario e altri dati identificativi disponibili. Aggiorna solo le
   righe HTML corrispondenti a partite identificabili senza ambiguità. Se la fonte manca, è illeggibile o una
   corrispondenza è incerta, non indovinare: segnala il problema e chiedi chiarimenti.
4. Per ogni partita corrispondente, aggiorna esclusivamente la data visualizzata e la data in `data-datetime`,
   mantenendo invariato l'orario già mostrato nel calendario. Il giorno della settimana visualizzato deve corrispondere
   alla nuova data.
5. Determina il luogo della partita in questo ordine:
    - Se nella colonna **L** della riga della partita è indicato un numero intero da **1 a 5**, usalo come codice di
      variazione della location. Cerca lo stesso numero nella colonna **C**, righe **231–235**, dello stesso foglio del
      calendario gare del workbook; il luogo corretto è il valore della colonna **D** nella medesima riga. Questo luogo
      sostituisce quello ordinario indicato per la partita.
    - Se la colonna L è vuota o non contiene un codice intero da 1 a 5, usa il luogo ordinario indicato nella riga della
      partita.
    - Se è presente un codice da 1 a 5 ma non è possibile trovare una corrispondenza univoca in C231:C235 o il luogo
      corrispondente in D è vuoto/non valido, non ripiegare sul luogo ordinario e non indovinare: non aggiornare il
      luogo di quella partita e segnala il problema. Puoi comunque aggiornare la data se la partita è identificata con
      certezza.
6. Confronta il luogo determinato con quello nel calendario HTML. Aggiorna il testo del luogo solo se differisce. Quando
   il luogo cambia, aggiorna anche il collegamento Google Maps con un URL di ricerca per il luogo corretto
   (`https://www.google.com/maps/search/?api=1&query=...`), codificando correttamente il testo nell'URL e usando `&amp;`
   nell'HTML. Se la cella del luogo non ha un link, aggiungilo con la classe `map-link` e gli attributi coerenti con gli
   altri link del calendario. Non inventare indirizzi o coordinate: il link deve cercare il luogo fornito dal workbook.
7. Non modificare nient'altro: layout, CSS, formattazioni, struttura, script, filtri, intestazioni, nomi delle squadre,
   orari, campionati, distanze, altre partite e workbook sorgente devono rimanere invariati. Non riformattare o
   riscrivere l'intero HTML: limita le modifiche ai campi delle partite interessate e ai link dei luoghi cambiati.
8. Controlla il diff finale: deve contenere solo le modifiche di date e luoghi/link Maps delle gare UISP future.
   Verifica che le date visualizzate e `data-datetime` concordino e che i link Maps puntino al luogo aggiornato.

## Resoconto

Al termine, indica quali partite sono state aggiornate e quali date/luoghi sono cambiati. Segnala esplicitamente le
partite per cui non è stato possibile risolvere la location dalla colonna L e dalle celle C231:D235. Se nessun dato è
cambiato, dichiaralo senza modificare il file.
