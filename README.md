<p align="center">
  <a href="https://ag.tavardt.com/it/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Hub di Hardening e Blindatura di Sicurezza per Pipeline RAG

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-italia.github.io/rag-security-hardener-it/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Motore di valutazione della sicurezza e blindatura contestuale per architetture RAG (Retrieval-Augmented Generation) sviluppato da **TAVARDT**. Ispirato agli standard OWASP LLM01, OWASP LLM04, OWASP LLM07 e MITRE ATLAS, questo toolkit controlla l'isolamento vettoriale multi-tenant, neutralizza le iniezioni indirette e genera middleware protettivi.

***

## Funzionalità Principali e Architettura Difensiva

* **Audit Deterministico delle Pipeline**: Valida la segregazione contestuale, i filtri sui metadati e i vincoli di chunking secondo specifiche formali di sicurezza.
* **Generazione Automatica di Middleware**: Esporta classi Python modulari configurate per sanificare il contesto estratto e imporre un rigoroso incapsulamento XML.
* **Verifica dell'Isolamento Multi-Tenant**: Certifica che le query nel database vettoriale richiedano filtri di metadati validati per impedire la diffusione non autorizzata di dati.

***

## Vettori di Rischio e Impatto Operativo

Elaborare flussi RAG senza un isolamento strutturato del contesto consente a istruzioni malevole nascoste in documenti esterni di alterare l'output del modello e sottrarre dati riservati. Il toolkit esamina cinque aree critiche di sicurezza:

* **Integrità dell'Ingestione Documentale**: Esamina le pipeline di caricamento contro iniezioni steganografiche in PDF, codici di controllo unicode e formati ostili (Deduzione: fino a -25 punti).
* **Isolamento Multi-Tenant nel Database Vettoriale**: Individua collezioni condivise prive di compartimentazione per namespace o metadati di controllo degli accessi (Deduzione: fino a -30 punti).
* **Incapsulamento dei Limiti Contestuali**: Blocca la concatenazione diretta del testo imponendo tag XML rigorosi con divieto esplicito di esecuzione comandi (Deduzione: fino a -25 punti).
* **Filtraggio delle Iniezioni Indirette nei Prompt**: Impiega filtri a espressioni regolari per neutralizzare istruzioni manipolative annidate nei frammenti di testo (Deduzione: fino a -20 punti).
* **Gate di Validazione dell'Output e Mascheramento**: Applica verifiche di attribuzione e filtri regex per oscurare informazioni sensibili prima della risposta (Deduzione: fino a -15 punti).

I sistemi sottoposti ad audit conseguono un punteggio complessivo da 10 a 100 punti. Il modello assegna verdetti operativi inequivocabili: **HARDENED** (da 85 a 100 punti), **MODERATE** (da 50 a 84 punti) o **CRITICAL** (inferiore a 50 punti), bloccando i rilasci non sicuri.

***

## Installazione ed Esecuzione CLI

Valutate la sicurezza delle vostre architetture o esportate moduli di middleware con comandi Python standard:

```bash
# Clonare il repository ufficiale
git clone https://github.com/TAVARDT-Italia/rag-security-hardener-it.git

# Accedere alla directory di lavoro
cd rag-security-hardener-it

# Valutare la pipeline RAG su tutti i livelli difensivi
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3

# Esportare il middleware di protezione in Python
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3 -e defensive_rag_middleware.py

# Esportare il report strutturato in formato JSON
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3 -j
```

***

## FAQ Tecniche

### Quali vettori di vulnerabilità analizza il kit di sicurezza RAG all'interno delle pipeline di recupero?

Lo strumento controlla le pipeline contro l'ingestione di documenti non autenticati, perdite cross-tenant nel database vettoriale, violazioni dei limiti di contesto, iniezioni indirette e risposte non verificate. I sistemi analizzati conseguono un punteggio difensivo compreso tra 10 e 100 punti, classificato in HARDENED, MODERATE o CRITICAL.

### Come previene le iniezioni indirette l'incapsulamento del contesto tramite delimitatori XML?

Racchiudere i frammenti documentali recuperati entro tag XML rigorosi separa nettamente le informazioni esterne dalle istruzioni operative di sistema. Questa separazione impedisce che comandi malevoli inseriti in testi di terze parti vengano interpretati dal modello linguistico come direttive vincolanti.

### Perché il filtraggio dei metadati di tenant è fondamentale nei database vettoriali multi-tenant?

Senza un rigoroso isolamento degli spazi dei nomi o controlli sui metadati, le interrogazioni di similarità semantica possono recuperare dati riservati di altri clienti. L'imposizione di vincoli di accesso in fase di query elimina il rischio di dispersione laterale di informazioni protette tra organizzazioni diverse.

### Quali difese operative assicura il blueprint di middleware esportato dal toolkit?

La generazione del middleware tramite l'opzione -e fornisce una classe difensiva Python pronta a ripulire i pattern ostili e normalizzare i delimitatori prima della composizione del prompt. Tale presidio di sicurezza intercetta tentativi di sovrascrittura delle istruzioni e richieste di esfiltrazione di credenziali durante l'esecuzione.

### Il kit di hardening può essere impiegato per controlli automatizzati nelle pipeline CI/CD?

Le interfacce CLI analizzano parametri architetturali o file di configurazione generando report strutturati tramite l'opzione -j. Le procedure automatizzate di integrazione possono interrogare la valutazione JSON per bloccare tempestivamente rilasci che non soddisfano gli standard di sicurezza.

***

## Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

### Licenza
Rilasciato sotto licenza MIT. Consultare [LICENSE](LICENSE) per tutti i dettagli.

***

© 2026 TAVARDT. Tutti i diritti riservati.
