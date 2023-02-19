# Web Application e JAX-RS

## Metodi HTTP corrispetivi CRUD: 
- GET: read
- POST: create
- PUT / PATH: update
- DELETE: delete

##  Header HTTP:
contiene i metadati della comunicazione.
Content-Type: 
Accept: 

## Specifiche Java
- Glassfish: applicazione Java EE che supporta lo sviluppo di Jakarta REST API
- ContextPath: percorso in cui confluiscono i file relativi alla root directory del webserver.

- @ApplicationPath: annotazione che identifica il percorso dell'applicazione che ricopre il ruolo di percorso URL base delle risorse.

- @Path: annotazione che identifica il percorso con cui una classe o metodo rispondono alle richieste.

- Servlet: componente che consente di gestire l'interazione tra client e server
- ServletContext: componente che si occupa della condivisione di file e dati tra le varie pagine della webapplication.
- @Context: consente di effettuare l'ignezione di richieste e risposte all'interno della webapplication. Lo abbiamo utillizato per inserire il ServletContext utilizzato per lo scambio e accesso di dati e file. 


- @XmlRootElement: annotazione che identifica elementi il cui schema viene scritto in XML.
```java
@XmlRootElement(name = "libro")
public class Libro {
	private String name;
	private String autore;
	...
}
```
```xml
<libro>
	<name>...</name>
	<autore>...</autore>
</libro>
```

- @PathParam: annotazione che consente di estrarre il valore di una variabile all'interno di un percorso.
```java
@Path("/libro/{nomeLibro}")
public String getLibro(@PathParam("nomeLibro") String nomeLibro) {
	return libri.get(nomeLibro);
}
```

- @CookieParam: annotazione che consente di estrarre il valore di una variabile all'interno di un cookie.
```java
@Path("/libro/aggiungi/{nomeLibro}")
public Response addBook(@CookieParam("userToken") String userToken, @PathParam("nomeLibro") String nomeLibro) {
	if (tokens.get(userToken) != null) {
		libri.add(nomeLibro);
		return Response.ok("inserito").status(200).build();
	} else return Response.status(Status.NOT_AUTORIZED).build();
}
```

- @QueryParam: annotazione che consente di estrarre il valore di una variabile all'interno di un percorso URL.
`GET: libri/get?nomeLibro="The Dictator Handbook"`
```java
@GET
public Response readBook(@QueryParam("nomeLibro") String nomeLibro) {
	Libro libro = libri.read(nomeLibro);
	
	return libro != null ? 
	Response.ok(libro).status(200).build() : 
	Response.status(Status.NOT_FOUND).build();	
}
```

- @FormParam: annotazione che consente di estrarre il valore di una variabile all'interno di un form.
```html
<html>
...
<form action="service/login" method="post">
	<input type="text" name="username" placeholder="Username">
	<input type="password" name="password" placeholder="Password">
	<input type="submit" name="login" value="login">
</form>
</html>
```
```java
@GET
public Response login(@FormParam("username") String username, @FormParam("password") String password) {
	User user = new User(username, SHA(password));
	User read = userPersistence.read(user);
	
	if (!user.equals(read)) return Response.status(Status.NOT_AUTORIZED);
	return Response.ok();
}
```

- @Consumes: annotazione che specifica il formato della risposta (corrispettivo dell'header Contet-Type dell'HTTP)
- @Produces: annotazione che specifica il formato della richiesta (corrispettivo  all'header Accept  dell'HTTP)

## Design Pattern
- Definzione: soluzione note a problemi riccorrenti.
- Singleton: pattern di tipo creazionale che determina e garantisce l'instanziazione di una e una sola instanza di una data classe fornendone un punto di accesso globale.

```java
public class PersistenzaUtenti implements IPersistence<String, Utente>
	private static PersistenzaUtenti instance = null;
	private static final List<Utente<String>> utenti;
	
	// Una ed una sola instanza
	private PersistenzaUtenti() {
		utenti = new ArrayList<Utente<String>>();
	}

	// Punto di accesso globale
	public static PersistenzaUtenti getInstance() { 
		if (instance == null) {
			instance = new PersistenzaUtenti();
		}	return instance;
	}
	
	...
}
```

- Template Method: pattern di tipo comportamentale che definisce un'elenco di operazioni da svolgere senza specificarne la definzione
```java
public class Game {
	// Metodo che definisce le operazioni da svolgere 'scheletro'
	public final void loadGame() {
		initialize();
		setup();
		save();
	}

	// Metodo Hook: da implementare nelle classi figlie
	abstract public void initialize();

	final public void setup() {
		// Codice che organizza il gioco
	}

	// Metodo Hook: da implementare nelle classi figlie
	abstract public void save();
}
```

- Observer: pattern di tipo architetturale che definisce rilazioni tra oggetti dipendenti tra loro al cambiare del loro stato. Si hanno `Osservatori` che "osservano" lo stato di `Soggetti`, gli oggetti osservati. 


```java
public class CanaleYoutube {
	public List<IOsservatoreCanale> utenti;
	public void notify(Event event) {
		utenti.forEach((utente) -> {
			utente.update(event);
		});
	}

	public void pubblicaVideo(Video video) {
		notify(new EventVideoPubblicato(this, video));
	}
}

public UtenteYoutube implements IOsservatoreCanale {
	public void update(Event event) {
		Object source = event.getSource();
		if (source instanceof CanaleYoutube) {
			// Codice per la notifca da parte di un canale youtube
		}
		...
	}
}

public interface IOsservatoreCanale {
	public void update();
}

public class Event implements SourceObject {
	private Object source;

	public Event(Object source) {
		this.source = source;
	}

	@Override
	public Object getSource() {
		return source;
	}
}

public class EventVideoPubblicato extends Event {
	...
}

```
- Getione Eventi (Java AWT): immaginiamo di dover effettuare un'azione ogni qualvolta un utente clicci un dato bottone, allora una la classe che reagisce all'azione "onButtonClick" deve ricoprire il ruolo di "Osservatore" e il bottone "osservato" assume il ruolo di "Soggetto". In java AWT si scrive.
```java
public class MyApp() {
	...
	button.addActionListener(this); // Aggiungi questa classe all'elenco degli osservatoi del bottone, this diventa un'osservatore di button;
	...
	public void onButtonClick() { ... }
}

```

Risorse:
- ApplicationPath, Path, PathParam: https://www.logicbig.com/tutorials/java-ee-tutorial/jax-rs/path-annotion-resource-mapping.html
- XmlRootElement: https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/annotation/XmlRootElement.html, https://howtodoinjava.com/jaxb/xmlrootelement-annotation/