# OWASP Web Application Security Testing Checklist

## Tabella dei Contenuti

* [Information Gathering](#Information)
* [Configuration Management](#Configuration)
* [Secure Transmission](#Transmission)
* [Authentication](#Authentication)
* [Session Management](#Session)
* [Authorization](#Authorization)
* [Data Validation](#Validation)
* [Denial of Service](#Denial)
* [Business Logic](#Business)
* [Cryptography](#Cryptography)
* [Risky Functionality - File Uploads](#File)
* [Risky Functionality - Card Payment](#Card)
* [HTML 5](#HTML)

-------
### <a name="Information">Information Gathering</a>
- [ ] Esplorare manualmente il sito
- [ ] Usare spider/crawler per contenuti nascosti o mancanti
- [ ] Controllare file che espongono contenuti, come robots.txt, sitemap.xml, .DS_Store
- [ ] Controllare le cache dei principali motori di ricerca per siti accessibili pubblicamente
- [ ] Controllare le differenze nei contenuti basate sull'User Agent (es. siti mobili, accesso come crawler dei motori di ricerca)
- [ ] Eseguire il fingerprinting dell'applicazione web
- [ ] Identificare le tecnologie utilizzate
- [ ] Identificare i ruoli degli utenti
- [ ] Identificare i punti di ingresso dell'applicazione
- [ ] Identificare il codice lato client
- [ ] Identificare più versioni/canali (es. web, web mobile, app mobile, servizi web)
- [ ] Identificare applicazioni co-ospitate e correlate
- [ ] Identificare tutti i nomi host e le porte
- [ ] Identificare contenuti ospitati da terze parti


### <a name="Configuration">Configuration Management</a>
- [ ] Controllare URL comunemente usati per applicazioni e amministrazione
- [ ] Controllare file vecchi, di backup e non referenziati
- [ ] Controllare i metodi HTTP supportati e il Cross Site Tracing (XST)
- [ ] Testare la gestione delle estensioni dei file
- [ ] Testare gli header di sicurezza HTTP (es. CSP, X-Frame-Options, HSTS)
- [ ] Testare le policy (es. Flash, Silverlight, robots)
- [ ] Controllare dati non di produzione in ambiente live, e viceversa
- [ ] Controllare dati sensibili nel codice lato client (es. chiavi API, credenziali)


### <a name="Transmission">Secure Transmission</a>
- [ ] Controllare versione SSL, algoritmi, lunghezza chiave
- [ ] Controllare la validità del certificato digitale (durata, firma e CN)
- [ ] Controllare che le credenziali siano consegnate solo tramite HTTPS
- [ ] Controllare che il modulo di login sia consegnato tramite HTTPS
- [ ] Controllare che i token di sessione siano consegnati solo tramite HTTPS
- [ ] Controllare se è in uso HTTP Strict Transport Security (HSTS)


### <a name="Authentication">Authentication</a>
- [ ] Testare l'enumerazione degli utenti
- [ ] Testare il bypass dell'autenticazione
- [ ] Testare la protezione contro il brute force
- [ ] Testare le regole di qualità delle password
- [ ] Testare la funzionalità "ricordami"
- [ ] Testare l'autocompletamento nei moduli/input delle password
- [ ] Testare il processo di reset e/o recupero delle password
- [ ] Testare il processo di cambio password
- [ ] Testare il CAPTCHA
- [ ] Testare l'autenticazione a più fattori
- [ ] Testare la presenza della funzionalità di logout
- [ ] Testare la gestione della cache su HTTP (es. Pragma, Expires, Max-age)
- [ ] Testare i login di default
- [ ] Testare la cronologia dell'autenticazione accessibile dall'utente
- [ ] Testare la notifica fuori canale di blocchi dell'account e cambiamenti di password riusciti
- [ ] Testare l'autenticazione coerente tra applicazioni con schema di autenticazione condiviso / SSO


### <a name="Session">Session Management</a>
- [ ] Stabilire come viene gestita la sessione nell'applicazione (es. token nei cookie, token nell'URL)
- [ ] Controllare i token di sessione per i flag dei cookie (httpOnly e secure)
- [ ] Controllare l'ambito dei cookie di sessione (path e dominio)
- [ ] Controllare la durata dei cookie di sessione (expires e max-age)
- [ ] Controllare la terminazione della sessione dopo un tempo massimo di vita
- [ ] Controllare la terminazione della sessione dopo un timeout relativo
- [ ] Controllare la terminazione della sessione dopo il logout
- [ ] Testare se gli utenti possono avere più sessioni simultanee
- [ ] Testare i cookie di sessione per la casualità
- [ ] Confermare che nuovi token di sessione siano emessi al login, cambio di ruolo e logout
- [ ] Testare la gestione coerente delle sessioni tra applicazioni con gestione delle sessioni condivisa
- [ ] Testare il session puzzling
- [ ] Testare il CSRF e il clickjacking


### <a name="Authorization">Authorization</a>
- [ ] Testare il path traversal
- [ ] Testare il bypass dello schema di autorizzazione
- [ ] Testare i problemi di controllo degli accessi verticali (escalation dei privilegi)
- [ ] Testare i problemi di controllo degli accessi orizzontali (tra due utenti allo stesso livello di privilegio)
- [ ] Testare l'assenza di autorizzazione


### <a name="Validation">Data Validation</a>
- [ ] Test per Reflected Cross Site Scripting
- [ ] Test per Stored Cross Site Scripting
- [ ] Test per DOM based Cross Site Scripting
- [ ] Test per Cross Site Flashing
- [ ] Test per HTML Injection
- [ ] Test per SQL Injection
- [ ] Test per SOQL Injection
- [ ] Test per LDAP Injection
- [ ] Test per ORM Injection
- [ ] Test per XML Injection
- [ ] Test per XXE Injection
- [ ] Test per SSI Injection
- [ ] Test per XPath Injection
- [ ] Test per XQuery Injection
- [ ] Test per IMAP/SMTP Injection
- [ ] Test per Code Injection
- [ ] Test per Expression Language Injection
- [ ] Test per Command Injection
- [ ] Test per Overflow (Stack, Heap and Integer)
- [ ] Test per Format String
- [ ] Test per le vulnerabilità incubate
- [ ] Test per HTTP Splitting/Smuggling
- [ ] Test per HTTP Verb Tampering
- [ ] Test per Open Redirection
- [ ] Test per Local File Inclusion
- [ ] Test per Remote File Inclusion
- [ ] Confrontare le regole di validazione lato client e lato server
- [ ] Test per NoSQL injection
- [ ] Test per HTTP parameter pollution
- [ ] Test per auto-binding
- [ ] Test per Mass Assignment
- [ ] Test per NULL/Invalid Session Cookie



### <a name="Denial">Denial of Service</a>
- [ ] Testare l'anti-automazione
- [ ] Testare il blocco dell'account
- [ ] Testare il DoS del protocollo HTTP
- [ ] Testare il DoS dei caratteri wildcard SQL


### <a name="Business">Business Logic</a>
- [ ] Testare l'uso improprio delle funzionalità
- [ ] Testare la mancanza di non ripudio
- [ ] Testare le relazioni di fiducia
- [ ] Testare l'integrità dei dati
- [ ] Testare la segregazione dei ruoli


### <a name="Cryptography">Cryptography</a>
- [ ] Controllare se i dati che dovrebbero essere crittografati non lo sono
- [ ] Controllare l'uso di algoritmi sbagliati a seconda del contesto
- [ ] Controllare l'uso di algoritmi deboli
- [ ] Controllare l'uso corretto del salting
- [ ] Controllare le funzioni di casualità


### <a name="File">Risky Functionality - File Uploads</a>
- [ ] Testare che i limiti di dimensione dei file, la frequenza di caricamento e il numero totale di file siano definiti e applicati
- [ ] Testare che i contenuti dei file corrispondano al tipo di file definito
- [ ] Testare che tutti i caricamenti di file abbiano la scansione antivirus in atto
- [ ] Testare che i nomi di file non sicuri siano sanificati
- [ ] Testare che i file caricati non siano direttamente accessibili nella radice web
- [ ] Testare che i file caricati non siano serviti sullo stesso nome host/porta
- [ ] Testare che i file e altri media siano integrati con gli schemi di autenticazione e autorizzazione


### <a name="Card">Risky Functionality - Card Payment</a>
- [ ] Testare le vulnerabilità note e i problemi di configurazione sul server web e sull'applicazione web
- [ ] Testare le password di default o indovinabili
- [ ] Testare i dati non di produzione in ambiente live, e viceversa
- [ ] Testare le vulnerabilità di iniezione
- [ ] Testare i buffer overflow
- [ ] Testare l'archiviazione crittografica non sicura
- [ ] Testare la protezione insufficiente del livello di trasporto
- [ ] Testare la gestione impropria degli errori
- [ ] Testare tutte le vulnerabilità con un punteggio CVSS v2 > 4.0
- [ ] Testare i problemi di autenticazione e autorizzazione
- [ ] Testare il CSRF


### <a name="HTML">HTML 5</a>
- [ ] Testare la messaggistica web
- [ ] Testare l'iniezione SQL nello storage web
- [ ] Controllare l'implementazione CORS
- [ ] Controllare l'applicazione web offline
