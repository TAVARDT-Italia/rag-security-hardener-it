# Validatore e Blindatura di Sicurezza per Pipeline RAG - TAVARDT Italia

> Audit di Isolamento del Contesto, Prevenzione Iniezioni Indirette e Protezione Difensiva dell'IA

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Active-brightgreen)](https://tavardt-italia.github.io/rag-security-hardener-it/)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Security: OWASP LLM](https://img.shields.io/badge/Security-OWASP%20LLM01%20%7C%20LLM02-red.svg)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

## Panoramica dell'Architettura e Sicurezza RAG

L'architettura RAG (Retrieval-Augmented Generation) introduce vettori critici di vulnerabilità nelle applicazioni aziendali di intelligenza artificiale. L'ingestione di documenti e basi di conoscenza espone l'applicazione a rischi di Iniezione Indiretta di Prompt (OWASP LLM01) e Perdita di Dati Multi-Tenant (OWASP LLM02).

Questo repository fornisce un'applicazione web interattiva con esecuzione 100% nel browser e un comando CLI in Python per verificare le architetture RAG e generare blueprint difensivi.

## Applicazione Web Interattiva

Accedi allo strumento online e verifica la tua pipeline in tempo reale:

- [https://tavardt-italia.github.io/rag-security-hardener-it/](https://tavardt-italia.github.io/rag-security-hardener-it/)

## Utilizzo dello Scanner CLI (Python)

Lo strumento `rag_security_hardener.py` opera esclusivamente con la libreria standard di Python (nessuna dipendenza di terze parti) e consente di automatizzare l'audit nelle pipeline CI/CD o in ambiente locale.

```bash
# Executar avaliacao interativa com parametros padrao
python rag_security_hardener.py

# Exportar middleware defensivo para uso imediato em seu pipeline
python rag_security_hardener.py --export-blueprint secure_rag_middleware.py

# Executar auditoria em modo JSON para integracao em CI/CD
python rag_security_hardener.py --ingestion 3 --vector-db 3 --context-boundary 3 --indirect-filter 3 --json
```

## Controlli Architetturali e Mitigazioni Difensive

1. **Isolamento del Contesto**: Incapsulamento rigoroso dei blocchi di contesto con tag XML (`<untrusted_context>`) e istruzioni di sistema blindate.
2. **Prevenzione Iniezioni Indirette**: Sanificazione euristica delle istruzioni incorporate nei documenti ingeriti.
3. **Isolamento Multi-Tenant (RBAC)**: Separazione rigorosa dei vettori tramite namespace e verifica delle autorizzazioni a ogni query.
4. **Gate di Uscita e Controllo Citazioni**: Verifica dell'attribuzione delle risposte e mascheramento attivo dei dati riservati.

## Portali Ufficiali

- **Portale Ufficiale TAVARDT**: [https://ag.tavardt.com/it/](https://ag.tavardt.com/it/)
- **Centro Strumenti**: [https://tools.tavardt.com/it/](https://tools.tavardt.com/it/)
- **Contatti**: [https://ag.tavardt.com/it/contact/](https://ag.tavardt.com/it/contact/)

---
&copy; 2026 TAVARDT Italia. Tutti i diritti riservati.
