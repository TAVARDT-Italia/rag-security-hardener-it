# Hub di Hardening e Blindatura di Sicurezza per Pipeline RAG

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-italia.github.io/rag-security-hardener-it/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![OWASP LLM](https://img.shields.io/badge/OWASP-LLM%20Top%2010-red.svg)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
[![MITRE ATLAS](https://img.shields.io/badge/MITRE-ATLAS%20Matrix-orange.svg)](https://atlas.mitre.org/)

**Hub di Architettura Difensiva e Blueprint di Blindatura per Pipeline RAG (Retrieval-Augmented Generation)**

Sviluppato e gestito dalla divisione di ingegneria della sicurezza in intelligenza artificiale di **TAVARDT**.

***

## Dimostrazione Online & Hub di Architettura Difensiva

È possibile consultare le specifiche tecniche difensive, i test di diagnostica architetturale e i blueprint di mitigazione direttamente dal browser:

* **[Applicazione Web Ufficiale su GitHub Pages](https://tavardt-italia.github.io/rag-security-hardener-it/)**
* **Centro Strumenti TAVARDT**

> [!NOTE]
> **Ambito di Esecuzione Tecnica:** Questo hub web fornisce specifiche di architettura difensiva e blueprint di configurazione. I controlli attivi dei database vettoriali e dell'integrità del contesto richiedono credenziali di ambiente e devono essere eseguiti all'interno dell'applicazione mediante l'utilità CLI ufficiale (`rag_security_auditor.py`). Le pagine web caricate nella sandbox del browser non possono connettersi direttamente ai cluster vettoriali privati.

***

## Blueprint Tecnici di Hardening

1. **rag-security-policy.yml:** Politiche di sicurezza aziendali che definiscono limiti di chunk, tag XML di isolamento del contesto e regole di validazione semantica.
2. **rag_chunk_sanitizer.py:** Pipeline di sanificazione per rimuovere caratteri invisibili Unicode, sequenze di escape e marker di prompt injection prima di generare gli embedding.
3. **vector_acl_filter.json:** Schema di query vettoriale che impone filtri obbligatori di controllo degli accessi (RBAC/ACL) per utente e tenant per prevenire l'esfiltrazione tra organizzazioni.
4. **rag_context_template.xml:** Template di incapsulamento del contesto delimitato da tag XML con direttive rigide di non esecuzione per modelli LLM.
5. **rag_security_auditor.py:** Utilità CLI locale deterministica eseguita nell'ambiente dell'applicazione per esaminare direttamente le configurazioni delle pipeline RAG e convalidare la conformità OWASP LLM.

***

## Utilizzo dell'Utilità CLI Deterministica

Per eseguire l'ispezione deterministica direttamente nell'ambiente dell'applicazione RAG:

```bash
# 1. Scaricare lo script di audit dal repository ufficiale
curl -sO https://raw.githubusercontent.com/TAVARDT-Italia/rag-security-hardener-it/main/rag_security_auditor.py

# 2. Ispezionare la pipeline e le specifiche difensive
python3 rag_security_auditor.py

# 3. Esportare i risultati in formato JSON strutturato
python3 rag_security_auditor.py -json
```

***

## Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

© 2026 TAVARDT. Tutti i diritti riservati.
