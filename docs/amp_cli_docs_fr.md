# Documentation Non Officielle d'Amp CLI

---

[Amp](https://ampcode.com) est un agent de codage IA, en aperçu de recherche de Sourcegraph. Ceci est la CLI pour Amp ; vous pouvez également utiliser [Amp dans VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp).

## Table des Matières

- [Documentation Non Officielle d'Amp CLI](#documentation-non-officielle-damp-cli)
  - [Table des Matières](#table-des-matières)
  - [Installation](#installation)
  - [Premiers Pas](#premiers-pas)
  - [Modes d'Utilisation](#modes-dutilisation)
    - [Mode Interactif](#mode-interactif)
    - [Mode Non Interactif](#mode-non-interactif)
  - [Authentification](#authentification)
    - [Connexion Basée sur le Web](#connexion-basée-sur-le-web)
    - [Authentification par Clé API](#authentification-par-clé-api)
  - [Options de Ligne de Commande](#options-de-ligne-de-commande)
  - [Commandes](#commandes)
  - [Variables d'Environnement](#variables-denvironnement)
  - [Exemples](#exemples)
  - [Configuration](#configuration)
    - [Référence des Paramètres](#référence-des-paramètres)
  - [Utilisation des Outils](#utilisation-des-outils)
  - [Fonctionnalités Avancées](#fonctionnalités-avancées)
    - [Navigation dans l'Historique](#navigation-dans-lhistorique)
    - [Mentions de Fichiers](#mentions-de-fichiers)
    - [Débogage](#débogage)
  - [Dépannage](#dépannage)
    - [Version de Node.js](#version-de-nodejs)
    - [Problèmes d'Authentification](#problèmes-dauthentification)
    - [Plus de Crédits](#plus-de-crédits)
  - [Exigences](#exigences)
  - [Dernière mise à jour](#dernière-mise-à-jour)

## Installation

Installez Amp CLI globalement en utilisant votre gestionnaire de paquets préféré :

```bash
npm install -g @sourcegraph/amp
```

Ou avec Yarn :

```bash
yarn global add @sourcegraph/amp
```

Ou avec pnpm :

```bash
pnpm add -g @sourcegraph/amp
```

## Premiers Pas

Après l'installation, vous pouvez commencer à utiliser Amp CLI immédiatement :

```bash
amp
```

Au premier lancement, Amp vous guidera à travers le processus d'authentification.

## Modes d'Utilisation

### Mode Interactif

Le mode interactif fournit une interface conversationnelle où vous pouvez avoir un dialogue avec Amp :

```bash
amp
```

En mode interactif :

- Tapez vos questions ou commandes à l'invite (`>`)
- Utilisez `\` suivi d'`Entrée` pour insérer des sauts de ligne, ou utilisez `Shift+Entrée` dans les terminaux supportés
- Appuyez sur `Ctrl+C` pour interrompre l'agent ou quitter
- Tapez `help` pour voir comment Amp peut vous aider
- Utilisez les touches fléchées ou Ctrl+P/Ctrl+N pour naviguer dans l'historique des messages
- Utilisez PageUp et PageDown pour aller directement dans l'historique
- Tapez @ suivi d'un motif pour rechercher et mentionner des fichiers de manière floue (utilisez Tab/Shift+Tab pour naviguer dans les résultats)

### Mode Non Interactif

Vous pouvez utiliser Amp en mode non interactif en redirigeant le contenu vers lui :

```bash
echo "commit all my unstaged changes" | amp
```

Ou en utilisant la redirection d'entrée/sortie :

```bash
amp < prompt.txt > output.txt
```

## Authentification

Amp CLI supporte deux méthodes d'authentification :

### Connexion Basée sur le Web

Par défaut, Amp utilise un flux de connexion basé sur le web :

1. Lancez `amp` pour la première fois
2. Une fenêtre de navigateur s'ouvrira pour vous authentifier avec ampcode.com
3. Après une authentification réussie, vous pouvez continuer à utiliser Amp CLI

### Authentification par Clé API

Vous pouvez également vous authentifier en utilisant des clés API :

1. Allez sur [ampcode.com/settings](https://ampcode.com/settings)
2. Copiez votre clé API
3. Définissez-la comme variable d'environnement :

```bash
export AMP_API_KEY=[REDACTED:api-key]
```

## Options de Ligne de Commande

Amp CLI supporte les options suivantes :

| Option                       | Description                                                          |
| ---------------------------- | -------------------------------------------------------------------- |
| `-V, --version`              | Afficher le numéro de version                                       |
| `--visibility <visibility>`  | Définir la visibilité du thread (private, public, team)             |
| `--notifications`            | Activer les notifications sonores (activé par défaut quand pas en mode execute) |
| `--no-notifications`         | Désactiver les notifications sonores                                |
| `--settings-file <value>`    | Chemin de fichier de paramètres personnalisé (remplace l'emplacement par défaut) |
| `--log-level <value>`        | Définir le niveau de log (error, warn, info, debug, audit)          |
| `--log-file <value>`         | Définir l'emplacement du fichier de log                             |
| `--dangerously-allow-all`    | Désactiver toutes les invites de confirmation de commande (l'agent exécutera toutes les commandes sans demander) |
| `-x, --execute [message]`    | Utiliser le mode execute, optionnellement avec message utilisateur. En mode execute, l'agent exécutera le prompt fourni (soit comme argument, soit via stdin). Seul le dernier message assistant est affiché. Activé automatiquement lors de la redirection stdout. |

## Commandes

Amp CLI inclut plusieurs sous-commandes pour des fonctionnalités améliorées :

| Commande                    | Description                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| `logout`                   | Se déconnecter en supprimant la clé API stockée                     |
| `login`                    | Se connecter à Amp                                                   |
| `threads`                  | Commandes de gestion des threads                                     |
| `threads new`              | Créer un nouveau thread et afficher son ID                          |
| `threads continue`         | Continuer un thread existant (utilise le dernier thread utilisé si aucun ID n'est fourni) |
| `threads fork`             | Créer un nouveau thread en bifurquant un existant et afficher son ID |
| `threads list`             | Lister tous vos threads avec leurs titres et statut de partage      |
| `threads share`            | Modifier la visibilité du thread ou partager avec le support        |
| `threads compact`          | Compacter un thread en créant un résumé pour réduire l'utilisation de tokens |
| `tools`                    | Commandes de gestion des outils                                     |
| `tools show`               | Afficher les outils disponibles                                     |
| `doctor`                   | Générer un bundle de support pour le dépannage                      |
| `update`                   | Mettre à jour Amp CLI vers la dernière version                      |

## Variables d'Environnement

| Variable            | Description                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `AMP_API_KEY`       | Clé API pour Amp (voir https://ampcode.com/settings)                |
| `AMP_URL`           | URL pour le service Amp (par défaut https://ampcode.com/)           |
| `AMP_LOG_LEVEL`     | Définir le niveau de log (peut aussi utiliser --log-level)          |
| `AMP_LOG_FILE`      | Définir l'emplacement du fichier de log (peut aussi utiliser --log-file) |
| `AMP_SETTINGS_FILE` | Définir le chemin du fichier de paramètres (peut aussi utiliser --settings-file, par défaut : ~/.config/amp/settings.json) |

## Exemples

Démarrer une session interactive :

```bash
amp
```

Démarrer une session interactive avec un message utilisateur :

```bash
echo "commit all my unstaged changes" | amp
```

Utiliser le mode execute (`--execute` ou `-x`) pour envoyer une commande à un agent, l'exécuter, afficher seulement le dernier message de l'agent, puis quitter :

```bash
amp -x "what file in this folder is in markdown format?"
```

Utiliser le mode execute et permettre à l'agent d'utiliser des outils qui nécessiteraient une approbation :

```bash
amp --dangerously-allow-all -x "Rename all .markdown files to .md. Only print list of renamed files."
```

Rediriger une commande vers l'agent et utiliser le mode execute :

```bash
echo "commit all my unstaged changes" | amp -x --dangerously-allow-all
```

Exécuter un prompt à partir d'un fichier et stocker le dernier message assistant dans un fichier (rediriger stdout équivaut à fournir `-x`/`--execute`) :

```bash
amp < prompt.txt > output.txt
```

## Configuration

Amp peut être configuré en utilisant un fichier de paramètres JSON situé à `~/.config/amp/settings.json`. Tous les paramètres utilisent le préfixe "amp.".

Configuration d'exemple :

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

### Référence des Paramètres

- **`amp.notifications.enabled`** : Activer les notifications sonores système quand l'agent termine des tâches
- **`amp.mcpServers`** : Serveurs Model Context Protocol auxquels se connecter pour des outils supplémentaires
- **`amp.tools.disable`** : Tableau des noms d'outils à désactiver. Utilisez 'builtin:nomoutil' pour désactiver uniquement l'outil intégré avec ce nom (permettant à un serveur MCP de fournir un outil avec ce nom).
- **`amp.commands.allowlist`** : Tableau des commandes shell qui peuvent être exécutées sans confirmation
- **`amp.commands.strict`** : Activer la validation stricte des commandes. Quand désactivé, certaines commandes comme Bazel obtiennent une validation de chemin assouplie.
- **`amp.dangerouslyAllowAll`** : Désactiver toutes les invites de confirmation de commande (l'agent exécutera toutes les commandes sans demander)
- **`amp.git.commit.coauthor.enabled`** : Activer l'ajout d'Amp comme co-auteur dans les commits git
- **`amp.git.commit.ampThread.enabled`** : Activer l'ajout du trailer Amp-Thread dans les commits git
- **`amp.updates.autoUpdate.enabled`** : Activer les mises à jour automatiques d'Amp CLI

## Utilisation des Outils

Amp peut utiliser divers outils pour vous aider dans vos tâches. Quand Amp veut utiliser un outil (comme exécuter une commande terminal), il demandera votre confirmation :

```text
Amp wants to run: git status

Allow this command? [y/n/!]
```

Options :

- `y` : Autoriser cette commande une fois
- `n` : Rejeter cette commande
- `!` : Autoriser et ajouter à la liste autorisée (ne demandera plus pour cette commande)

## Fonctionnalités Avancées

### Navigation dans l'Historique

Amp CLI vous permet de naviguer dans votre historique de messages :

- Utilisez les touches fléchées ou `Ctrl+P`/`Ctrl+N` pour naviguer dans les messages adjacents de l'historique
- Les touches `PageUp` et `PageDown` sautent directement dans l'historique indépendamment de la position du curseur
- Votre brouillon actuel est disponible à la fin de l'historique
- Appuyez sur `Ctrl+C` ou `Échap` pour annuler et retourner à votre brouillon

### Mentions de Fichiers

Vous pouvez rapidement référencer des fichiers dans la CLI en utilisant la fonctionnalité de mention de fichiers :

- Tapez `@` suivi d'un motif pour commencer une recherche floue de fichiers
- Utilisez Tab ou `Shift+Tab` pour naviguer dans les résultats de recherche
- Appuyez sur `Entrée` pour confirmer et insérer la mention de fichier

### Débogage

À des fins de débogage, vous pouvez utiliser :

```bash
amp --log-level debug --log-file amp.log
```

## Dépannage

### Version de Node.js

Amp CLI nécessite Node.js v22 ou supérieur. Si vous rencontrez des erreurs, vérifiez votre version de Node.js :

```bash
node --version
```

### Problèmes d'Authentification

Si vous avez des problèmes avec l'authentification basée sur le web, essayez la méthode de clé API décrite dans la section [Authentification](#authentification).

### Plus de Crédits

Si vous voyez un message "Out of free credits", visitez [ampcode.com/settings](https://ampcode.com/settings) pour mettre à niveau votre compte.

## Exigences

- Node.js v22 ou supérieur
- Connexion Internet

## Dernière mise à jour

2025-07-25
