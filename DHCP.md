---
tag: note
type: networking
---
# Dynamic Host Configuration
[[Protocollo]] [[client/server]] trasportato in [[UDP]] e servizio per la 
[[DHCP#Configurazione di rete| configurazione di rete]] agli host in rete [[TCP/IP]].

## Configurazione di rete
La richiesta della configurazione di rete avviene durante la fase di [[bootstrap]], nel [[dominio di broadcast]] deve esserci almeno un server DHCP oppure una stazione che opera da [[DHCP Relay]] ovvero si occupa di ritrasmettere la richiesta ad un altro dominio di broadcast e fornire la risposta al client.

### Parametri
La configurazione TCP/IP fornita consiste in: [[indirizzo IP]], [[subnetmask]], [[default gateway]], indirizzi di server [[DNS]], [[lease]], ecc.

## Invio dei pacchetti
I [[pacchetti]] vengono inoltrati in [[broadcast]]: il [[client]] effettua la richiesta sulla **[[porta]] 67** attente la risposta sulla porta **[[porta]] 68**.

## Indirizzi dinamici
Gli [[indirizzi IP]] forniti dal server DHCP prendono il nome di **indirizzi dinamici**.

## Funzionamento
Viene designata una macchina server a fornire i [[#Configurazione di rete | parametri di inizializzazione]] richiesti dal client, di cui tiene traccia un un proprio [[database]]. Viene definito un [[ambito]] ovvero il pool degli indirizzi IP disponibili. Di default. gli indirizzi vengono assegnati [[DHCP#Indirizzi dinamici | dinamicamente]] per un periodo di tempo determinato ([[lease]]). Gli indirizzi IP permanenti vengono assegnati mediante le [[reservation]], dove mediante [[l'indirizzo MAC]] della macchina viene associato l'indirizzo IP riservato.

## Comunicazione
Scambio di quattro messaggi in handshake simmetrico a 4 vie detto [[DORA]]: 
1. [DISCOVER](): un client invia la richiesta in broadcast sulla porta 67 inoltrando un parametro id che lo indentifica nell'arco della comunicazione.
2. [OFFER](): un server, ricevuta la richiesta, invia la la risposta in broadcast: una configurazione contenente l'indirizzo IP proposto / "offerto".
3. [REQUEST](): il client invia una richiesta in broadcast per conferma l'offerta ricevuta indicando la configurazione di rete scelta.
4. [PACK](): il server invia, in broadcast, una risposta di conferma dei dati, aggiorna il proprio database e ambito e chiude la sessione.

## Sicurezza
Il protocollo opera nelle reti trust (reti sicure in LAN o P2P).
Le richieste ricevuta dal server e le risposte ricevute dal client possono essere illegittime.

### DHCP Address Starvation:
Il server DHCP potrebbe ricevere un numero di richieste DHCP, dove l'indirizzo fisico inviato non corrisponde a quello della macchina ma viene continuamente alternato mediante [[MAC spoofing]], sufficiente da esaurire il proprio ambito (pool di indirizzi). [Maggiori informazioni...](https://www.sciencedirect.com/science/article/abs/pii/S0045790612001140#:~:text=DHCP%20starvation%20attack%20is%20an,users%20can%20be%20denied%20service)

### DHCP Rouge
Il client DHCP potrebbe ricevere configurazioni di rete scorrette dove i parametri, alterati e manipolati, possono costituire gravi vulnerabilità. [Maggiori informazioni...](https://en.wikipedia.org/wiki/Rogue_DHCP)

[Template :: [[NetworkingT]]]
[Date :: [[19-12-2022]]]