---
title: Gestione dello Stato
---

# 1. Index


# 2. Gestione dello Stato

---
title: Gestione dello Stato
---

# 1. Index

<!--toc:start-->

- [1. Index](#1-index)
- [2. Gestione dello Stato](#2-gestione-dello-stato)
  - [2.1. Cookies](#21-cookies)
  - [2.2. Serializzazione](#22-serializzazione)
  - [2.3. Stato di Sessione](#23-stato-di-sessione)
  - [2.4. HTML5 WebStorage](#24-html5-webstorage)
  <!--toc:end-->

# 2. Gestione dello Stato

<div class="grid2">
<div class="">

Nelle applicazioni web la gestione degli stati non è "semplice" come nel caso delle applicazioni desktop.
Nel caso di quset'ultime ogni utilizzo dell'applicazione ha in memoria lo stato precedente dalla prima esecuzione.

Nel caso delle applicazioni web **ogni richiesta _HTTP_ è indipendente dalle precedenti**.
Il webserver a priori non ha modo di capire se due richieste provengano da utenti diversi o meno.

</div>
<div class="">
<img class="80" src="./images/Stato/Differenza Desktop-Web.png">
</div>
</div>

Abbiamo la necessità quindi di distinguere tra **sessioni diverse**.
I meccanismi disponibili all'interno dell'_HTTP_ per passare queste richieste sono:

- _Query strings_: contengono un'identificatore univoco che può essere propagato
- _Cookies_

## 2.1. Cookies

Quello dei **cookies** è un approccio _client-side_ per propagare informazioni di stato.

Sono coppie di `nome=valore` salvati in uno o più file che sono gestiti dal browser.

Nonostante le informazioni siano **salvate e gestite dal browser**, l'informazioni nei _cookie_ **viaggiano nell'header _HTTP_**.

I siti che utilizzano _cookies_ non dovrebbero dipendere dalla loro disponibilità per **feature critiche**, poiché i _cookies_ possono essere cancellati/modificati dagli utenti.

Uno schema di come funzionano i cookie è il seguente:

<img class="60" src="./images/Stato/Cookie - life.png">

Un _cookie_ è una **piccola quantità di dati** (circa `4KB`) **inviati da un sito web e salvati nel web browser di un utente** mentre l'utente utilizza un sito.

Un web-server specifica che un cookie venga settato inviando un header _HTTP_ chiamato `Set-Cookie`:

> Set-Cookie: name=value[; expires=date][; domain=domain][; path=path][; secure]

Quando un _cookie_ è presente e le regole opzionali lo permettono, il _cookie_ è inviato in un header HTTP chiamato `Cookie` che contiene `Cookie: name=value`

Per creare un _cookie_ in _PHP_:

```php
bool setcoockie(string $name [,
                string $value [,
                int $expire = 0 [,
                $path [,
                string $domain [,
                bool $secure = false [,
                bool $hrrponly = false ]]]]]])
```

Questa funzione definisce un cookie che andrà inviato con il resto dell'_header HTTP_.
Come tutti gli altri _header_, **devono essere inviati prima di qualsiasi output da parte dello script**

Andiamo ad analizzare più a fondo cosa indicano:

<div class="flexbox"><span class="index">

| Variabile | Descrizione                                                                                                                                                                                                                                                                              |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `expire`  | indica quando un _cookie_ non deve più esser inviato al server, e può essere canccellato dal browser. Se non + specificato diversamente il _lifespan_ di un _cookie_ è **una singola sessione** (quando si accende il browser fino a quando si spegne).                                  |
| `domain`  | indica i domini ai quali in cookie va inviato. Di default è impostato all'_host della pagina che crea il cookie_                                                                                                                                                                         |
| `path`    | indica un _path URL_ che **deve esistere nella risorsa richiesta prima di inviare l'header**. La verifica è fatta comparando i singoli caratteri con l'inizio della richiesta _URL_, e il cookie è inviato solo se c'è una corrispondenza. Di default il valore è la _current directory_ |
| `secure`: | è una flag che non ha valori specificati. Specifica se il cookie va inviato tramite una richiesta `SSL` con il _protocollo HTTPS_ (contenente informazioni confidenziali/sensibili). Di default i cookie in una connessione HTTPS sono settati su `secure`.                              |

</span></div>

```php
$value = 'a nice cookie';

setcookie("mycookie", $value);


setcookie("mycookie", $value, time()+3600); // lifespan 1 ora

setcookie(  "mycookie",
            $value,
            time() + 3600,
            "/~mario/",
            "unipi.it",
            1);
/*
* lifespan 1 ora,
* disponibile nella directory /~mario/ e le sue sub-directory
* disponibile nei sottodomini di unipi.it
* Settato se esiste una connessione sicura
*/
```

Esistono due tipi di cookie:

- _Cookie di **sessione**_: non hanno una scadenza (quella della sessione)
- _Cookie **persistenti**_: hanno una scadenza specificata

Per utilizzare un _cookie_:

<div class="grid2">
<div class="top">
<p class="subt">

Scrittura

</p>

```php
$scadenza = time() + 60*60*24;
// Aggiungo un giorno ad adesso

$name = "Username";
$value = "Riccardo";
setcookie($name, $value, $scadenza);
```

</div>
<div class="top">
<p class="subt">

Lettura

</p>

```php
if(!isset($_COOKIE['Username'])){
    // no valid cookie found
}
else{
    echo "L'username recuperato dal cookie è:";
    echo $_COOKIE["Username"];
}
```

</div>
</div>

In aggiunta a essere per tenere traccia di _utenti autenticati_ e _carrelli_ i _cookie_ possono implementare:

- Funzioni **ricordami** (_persistent cookie_)
- Salvare le preferenze degli utenti
- Tenere traccia del comportamento del browser di un utente

## 2.2. Serializzazione

La **serializzazione** è il processo di prendere _oggetti complicati_ e ridurli a _zero e uno_ per salvarli o trasmetterli.

Il PHP questo processo è molto semplice tramite funzioni `serialize()` e `unserializer()`:

```php
interface Serializable{
    public function serialize();
    public function unserialize($serialized);
}
```

<div class="grid2">
<div class="">

```php
class Artist implements Serializable {
    // ...

    public function serialize() {
        // Utilizzo la funzione built-in
        return serialize(array(
            "earliest" => $this->earliestDate,
            "first" => $this->firstName,
            "last" => $this->lastName,
            "ddate" => $this->deathDate,
            "bdate" => $this->birthDate,
            "bcity" => $this->birthCity,
            "works" => $this->artworks
        ));
    }

    public function unserialize($data) {
        // Utilizzo la funzione built-in
        $data = unserialize($data);
        self::earliestDate = $data['earliest'];
        $this->firstName = $data['first'];
        $this->lastName = $data['last'];
        $this->deathDate = $data['ddate'];
        $this->birthDate = $data['bdate'];
        $this->birthCity = $data['bcity'];
        $this->artworks = $data['works'];
    }

    // ...
}
```

</div>
<div class="">
<img class="70" src="./images/Stato/Serializzazione - Picasso.png">
</div>
</div>

L'output della chiamata `serialize($piasso)` <small>utilizzando la funzione top-level</small> è :

> C:6:"Artist":764:{a:7:{s:8:"earliest";s:13:"Oct 25, 1881";s:5:"firstName";s:5:"Pablo";s:4:"lastName";s:7:"Picasso";s:5:"birthDate";s:13:"Oct 25, 1881";s:5:"deathDate";s:11:"Apl 8, 1973";s:5:"birthCity”;s:6:"Malaga";s:5:"works"; a:3:{i:0;C:8:"Painting":134:{a:2:{s:4:"size”;a:2:{i:0;d:7.7999999999999998;i:1;d:3.5;}s:7:"artData";s:54:"a:2:{s:4:"date";s:4:"1937";s:4:"name";s:8:"Guernica";}";}}i:1;C:9:"Sculpture”:186:{a:2:{s:6:"weight";s:8:"162 tons";s:13:"paintingData"; s:133:"a:2:{s:4:"size";a:1:{i:0;d:15.119999999999999;}s:7:"artData";s:53:”a:2:{s:4:"date";s:4:"1967";s:4:"name";s:7:"Chicago";}";}";}}i:2;C:5:"Movie":175:{a:2:{s:5:"media";s:8:"file.avi";s:13:"paintingData";s:113:"a:2:{s:4:"size";a:2:{i:0;i:32;i:1;i:48;}s:7:"artData";s:50:"a:2:{s:4:"date";s:4:"1968";s:4:"name";s:4:"test";}";}";}}}}}

Se questi dati (salvati in `$data`) sono inseriti nella funzione `$unserialize($data)` istanzieremo un nuovo oggetto **identico all'originale**.

Poiché ad ogni richiesta gli oggetti devono essere ricostruiti, utilizzare la **serializzazione** per recuperare oggetti è un metodo rapido per _mantenere lo stato tra più richieste_.

```php
// --- FILE classa.inc --- //
class classA{
    private $one = 1;
    public function getOne(){echo $this->one;}
}
```

```php
// --- FILE pag1.php --- //
include("classa.inc");
$a = new A;
$s = serialize($a);

file_put_contents('store', $s);
```

```php
// --- FILE pag2.php: --- //
include("classa.inc");

$s = file_get_contents('store');
$a = unserialize($s);

$a->show_one();
```

## 2.3. Stato di Sessione

<div class="grid2">
<div class="">

Dati utenti diversi che accedono alla stessa applicazione web, vorremmo avere degli oggetti sessione diversi per ognuno di loro.

Il **session-state** è un meccanismo _server-side_ che permette di salvare e recuperare oggetti di qualsiasi tipo per ogni _sessione unica di un utente_.

Il **session state** è ideale per salvare più oggetti complessi/strutture dati in una sessione.

</div>
<div class="">

<img class="85" src="./images/Stato/Session State.png">
</div>
</div>

In PHP il _session-state_ si trova nella variabile `$_SESSION`, e ogni sessione viene inizializzata dalla funzione `session_start()`

<div class="grid2">
<div class="top">

```php
session_start();

if(isset($_SESSION['user'])){
    // User è loggato
}
else{
    // Nessuno è loggato
}
```

</div>
<div class="top">

Un esempio di quello a sinstra:

```php
include_once("ShoppingCart.class.php");

session_start();

if(!isset($_SESSION['Cart'])){
    $_SESSION["Cart"] = new ShoppingCart();
}
$cart = $_SESSION["Cart"];
```

</div>
</div>

In _PHP_ le sessioni sono identificate da un _**ID univoco a 32 caratteri**_ che è continuamente scambiato tra l'utente e il server tramite _session un cookie_.

Nel caso di sessioni ex-novo, _PHP_ assegna una collezione stile dizionaria vuota, in grado di tenere traccia di tutti gli stati un questa sessione.
Quando la richiesta è stata processata, il _session state_ è salvato tramite qualche metodo di _storage_ chiamato **session state provider**.
Quasto una nuova richiesta per una sessione esistente arriva, il dizionario recupera i valori precedenti dal **session state provider**.

E' possibile configurare dove i file sono salvati, in memoria o in file.

Mantenere tutte le informazioni riguardo i _session state_ su un'unica macchina può portare a rallentamenti della rete e ad una saturazione della memoria molto rapida.

<div class="grid2">
<div class="">

Un metodo è salvare le informazioni su **più webserver**, tutti collegati ad un **load balancer** al quale l'utente si connetterà, e che smisterà le varie richieste tra i web server

Nel caso in cui le informazioni siano salvate in memoria, richieste smistate a macchine diverse perdono gli stati precedenti.

Alcuni metodi per risolvere sono:

- Rendere il _load balancer_ **session aware**: data una sessione utilizza sempre lo stesso webServer
- Salvare gli stati in un **session server condiviso** tra i _webServer_

</div>
<div class="">

<img class="70" src="./images/Stato/Session Server.png">
</div>
</div>

## 2.4. HTML5 WebStorage

E' un supplemento ai _cookie_, **gestito dal browser**.

A differenza ai _cookie_ non viene trasmesso tra server e browser con ogni richiesta/risposta, e **non ha il limite ai `4KB`**.

Anche di _web storage_ ne esistono due tipi:

- `localStorage`: salva informazioni tra sessioni del browser
- `sessionStorage`: salva informazioni fino alla chiusura del browser

```html
<form ...>
  <h1>Web Storage Writer</h1>
  <script>
    if (
      typeof localStorage === "undefined" ||
      typeof sessionStorage === "undefined"
    ) {
      alert("Web Storage non supportato");
    } else {
      sessionStorage.setItem("TodaysDate", new Date());
      sessionStorage.FavoriteArtist = "Matisse";

      localStorage.UserName = "Riccardo";
      document.write("Web Storage modificato");
    }
  </script>
  <p><a href="WebStorageReader.php">Vai al reader</a></p>
</form>
```

Un modo migliore per pensare ai _Web Storage_ non è come _rimpiazzo ai cookie_, ma come una **cache locale per item statici disponibili al JavaScript**.

Un utilizzo pratico è per salvare contenuti statici scariati in maniera asincrona come `XML` o `JSON` da un _web service_ nel _web storage_, diminuendo il carico sul _server_.
