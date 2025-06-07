# Inoffizielle Amp CLI Dokumentation

---

[Amp](https://ampcode.com) ist ein KI-Programmieragent in der Forschungsvorschau von Sourcegraph. Dies ist die CLI für Amp; Sie können auch [Amp in VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp) verwenden.

## Inhaltsverzeichnis

- [Inoffizielle Amp CLI Dokumentation](#inoffizielle-amp-cli-dokumentation)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Installation](#installation)
  - [Erste Schritte](#erste-schritte)
  - [Verwendungsmodi](#verwendungsmodi)
    - [Interaktiver Modus](#interaktiver-modus)
    - [Nicht-interaktiver Modus](#nicht-interaktiver-modus)
  - [Authentifizierung](#authentifizierung)
    - [Web-basierte Anmeldung](#web-basierte-anmeldung)
    - [API-Schlüssel-Authentifizierung](#api-schlüssel-authentifizierung)
  - [Kommandozeilenoptionen](#kommandozeilenoptionen)
  - [Befehle](#befehle)
  - [Umgebungsvariablen](#umgebungsvariablen)
  - [Beispiele](#beispiele)
  - [Konfiguration](#konfiguration)
    - [Einstellungsreferenz](#einstellungsreferenz)
  - [Tool-Verwendung](#tool-verwendung)
  - [Erweiterte Funktionen](#erweiterte-funktionen)
    - [Verlaufsnavigation](#verlaufsnavigation)
    - [Dateierwähnungen](#dateierwähnungen)
    - [Debugging](#debugging)
  - [Problembehandlung](#problembehandlung)
    - [Node.js Version](#nodejs-version)
    - [Authentifizierungsprobleme](#authentifizierungsprobleme)
    - [Keine Guthaben](#keine-guthaben)
  - [Anforderungen](#anforderungen)
  - [Zuletzt aktualisiert](#zuletzt-aktualisiert)

## Installation

Installieren Sie die Amp CLI global mit Ihrem bevorzugten Paketmanager:

```bash
npm install -g @sourcegraph/amp
```

Oder mit Yarn:

```bash
yarn global add @sourcegraph/amp
```

Oder mit pnpm:

```bash
pnpm add -g @sourcegraph/amp
```

## Erste Schritte

Nach der Installation können Sie Amp CLI sofort verwenden:

```bash
amp
```

Beim ersten Start führt Sie Amp durch den Authentifizierungsprozess.

## Verwendungsmodi

### Interaktiver Modus

Der interaktive Modus bietet eine Gesprächsschnittstelle, in der Sie einen Dialog mit Amp führen können:

```bash
amp
```

Im interaktiven Modus:

- Geben Sie Ihre Fragen oder Befehle an der Eingabeaufforderung (`>`) ein
- Verwenden Sie `\` gefolgt von `Enter`, um Zeilenumbrüche einzufügen, oder verwenden Sie `Shift+Enter` in unterstützten Terminals
- Drücken Sie `Ctrl+C`, um den Agenten zu unterbrechen oder zu beenden
- Geben Sie `help` ein, um zu sehen, wobei Amp Ihnen helfen kann
- Verwenden Sie die Pfeiltasten oder Ctrl+P/Ctrl+N, um durch den Nachrichtenverlauf zu navigieren
- Verwenden Sie PageUp und PageDown, um direkt im Verlauf zu springen
- Geben Sie @ gefolgt von einem Muster ein, um Dateien per Fuzzy-Suche zu finden und zu erwähnen (verwenden Sie Tab/Shift+Tab, um durch die Ergebnisse zu navigieren)

### Nicht-interaktiver Modus

Sie können Amp im nicht-interaktiven Modus verwenden, indem Sie Inhalte an ihn weiterleiten:

```bash
echo "commit all my unstaged changes" | amp
```

Oder durch Verwendung von Ein-/Ausgabeumleitung:

```bash
amp < prompt.txt > output.txt
```

## Authentifizierung

Amp CLI unterstützt zwei Authentifizierungsmethoden:

### Web-basierte Anmeldung

Standardmäßig verwendet Amp einen web-basierten Anmeldevorgang:

1. Führen Sie `amp` zum ersten Mal aus
2. Ein Browserfenster wird geöffnet, um sich bei ampcode.com zu authentifizieren
3. Nach erfolgreicher Authentifizierung können Sie Amp CLI weiter verwenden

### API-Schlüssel-Authentifizierung

Sie können sich auch mit API-Schlüsseln authentifizieren:

1. Gehen Sie zu [ampcode.com/settings](https://ampcode.com/settings)
2. Kopieren Sie Ihren API-Schlüssel
3. Setzen Sie ihn als Umgebungsvariable:

```bash
export AMP_API_KEY=[REDACTED:api-key]
```

## Kommandozeilenoptionen

Amp CLI unterstützt die folgenden Optionen:

| Option                    | Beschreibung                                                         |
| ------------------------- | -------------------------------------------------------------------- |
| `-h, --help`              | Hilfeinformationen anzeigen                                         |
| `-V, --version`           | Versionsnummer ausgeben                                              |
| `--thread-id [THREAD_ID]` | ID des Threads, der fortgesetzt werden soll                         |
| `--notifications`         | Tonbenachrichtigungen aktivieren (standardmäßig aktiviert wenn interaktiv) |
| `--no-notifications`      | Tonbenachrichtigungen deaktivieren                                   |
| `--color`                 | Farbausgabe aktivieren (standardmäßig aktiviert wenn stdout und stderr an ein TTY gesendet werden) |
| `--no-color`              | Farbausgabe deaktivieren                                             |
| `--settings-file <value>` | Benutzerdefinierter Einstellungsdateipfad (überschreibt den Standardort) |
| `--log-level <value>`     | Log-Level setzen (error, warn, info, debug, audit)                  |
| `--log-file <value>`      | Log-Datei-Speicherort setzen                                        |

## Befehle

Amp CLI enthält mehrere Unterbefehle für erweiterte Funktionalität:

| Befehl              | Beschreibung                                                         |
| ------------------- | -------------------------------------------------------------------- |
| `logout`            | Abmelden durch Entfernen des gespeicherten API-Schlüssels           |
| `login`             | Bei Amp anmelden                                                     |
| `threads`           | Thread-Verwaltungsbefehle                                            |
| `threads new`       | Neuen Thread erstellen und seine ID ausgeben                        |
| `threads continue`  | Vorhandenen Thread fortsetzen (verwendet zuletzt verwendeten Thread wenn keine ID angegeben) |
| `threads fork`      | Neuen Thread durch Verzweigung eines vorhandenen erstellen und seine ID ausgeben |
| `threads list`      | Alle Ihre Threads mit ihren Titeln und Freigabestatus auflisten     |
| `tools`             | Tool-Verwaltungsbefehle                                              |
| `tools show`        | Verfügbare Tools anzeigen                                            |

## Umgebungsvariablen

| Variable            | Beschreibung                                                         |
| ------------------- | -------------------------------------------------------------------- |
| `AMP_API_KEY`       | API-Schlüssel für Amp (siehe https://ampcode.com/settings)          |
| `AMP_URL`           | URL für den Amp-Service (Standard ist https://ampcode.com/)         |
| `AMP_LOG_LEVEL`     | Log-Level setzen (kann auch --log-level verwenden)                  |
| `AMP_LOG_FILE`      | Log-Datei-Speicherort setzen (kann auch --log-file verwenden)       |
| `AMP_SETTINGS_FILE` | Einstellungsdateipfad setzen (kann auch --settings-file verwenden, Standard: ~/.config/amp/settings.json) |

## Beispiele

Eine interaktive Sitzung starten:

```bash
amp
```

Einen Befehl in einer nicht-interaktiven Sitzung ausführen:

```bash
echo "commit all my unstaged changes" | amp
```

Von einer Prompt-Datei in einer nicht-interaktiven Sitzung ausführen und Ausgabe in einer Datei speichern:

```bash
amp < prompt.txt > output.txt
```

## Konfiguration

Amp kann über eine JSON-Einstellungsdatei konfiguriert werden, die sich unter `~/.config/amp/settings.json` befindet. Alle Einstellungen verwenden das Präfix "amp.".

Beispielkonfiguration:

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
  "amp.mcp.disable": [],
  "amp.tools.disable": [
    "browser_navigate"
  ],
  "amp.commands.allowlist": [
    "git status",
    "ls -la",
    "npm run build"
  ]
}
```

### Einstellungsreferenz

- **`amp.notifications.enabled`**: System-Tonbenachrichtigungen aktivieren, wenn der Agent Aufgaben abschließt
- **`amp.mcpServers`**: Model Context Protocol Server, mit denen für zusätzliche Tools eine Verbindung hergestellt werden soll
- **`amp.mcp.disable`**: Array von MCP-Servernamen, die deaktiviert werden sollen
- **`amp.tools.disable`**: Array von Tool-Namen, die deaktiviert werden sollen
- **`amp.commands.allowlist`**: Array von Shell-Befehlen, die ohne Bestätigung ausgeführt werden können

## Tool-Verwendung

Amp kann verschiedene Tools verwenden, um bei Ihren Aufgaben zu helfen. Wenn Amp ein Tool verwenden möchte (wie das Ausführen eines Terminalbefehls), wird es um Ihre Bestätigung bitten:

```
Amp wants to run: git status

Allow this command? [y/n/!]
```

Optionen:

- `y`: Diesen Befehl einmal erlauben
- `n`: Diesen Befehl ablehnen
- `!`: Erlauben und zur Erlaubnisliste hinzufügen (wird für diesen Befehl nicht mehr fragen)

## Erweiterte Funktionen

### Verlaufsnavigation

Amp CLI ermöglicht es Ihnen, durch Ihren Nachrichtenverlauf zu navigieren:

- Verwenden Sie die Pfeiltasten oder `Ctrl+P`/`Ctrl+N`, um durch benachbarte Nachrichten im Verlauf zu navigieren
- `PageUp` und `PageDown` Tasten springen direkt im Verlauf, unabhängig von der Cursorposition
- Ihr aktueller Entwurf ist am Ende des Verlaufs verfügbar
- Drücken Sie `Ctrl+C` oder `Esc`, um abzubrechen und zu Ihrem Entwurf zurückzukehren

### Dateierwähnungen

Sie können Dateien in der CLI schnell referenzieren, indem Sie die Dateierwähnungsfunktion verwenden:

- Geben Sie `@` gefolgt von einem Muster ein, um mit der Fuzzy-Suche nach Dateien zu beginnen
- Verwenden Sie Tab oder `Shift+Tab`, um durch die Suchergebnisse zu navigieren
- Drücken Sie `Enter`, um zu bestätigen und die Dateierwähnung einzufügen

### Debugging

Für Debugging-Zwecke können Sie verwenden:

```bash
amp --log-level debug --log-file amp.log
```



## Problembehandlung

### Node.js Version

Amp CLI erfordert Node.js v22 oder höher. Wenn Sie Fehler auftreten, überprüfen Sie Ihre Node.js-Version:

```bash
node --version
```

### Authentifizierungsprobleme

Wenn Sie Probleme mit der web-basierten Authentifizierung haben, versuchen Sie die im Abschnitt [Authentifizierung](#authentifizierung) beschriebene API-Schlüssel-Methode zu verwenden.

### Keine Guthaben

Wenn Sie eine Meldung "Out of free credits" sehen, besuchen Sie [ampcode.com/settings](https://ampcode.com/settings), um Ihr Konto zu aktualisieren.

## Anforderungen

- Node.js v22 oder höher
- Internetverbindung

## Zuletzt aktualisiert

2025-05-27
