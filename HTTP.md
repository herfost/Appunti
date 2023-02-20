---
tag: note
type: networking
---

# Hypertext Transfer Protocol
[[Protocollo client/server]] [[Protocollo Stateless |stateless]] di tipo [[Protocollo testuale |testuale]] trasportato da TCP sulla **[[porta]] 80 (oppure 8080)** 
I client prendono il nome di [[Web Browser]], i server prendono il nome di [[Web Server]].
Il client effettua una richiesta specificando la risorsa attraverso un [[ Uniform Resource Lacator | URI (Uniform Resource Lacator)]]. L'URL identifica univocamente una risorsa sulla rete [[TCP/IP]] mediante una stringa strutturata. 

## Composizione URL 
[Schema (protocollo)](): nome del protocollo con cui viene recuperata la risorsa.

## Stateless 
Le connessioni vengono chiuse dopo la risposta del server. Il server non ha modo di associare dati specifici ai client durante le session di navigazione. 

## Cookie
Blocco di dati creato da un [[Web Server]] durante la navigazione da parte di un utente su un sito web. Viene memorizzato sul computer dell'utente dal [[Web Browser]] e consente di tracciare gli accessi del client alla risorsa memorizzando i dati a fine sessione. Quando viene effettuata una nuove connessione, vengono caricati i cookie contenenti le informazioni della sessione precedente.

## Sessione
1. [[Web Server]] in ascolto sulla **[[porta]] 80**. 
2. [[Web Browser]] effettua una richiesta utilizzando uno dei [[#Metodi]] HTTP passando come argomento l' [[Uniform Resource Lacator |URL]]  e specificando le caratteristiche della richiesta negli [headers]().
3. [[Web Server]] invia una riposta specificando lo [[stato]] della richiesta (200 OK, 404 NOT FOUND ecc...) specificando le caratteristiche della risposta negli [headers]().
4. [[Web Server]] inoltra il [corpo]() del messaggio. Effettua la disconnessione.

## Pacchetto
Il client invia [HTTP Request](): **richiesta**, **headers**, riga vuota, **corpo**.
Il server invia [HTTP Response](): **stato**, **headers**, riga vuota, **corpo**.

## Metodi 
Richieste effettuabili mediante il protocollo.
-   GET (read)
-   POST (create)
-   PUT (update) (Sovrascrive l'intero record )
-   PATCH (update) (Sovrascrive solo la parte del record indicata)
-   DELETE 
-   HEAD
-   TRACE
-   OPTIONS
-   CONNECT

## Sicurezza 
Il protocollo viene utilizzato maggiormente nelle reti pubbliche. 

### Man in the middle
Un "prof. lei Hakero" legge e modifica i messaggi tra due nodi. Mediante [[Web spoofing]] vengono modificati gli indirizzi IP dell'header. Un utente non sa di comunicare con un server malevolo che alla ricezione del messaggio li modifica a proprio piacimento e inoltra la risposta al richiedente. 
Inoltre, i pacchetti inviati non sono cifrati quindi il contenuto dei pacchetti può essere letto mediante [sniffing](O) del traffico di rete ([[Wireshark]] ecc.)

### Hypertext Transfer Protocol over Secure Socket
Viene autenticata l'autenticazione dei due capi della connessione.
Il messaggio viene cifrato.

### Cookies 
[HTTPOnly](): blocca l'accesso ai cookie da parte degli script.

[Template :: [[NetworkingT]]]
[Date :: [[19-12-2022]]]