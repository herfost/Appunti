---
tag: note
type: networking
---
# Domain Name System
[[Protocollo]] [[client/server]] trasportato in [[UDP]] e servizio per la 
risoluzione dei nomi simbolici in [[Indirizzo IP]].

# Richista della risoluzione
Il client DNS effettua una richiesta inoltrano un [[pacchetto DNS]] all'indirizzo IP del server DNS (ottenuto dalla configurazione di base possibilmente fornitagli dal server [[DHCP]]) sulla **[[porta]] 58**.  Nel pacchetto di richiesta del client sono contenuti: [[#Componenti | nome simbolico]] da risolvere.
Il name server cerca all'interno del database in cui sono associati nome simbolici ed indirizzi di rete, la corrispondenza del nome richiesto. Nel caso il nome non sia peresenta all'interno del proprio database, il server DNS si comporta da [[attore]] diventando a suo volta un resolver: contatta un'altro name server (DNS Privato) per ottenere l'indirizzo di rete. Questa oprerazione si ripete fino al raggiungimento di un name server avente la corrispondenza richiesta. Le risposte si susseguono fino a giungere al resolver iniziale (DNS Pubblico). 

## Componenti
- [Nome di domionio](): stringa separata da punti (`itis.magistricumacini.edu.it`)  in notazione [[Little Endian]].
- [Fully Qualified Domain Name](): nome di domionio di riferimento a uno specifico nodo dell'albero DNS.
- [Server DNS](): posside un proprio database ove associati nomi simboli e indirizzi di rete corrispondenti, una memoria cache, indirizzi dei resolver DNS Privati.
- Record DNS: resource record con PK = Nome del record. 
	- A = Classico: associazione Nome - Indirizzo
	- PTR = Inversa: associazione Indirizzo IP - Nome
	- CNAME : associazione Nome - Alias
	- MX: associazione Nome - Server Posta Elettronica del nome
	- NS: associazione Nome : Server Autoritativo.

## IANA Schema Gerarchico
[ICCAN/IANA](https://it.wikipedia.org/wiki/ICANN) si occupa dell'organizzazione dei nomi di dominio.
Lo schema consiste in una gerarchia ad albero invertito con root = `.`
A seguire si hanno i nomi di dominio di primo livello [Top Level Domain (TLD)]() quali ccTLD (it, en ecc.), usTLD (edu, gov ecc.) e gTLD (com, net, org ecc.).
Gli enti territoriali gestiscono i domini di secondo livello (Il .it viene gestito dal CNR).

## Richiesta iterativa
Il resolver DNS Pubblico effettua una richeista ad un altro resolver DNS Privato che in caso di corrispondenza inoltra l'indirizzo di rete al resolver DNS Pubblico cha ha effettua la richiesta, altrimenti restituisce l'indirizzo di un'altro DNS che potrebbe effettuare la risoluzione. Il DNS Pubblico effettua una richiesta al resolver DNS fornitogli ripetendo il processo fino al raggiungimento della corrispondenza richiesta.

## Richiesta ricorsiva
Il resolver DNS Pubblico effettua una richiesta ad un altro resolver DNS Privato che in caso di corrispondenza fornisce l'indirizzo di rete richiesto altrimenti si comporta da [[attore]] richiedendo a sua volta la risoluzione ad un resolver DNS Privato che si comporta allo stesso modo. Una volta ricevuta la risposta la inoltra al resolver DNS Pubblico che lo ha contattato. Il processo si ripete fino al raggiungimento della corrispondenza richiesta.
I resolver DNS mantengono le risoluzioni dei nomi nella memoria chace per un tempo di vita detto TTL.

Il server che ha esaudito la richiesta prende il nome di [name server autoritativo]().

## Sicurezza 
L'inivio dei pacchetti UDP non prevede un meccanismo di legittimazione.

### DNS cache poisoning
Il client riceve dei pacchetti DNS falsi contenenti indirizzi IP fasulli al fine di reindirizzare l'utente a   siti diversi da quelli richiesti (phishing ecc.)

[Template :: [[NetworkingT]]]
[Date :: [[19-12-2022]]]