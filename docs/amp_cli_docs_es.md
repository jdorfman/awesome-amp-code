# Documentación No Oficial de Amp CLI

---

[Amp](https://ampcode.com) es un agente de codificación (coding agent) con IA, en vista previa de investigación de Sourcegraph. Esta es la CLI para Amp; también puedes usar [Amp en VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp).

## Tabla de Contenidos

- [Documentación No Oficial de Amp CLI](#documentación-no-oficial-de-amp-cli)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [Instalación](#instalación)
  - [Primeros Pasos](#primeros-pasos)
  - [Modos de Uso](#modos-de-uso)
    - [Modo Interactivo](#modo-interactivo)
    - [Modo No Interactivo](#modo-no-interactivo)
  - [Autenticación](#autenticación)
    - [Inicio de Sesión Basado en Web](#inicio-de-sesión-basado-en-web)
    - [Autenticación con API Key](#autenticación-con-api-key)
  - [Opciones de Línea de Comandos](#opciones-de-línea-de-comandos)
  - [Comandos](#comandos)
  - [Variables de Entorno](#variables-de-entorno)
  - [Ejemplos](#ejemplos)
  - [Configuración](#configuración)
    - [Referencia de Configuraciones](#referencia-de-configuraciones)
  - [Uso de Herramientas](#uso-de-herramientas)
  - [Características Avanzadas](#características-avanzadas)
    - [Navegación del Historial](#navegación-del-historial)
    - [Menciones de Archivos](#menciones-de-archivos)
    - [Depuración](#depuración)
  - [Solución de Problemas](#solución-de-problemas)
    - [Versión de Node.js](#versión-de-nodejs)
    - [Problemas de Autenticación](#problemas-de-autenticación)
    - [Sin Créditos](#sin-créditos)
  - [Requisitos](#requisitos)
  - [Última actualización](#última-actualización)

## Instalación

Instala Amp CLI globalmente usando tu gestor de paquetes preferido:

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

## Primeros Pasos

Después de la instalación, puedes comenzar a usar Amp CLI inmediatamente:

```bash
amp
```

En la primera ejecución, Amp te guiará a través del proceso de autenticación.

## Modos de Uso

### Modo Interactivo

El modo interactivo proporciona una interfaz conversacional donde puedes tener un diálogo con Amp:

```bash
amp
```

En modo interactivo:

- Escribe tus preguntas o comandos en el prompt (`>`)
- Usa `\` seguido de `Enter` para insertar saltos de línea, o usa `Shift+Enter` en terminales compatibles
- Presiona `Ctrl+C` para interrumpir el agente o salir
- Escribe `help` para ver en qué puede ayudarte Amp
- Usa las teclas de flecha o Ctrl+P/Ctrl+N para navegar por el historial de mensajes
- Usa PageUp y PageDown para saltar directamente en el historial
- Escribe @ seguido de un patrón para buscar difusamente y mencionar archivos (usa Tab/Shift+Tab para navegar por los resultados)

### Modo No Interactivo

Puedes usar Amp en modo no interactivo canalizando contenido hacia él:

```bash
echo "commit all my unstaged changes" | amp
```

O usando redirección de entrada/salida:

```bash
amp < prompt.txt > output.txt
```

## Autenticación

Amp CLI admite dos métodos de autenticación:

### Inicio de Sesión Basado en Web

Por defecto, Amp usa un flujo de inicio de sesión basado en web:

1. Ejecuta `amp` por primera vez
2. Se abrirá una ventana del navegador para autenticarte con ampcode.com
3. Después de la autenticación exitosa, puedes continuar usando Amp CLI

### Autenticación con API Key

También puedes autenticarte usando API keys:

1. Ve a [ampcode.com/settings](https://ampcode.com/settings)
2. Copia tu API key
3. Configúrala como una variable de entorno:

```bash
export AMP_API_KEY=[REDACTED:api-key]
```

## Opciones de Línea de Comandos

Amp CLI admite las siguientes opciones:

| Opción                    | Descripción                                                          |
| ------------------------- | -------------------------------------------------------------------- |
| `-h, --help`              | Mostrar información de ayuda                                        |
| `-V, --version`           | Mostrar el número de versión                                        |
| `--thread-id [THREAD_ID]` | ID del hilo (thread) para continuar ejecutando                      |
| `--notifications`         | Habilitar notificaciones de sonido (habilitado por defecto cuando es interactivo) |
| `--no-notifications`      | Deshabilitar notificaciones de sonido                               |
| `--color`                 | Habilitar salida con color (habilitado por defecto si stdout y stderr se envían a un TTY) |
| `--no-color`              | Deshabilitar salida con color                                       |
| `--settings-file <value>` | Ruta de archivo de configuraciones personalizada (anula la ubicación por defecto) |
| `--log-level <value>`     | Establecer nivel de registro (error, warn, info, debug, audit)      |
| `--log-file <value>`      | Establecer ubicación del archivo de registro                        |

## Comandos

Amp CLI incluye varios subcomandos para funcionalidad mejorada:

| Comando             | Descripción                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `logout`            | Cerrar sesión eliminando la API key almacenada                      |
| `login`             | Iniciar sesión en Amp                                               |
| `threads`           | Comandos de gestión de hilos (threads)                              |
| `threads new`       | Crear un nuevo hilo e imprimir su ID                                |
| `threads continue`  | Continuar un hilo existente (usa el último hilo usado si no se proporciona ID) |
| `threads fork`      | Crear un nuevo hilo bifurcando uno existente e imprimir su ID       |
| `threads list`      | Listar todos tus hilos con sus títulos y estado de compartición     |
| `tools`             | Comandos de gestión de herramientas                                  |
| `tools show`        | Mostrar herramientas disponibles                                     |

## Variables de Entorno

| Variable            | Descripción                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `AMP_API_KEY`       | API key para Amp (ver https://ampcode.com/settings)                 |
| `AMP_URL`           | URL para el servicio Amp (por defecto es https://ampcode.com/)      |
| `AMP_LOG_LEVEL`     | Establecer nivel de registro (también se puede usar --log-level)    |
| `AMP_LOG_FILE`      | Establecer ubicación del archivo de registro (también se puede usar --log-file) |
| `AMP_SETTINGS_FILE` | Establecer ruta del archivo de configuraciones (también se puede usar --settings-file, por defecto: ~/.config/amp/settings.json) |

## Ejemplos

Iniciar una sesión interactiva:

```bash
amp
```

Ejecutar un comando en una sesión no interactiva:

```bash
echo "commit all my unstaged changes" | amp
```

Ejecutar desde un archivo de prompt en una sesión no interactiva y almacenar salida en un archivo:

```bash
amp < prompt.txt > output.txt
```

## Configuración

Amp puede configurarse usando un archivo de configuraciones JSON ubicado en `~/.config/amp/settings.json`. Todas las configuraciones usan el prefijo "amp.".

Configuración de ejemplo:

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

### Referencia de Configuraciones

- **`amp.notifications.enabled`**: Habilitar notificaciones de sonido del sistema cuando el agente completa tareas
- **`amp.mcpServers`**: Servidores Model Context Protocol a los que conectarse para herramientas adicionales
- **`amp.mcp.disable`**: Array de nombres de servidores MCP a deshabilitar
- **`amp.tools.disable`**: Array de nombres de herramientas a deshabilitar
- **`amp.commands.allowlist`**: Array de comandos de shell que pueden ejecutarse sin confirmación

## Uso de Herramientas

Amp puede usar varias herramientas para ayudar con tus tareas. Cuando Amp quiere usar una herramienta (como ejecutar un comando de terminal), pedirá tu confirmación:

```
Amp wants to run: git status

Allow this command? [y/n/!]
```

Opciones:

- `y`: Permitir este comando una vez
- `n`: Rechazar este comando
- `!`: Permitir y agregar a lista de permitidos (no preguntará de nuevo para este comando)

## Características Avanzadas

### Navegación del Historial

Amp CLI te permite navegar por tu historial de mensajes:

- Usa las teclas de flecha o `Ctrl+P`/`Ctrl+N` para navegar por mensajes adyacentes en el historial
- Las teclas `PageUp` y `PageDown` saltan directamente en el historial independientemente de la posición del cursor
- Tu borrador actual está disponible al final del historial
- Presiona `Ctrl+C` o `Esc` para cancelar y regresar a tu borrador

### Menciones de Archivos

Puedes referenciar archivos rápidamente en la CLI usando la característica de mención de archivos:

- Escribe `@` seguido de un patrón para comenzar a buscar archivos difusamente
- Usa Tab o `Shift+Tab` para navegar por los resultados de búsqueda
- Presiona `Enter` para confirmar e insertar la mención del archivo

### Depuración

Para propósitos de depuración, puedes usar:

```bash
amp --log-level debug --log-file amp.log
```



## Solución de Problemas

### Versión de Node.js

Amp CLI requiere Node.js v22 o superior. Si encuentras errores, verifica tu versión de Node.js:

```bash
node --version
```

### Problemas de Autenticación

Si tienes problemas con la autenticación basada en web, intenta usar el método de API key descrito en la sección [Autenticación](#autenticación).

### Sin Créditos

Si ves un mensaje de "Out of free credits", visita [ampcode.com/settings](https://ampcode.com/settings) para actualizar tu cuenta.

## Requisitos

- Node.js v22 o superior
- Conexión a internet

## Última actualización

2025-05-27
