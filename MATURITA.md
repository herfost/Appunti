# Oggetti

Il progetto prevede la seguente struttura:

- `domain`: costituito dalle classi degli oggetti persisiti nel database, classi mappate a database attraverso ORM
- `services`: parte di business logic nella quale sono contenute le funzionalità necessarie alle richieste come SaS
- `apis`: esposizione delle informazioni

## Domain :

Le classi degli oggetti persisiti nel database, prive di annotazioni e specifiche di linguaggio per favorire la lettura, sono:

### Caseificio

```
Caseificio:
    id: CaseificioId
    name: String
    rappresentative: String
    address: Address
```

### Shape

```
Shape:
    id: ShapeId
    choice: Enum ShapeChoice
    seasoning: Enum ShapeSeasoning
    productionDate: DateTime
    weight: Double
```

### Sale

```
Sale:
    id: SaleId
    type: Enum SaleType
    cost: Double
    date: DateTime
    shape: Shape
```

### Client

```
Client:
    id: ClientId
    name: String
    type: Enum ClientType
    address: Address
    partitaIva: String
```

### Address

```
Address:
    street: String
    city: String
    province: String
    latitude: Double
    longitude: Double
```

### ShapeChoice

```
Enum ShapeChoice:
    STANDARD,
    DIFETTOSA
```

### ShapeSeasoning

```
Enum ShapeSeasoning:
    ANNUALE: 12,
    BIENNALE: 24,
    SEMI_TRIENNALE: 30,
    TRIENNALE: 36
```

### SaleType

```
Enum SaleType:
    DETTAGLIO,
    INGROSSO,
    OMAGGIO,
    PROMOZIONE
```

### ClientType

```
Enum ClientType:
    GRANDE_DISTRIBUZIONE
    GROSSISTA
    PERSONA_FISICA
```

### UserCredentials

```
UserCredentials
    username: String
    password: String
    applicationId: String
```

### EntityId

Per fovorire la leggibilità e mantenibilità del codice si utilizzano delle classi Wrapper per i parametri identificati (Primary Key, Foreign Key)

- `CaseificioId`: classe che provvede alla gestione dell'Id per la classe Caseificio
- `ShapeId`: classe che provvede alla gestione dell'Id per la classe Shape
- `SaleId`: classe che provvede alla gestione dell'Id per la classe Sale
- `ClientId`: classe che provvede alla gestione dell'Id per la classe Client

### ORM

Mediante l'uso di ORM, apposite librerie e annotazioni si realizzano le tabelle dell'entità del dominio e si specificano primary keys, foreign keys.
Scrivere codice SQL sono in caso di necessità e query specifiche, difatto utilizzarei anche annotazioni e librerie, vedere Lambok ad esempio, per evitare di riempire le classi del dominio con metodi verbosi e favorire la coesione e compresione del codice.

```
@Entity
CaseificioId:
    @Id
    @PrimaryKey
    CaseificioId
    ...
```

## Services

I servizi prevedono le infrastture utili alla realizzazione delle funzionalità richieste

### Database

Realizzato attraverso ORM e liberia, che mappano gli oggetti del `domain` a entity tramite relative annotazioni e impostano specifiche del database: `stored procedures`, `dbms` scelto ecc. Viene realizzato un opportuno sistema

### Business Logic

#### Interfaccia a database

- Operazioni CRUD
- Query al database

#### Autenticazione

L'immissione dei dati relativi alla produzione all'interno di un caseificio all'interno della piattaforma viene preceduto dall'accesso dell'utente. Alcune dei possibili metodo che si possono utilizzare sono:

- Athentication as a Service by Okta
- Codice OTP tramite API Google
- Codice QR nel caso, in futuro, si volesse realizzare un'applicazione mobile.

### Webapplication

La webapplication viene costruita mediante Framework frontend React, la veste grafica mediante Tailwindcss, come pakage manager Vite

#### Componenti

Le componenti utili al progetto sono:

- LoginForm: form che l'utente utilizza per accedere alla piattaforma.
- DichiarazioneForm: insieme dei dati richiesti dal consorzio
- DichiarazioneCard: insieme dei dati richiesti dal consorzio come componente leggibile.
- EntitiesCard: informazioni delle entity rappresentanti come componenti leggibili (CaseificioCard, ShapeCard ecc.)
- CardContainer: contenitore delle Card
- Navbar: barra di navigazione utilizzata per accedere alle varie sezioni della piattaforma

#### Routes

Le pagine della piattaforma sono:

- Login
- Homepage
- Produzione: pagina in cui visualizzare le dichiarazioni effettuate e aggiungerne di nuove
- Caseifici, Clienti, Vendite, Forme: registro delle entity
- Dashborad: sezione in cui visualizzare, filtrare e gestire i dati di interesse (operazione di media, calcolo per entity, analisi ecc.)

Le pagine della piattaforma sono costituite da componenti popolate dai dati pubblici ottenuti attraverso le API

```jsx
export default function Caseifici {
    const [caseifici, setCaseifici] = useState([]);

    useEffect(() => {
        const fetchCaseifici = async () => {
          const data = await (await fetch("api/caseifici")).json();
          setCaseifici(data);
        };

        fetchCaseifici();
    }, []);

    return (
        <CardGroup 
            cards={
                caseificiCards = []
                caseifici.map((caseificio) => {
                    caseificiCards.push(ICaseificioCard(...caseificio));
                }
            }
        />
    );
}
```

## APIs
Le API sono disposte per le relative entity e funzionalità della piattaforma: 
- Caseificio: (getAll, getById, getByName ...)
- Shape
- Sale
- Client
- Address (caseificio/id/address, ...)

Utente > API Request > Servizio > Database > Servizio > API Response > Utente