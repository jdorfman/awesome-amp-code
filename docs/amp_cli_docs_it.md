# Documentazione Non Ufficiale di Amp CLI

---

[Amp](https://ampcode.com) è un agente di codifica AI, in anteprima di ricerca da Sourcegraph. Questa è la CLI per Amp; puoi anche usare [Amp in VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp).

## Indice

- [Documentazione Non Ufficiale di Amp CLI](#documentazione-non-ufficiale-di-amp-cli)
  - [Indice](#indice)
  - [Installazione](#installazione)
  - [Primi Passi](#primi-passi)
  - [Modalità di Utilizzo](#modalità-di-utilizzo)
    - [Modalità Interattiva](#modalità-interattiva)
    - [Modalità Non Interattiva](#modalità-non-interattiva)
  - [Autenticazione](#autenticazione)
    - [Login Basato su Web](#login-basato-su-web)
    - [Autenticazione con Chiave API](#autenticazione-con-chiave-api)
  - [Opzioni della Riga di Comando](#opzioni-della-riga-di-comando)
  - [Comandi](#comandi)
  - [Variabili di Ambiente](#variabili-di-ambiente)
  - [Esempi](#esempi)
  - [Configurazione](#configurazione)
    - [Riferimento delle Impostazioni](#riferimento-delle-impostazioni)
  - [Utilizzo degli Strumenti](#utilizzo-degli-strumenti)
  - [Funzionalità Avanzate](#funzionalità-avanzate)
    - [Navigazione della Cronologia](#navigazione-della-cronologia)
    - [Menzioni di File](#menzioni-di-file)
    - [Debug](#debug)
  - [Risoluzione dei Problemi](#risoluzione-dei-problemi)
    - [Versione di Node.js](#versione-di-nodejs)
    - [Problemi di Autenticazione](#problemi-di-autenticazione)
    - [Crediti Esauriti](#crediti-esauriti)
  - [Requisiti](#requisiti)
  - [Ultimo aggiornamento](#ultimo-aggiornamento)

## Installazione

Installa Amp CLI globalmente usando il tuo gestore di pacchetti preferito:

```bash
npm install -g @sourcegraph/amp
```

O con Yarn:

```bash
yarn global add @sourcegraph/amp
```

O con pnpm:

```bash
pnpm add -g @sourcegraph/amp
```

## Primi Passi

Dopo l'installazione, puoi iniziare a utilizzare Amp CLI immediatamente:

```bash
amp
```

Al primo avvio, Amp ti guiderà attraverso il processo di autenticazione.

## Modalità di Utilizzo

### Modalità Interattiva

La modalità interattiva fornisce un'interfaccia conversazionale dove puoi avere un dialogo con Amp:

```bash
amp
```

In modalità interattiva:

- Digita le tue domande o comandi al prompt (`>`)
- Usa `\` seguito da `Enter` per inserire nuove righe, o usa `Shift+Enter` nei terminali supportati
- Premi `Ctrl+C` per interrompere l'agente o uscire
- Digita `help` per vedere con cosa può aiutarti Amp
- Usa i tasti freccia o Ctrl+P/Ctrl+N per navigare nella cronologia dei messaggi
- Usa PageUp e PageDown per saltare direttamente nella cronologia
- Digita @ seguito da un pattern per cercare e menzionare file in modo fuzzy (usa Tab/Shift+Tab per navigare nei risultati)

### Modalità Non Interattiva

Puoi utilizzare Amp in modalità non interattiva inviando contenuto attraverso pipe:

```bash
echo "commit all my unstaged changes" | amp
```

O usando la redirezione di input/output:

```bash
amp < prompt.txt > output.txt
```

## Autenticazione

Amp CLI supporta due metodi di autenticazione:

### Login Basato su Web

Per impostazione predefinita, Amp utilizza un flusso di login basato su web:

1. Esegui `amp` per la prima volta
2. Si aprirà una finestra del browser per autenticarti con ampcode.com
3. Dopo l'autenticazione riuscita, puoi continuare a utilizzare Amp CLI

### Autenticazione con Chiave API

Puoi anche autenticarti utilizzando le chiavi API:

1. Vai su [ampcode.com/settings](https://ampcode.com/settings)
2. Copia la tua chiave API
3. Impostala come variabile di ambiente:

```bash
export AMP_API_KEY=[REDACTED:api-key]
```

## Opzioni della Riga di Comando

Amp CLI supporta le seguenti opzioni:

| Opzione                      | Descrizione                                                          |
| ---------------------------- | -------------------------------------------------------------------- |
| `-V, --version`              | Mostra il numero di versione                                        |
| `--visibility <visibility>`  | Imposta la visibilità del thread (private, public, team)           |
| `--notifications`            | Abilita notifiche sonore (abilitate per impostazione predefinita quando interattivo) |
| `--no-notifications`         | Disabilita notifiche sonore                                         |
| `--settings-file <value>`    | Percorso personalizzato del file delle impostazioni (sovrascrive la posizione predefinita) |
| `--log-level <value>`        | Imposta il livello di log (error, warn, info, debug, audit)        |
| `--log-file <value>`         | Imposta la posizione del file di log                               |
| `--dangerously-allow-all`    | Disabilita tutti i prompt di conferma dei comandi (l'agente eseguirà tutti i comandi senza chiedere) |

## Comandi

Amp CLI include diversi sottocomandi per funzionalità avanzate:

| Comando                    | Descrizione                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| `logout`                   | Disconnettiti rimuovendo la chiave API memorizzata                  |
| `login`                    | Accedi ad Amp                                                        |
| `threads`                  | Comandi di gestione dei thread                                      |
| `threads new`              | Crea un nuovo thread e stampa il suo ID                            |
| `threads continue`         | Continua un thread esistente (usa l'ultimo thread utilizzato se non viene fornito l'ID) |
| `threads fork`             | Crea un nuovo thread facendo il fork di uno esistente e stampa il suo ID |
| `threads list`             | Elenca tutti i tuoi thread con i loro titoli e stato di condivisione |
| `threads share`            | Cambia la visibilità del thread o condividi con il supporto        |
| `threads compact`          | Compatta un thread creando un riassunto per ridurre l'uso dei token |
| `tools`                    | Comandi di gestione degli strumenti                                 |
| `tools show`               | Mostra gli strumenti disponibili                                    |
| `doctor`                   | Genera un bundle di supporto per la risoluzione dei problemi       |
| `update`                   | Aggiorna Amp CLI all'ultima versione                               |

## Variabili di Ambiente

| Variabile           | Descrizione                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `AMP_API_KEY`       | Chiave API per Amp (vedi https://ampcode.com/settings)             |
| `AMP_URL`           | URL per il servizio Amp (predefinito è https://ampcode.com/)       |
| `AMP_LOG_LEVEL`     | Imposta il livello di log (può anche usare --log-level)            |
| `AMP_LOG_FILE`      | Imposta la posizione del file di log (può anche usare --log-file)  |
| `AMP_SETTINGS_FILE` | Imposta il percorso del file delle impostazioni (può anche usare --settings-file, predefinito: ~/.config/amp/settings.json) |

## Esempi

Avvia una sessione interattiva:

```bash
amp
```

Esegui un comando in una sessione non interattiva:

```bash
echo "commit all my unstaged changes" | amp
```

Esegui da un file di prompt in una sessione non interattiva e memorizza l'output in un file:

```bash
amp < prompt.txt > output.txt
```

## Configurazione

Amp può essere configurato utilizzando un file di impostazioni JSON situato in `~/.config/amp/settings.json`. Tutte le impostazioni utilizzano il prefisso "amp.".

Configurazione di esempio:

```json
{
  "amp.notifications.enabled": true,
  "amp.mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-filesystem",
        "/path/to/allowed/dir"
      ]
    }
  },
  "amp.tools.disable": [
    "browser_navigate",
    "builtin:edit_file"
  ],
  "amp.commands.allowlist": [
    "git status",
    "ls -la",
    "npm run build"
  ],
  "amp.commands.strict": false,
  "amp.dangerouslyAllowAll": false,
  "amp.git.commit.coauthor.enabled": true,
  "amp.git.commit.ampThread.enabled": true,
  "amp.updates.autoUpdate.enabled": true
}
```

### Riferimento delle Impostazioni

- **`amp.notifications.enabled`**: Abilita notifiche sonore di sistema quando l'agente completa le attività
- **`amp.mcpServers`**: Server Model Context Protocol a cui connettersi per strumenti aggiuntivi
- **`amp.tools.disable`**: Array di nomi di strumenti da disabilitare. Usa 'builtin:toolname' per disabilitare solo lo strumento builtin con quel nome (permettendo a un server MCP di fornire uno strumento con quel nome).
- **`amp.commands.allowlist`**: Array di comandi shell che possono essere eseguiti senza conferma
- **`amp.commands.strict`**: Abilita la validazione rigorosa dei comandi. Quando disabilitato, certi comandi come Bazel ottengono una validazione del percorso rilassata.
- **`amp.dangerouslyAllowAll`**: Disabilita tutti i prompt di conferma dei comandi (l'agente eseguirà tutti i comandi senza chiedere)
- **`amp.git.commit.coauthor.enabled`**: Abilita l'aggiunta di Amp come co-autore nei commit git
- **`amp.git.commit.ampThread.enabled`**: Abilita l'aggiunta del trailer Amp-Thread nei commit git
- **`amp.updates.autoUpdate.enabled`**: Abilita aggiornamenti automatici di Amp CLI

## Utilizzo degli Strumenti

Amp può utilizzare vari strumenti per aiutarti con le tue attività. Quando Amp vuole utilizzare uno strumento (come eseguire un comando del terminale), chiederà la tua conferma:

```
Amp wants to run: git status

Allow this command? [y/n/!]
```

Opzioni:

- `y`: Consenti questo comando una volta
- `n`: Rifiuta questo comando
- `!`: Consenti e aggiungi all'allowlist (non chiederà più per questo comando)

## Funzionalità Avanzate

### Navigazione della Cronologia

Amp CLI ti permette di navigare nella cronologia dei tuoi messaggi:

- Usa i tasti freccia o `Ctrl+P`/`Ctrl+N` per navigare tra i messaggi adiacenti nella cronologia
- I tasti `PageUp` e `PageDown` saltano direttamente nella cronologia indipendentemente dalla posizione del cursore
- La tua bozza corrente è disponibile alla fine della cronologia
- Premi `Ctrl+C` o `Esc` per annullare e tornare alla tua bozza

### Menzioni di File

Puoi fare riferimento rapidamente ai file nella CLI utilizzando la funzione di menzione dei file:

- Digita `@` seguito da un pattern per iniziare la ricerca fuzzy dei file
- Usa Tab o `Shift+Tab` per navigare nei risultati della ricerca
- Premi `Enter` per confermare e inserire la menzione del file

### Debug

Per scopi di debug, puoi utilizzare:

```bash
amp --log-level debug --log-file amp.log
```



## Risoluzione dei Problemi

### Versione di Node.js

Amp CLI richiede Node.js v22 o superiore. Se incontri errori, controlla la tua versione di Node.js:

```bash
node --version
```

### Problemi di Autenticazione

Se hai problemi con l'autenticazione basata su web, prova a utilizzare il metodo della chiave API descritto nella sezione [Autenticazione](#autenticazione).

### Crediti Esauriti

Se vedi un messaggio "Out of free credits", visita [ampcode.com/settings](https://ampcode.com/settings) per aggiornare il tuo account.

## Requisiti

- Node.js v22 o superiore
- Connessione internet

## Ultimo aggiornamento

2025-07-23
