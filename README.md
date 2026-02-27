# Java Network: Iterative Echo Socket

Progetto Java che implementa un sistema di comunicazione client-server iterativo basato su protocollo TCP/IP.

## Descrizione
Il programma estende le funzionalità di base delle socket TCP permettendo una sessione di messaggistica continua. Il server rimane attivo e processa i messaggi inviati dal client in un ciclo interattivo, convertendo il testo in maiuscolo fino alla ricezione del comando di chiusura.



## Funzionamento dei Componenti:
* **Server Iterativo**: Inizializza la `ServerSocket` e utilizza il metodo `.accept()` per stabilire la connessione. Entra in un ciclo di ascolto continuo dove legge le stringhe del client e le restituisce modificate. La sessione termina e le risorse (stream e socket) vengono liberate solo se riceve il messaggio "BYE".
* **Client Persistente**: Si connette al server e apre un canale di comunicazione interattivo tramite `Scanner`. Permette l'invio di molteplici messaggi all'interno della stessa connessione, chiudendo il socket solo dopo l'invio del comando di disconnessione.

Il sistema garantisce la corretta gestione del ciclo di vita della connessione, assicurando che i socket vengano chiusi su entrambi i lati per evitare perdite di risorse (resource leaks).

## Tecnologie e Concetti
* **Java Networking**: Utilizzo avanzato delle classi `Socket` e `ServerSocket`.
* **Session Management**: Implementazione di una logica di terminazione della sessione basata su keyword ("BYE").
* **Stream I/O**: Utilizzo di `BufferedReader` e `PrintWriter` con auto-flush per la sincronizzazione dei messaggi.
* **Controllo del Flusso**: Gestione di cicli `while(true)` annidati per supportare la riconnessione e la persistenza della sessione.
