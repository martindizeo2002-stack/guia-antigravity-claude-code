# 01 · Instalación

## Qué es cada cosa

- **Antigravity** es el IDE de Google (gratis, basado en VS Code). Trae los agentes de Gemini integrados y sirve como editor principal.
- **Claude Code** es el agente de Anthropic. Corre en la terminal y tiene extensión para el IDE. Es el que hace el trabajo pesado: lee tus archivos, ejecuta comandos, escribe entregables, se conecta a Drive/Calendar/etc.
- La combinación: Antigravity como editor + Claude Code adentro como cerebro ejecutor.

## Paso 1 — Instalar Antigravity

1. Entrá a [antigravity.google](https://antigravity.google) y descargá el instalador para tu sistema (Mac o Windows).
2. Instalalo como cualquier app. Al abrirlo te pide loguearte con tu cuenta de Google.
3. Listo. Es un VS Code con esteroides, si usaste VS Code te vas a sentir en casa.

## Paso 2 — Instalar Claude Code (CLI)

Abrí la terminal (la de Antigravity sirve: menú Terminal → New Terminal) y corré:

**Mac / Linux:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows (PowerShell):**
```powershell
irm https://claude.ai/install.ps1 | iex
```

Alternativa si tenés Node.js instalado:
```bash
npm install -g @anthropic-ai/claude-code
```

Verificá que quedó instalado:
```bash
claude --version
```

## Paso 3 — Loguearte

En la terminal, dentro de cualquier carpeta, corré:

```bash
claude
```

La primera vez te abre el navegador para loguearte. Dos opciones:

- **Cuenta de Claude (Pro o Max)** — la recomendada. Pagás la suscripción mensual y usás Claude Code sin límite por uso.
- **API key de Anthropic** — pagás por consumo. Solo si ya tenés cuenta de API.

Para laburar en serio con esto necesitás como mínimo el plan **Pro**. Si lo vas a usar todos los días, **Max** rinde más.

## Paso 4 — Conectar Claude Code con Antigravity

Como Antigravity está basado en VS Code, la extensión de Claude Code funciona adentro:

1. Abrí el panel de extensiones (`Cmd+Shift+X` en Mac, `Ctrl+Shift+X` en Windows).
2. Buscá **"Claude Code"** y fijate que sea la oficial de **Anthropic**.
3. Instalala.

Atajo alternativo: si abrís la terminal integrada de Antigravity y corrés `claude`, la integración con el IDE se suele instalar sola. Después, adentro de Claude Code, corré `/ide` para conectarlo al editor.

Con la extensión conectada, Claude ve qué archivo tenés abierto y qué texto seleccionaste, y te muestra los cambios como diffs en el editor.

## Paso 5 — Verificar que todo anda

```bash
claude doctor
```

Te tira un diagnóstico del setup. Si algo está en rojo, seguí lo que te sugiere.

## Estructura de carpetas recomendada

Un negocio = una carpeta = un workspace. Ejemplo:

```
~/Desktop/mi-negocio/
  CLAUDE.md            ← el cerebro (lo armás en la parte 02)
  .claude/
    skills/            ← tus comandos custom (parte 04)
    agents/            ← tus agentes (parte 04)
  datos/               ← CSVs, exports, transcripciones, lo que uses
```

Siempre abrí Antigravity **en la carpeta del negocio** (File → Open Folder) y corré `claude` parado ahí. Claude Code carga automáticamente el CLAUDE.md de la carpeta donde lo ejecutás.

Siguiente: [02-primeros-pasos.md](02-primeros-pasos.md)
