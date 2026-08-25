# 05 · Conexiones (MCP) — Drive, Calendar, Gmail y más

MCP es el protocolo con el que Claude Code se conecta a herramientas externas. Con las conexiones armadas, Claude puede leer tus sheets, revisar tu calendario, buscar mails, leer transcripciones de llamadas y más. Acá es donde el setup pasa de "chat que escribe" a "empleado con acceso a los sistemas".

## Las que uso y para qué

| Conexión | Qué habilita |
|----------|--------------|
| **Google Drive** | Leer y crear Docs/Sheets. CRM, trackers, planes semanales, guiones |
| **Google Calendar** | Leer próximas calls (base del comando /precall), crear eventos |
| **Gmail** | Buscar mails, armar borradores |
| **Fathom** (o tu grabador de calls) | Buscar reuniones y traer transcripciones. Oro para analizar ventas |
| **Notion** | Si tu equipo documenta ahí |

## Cómo conectar

### Vía claude.ai (lo más simple para Google)

1. Entrá a [claude.ai/settings/connectors](https://claude.ai/settings/connectors) con la misma cuenta que usás en Claude Code.
2. Conectá Google Drive, Calendar, Gmail (te pide autorizar con tu cuenta de Google).
3. Los conectores quedan disponibles también en Claude Code automáticamente.

### Vía terminal (para servidores MCP de terceros)

```bash
# ejemplo genérico
claude mcp add <nombre> -- <comando-del-servidor>

# listar lo conectado
claude mcp list
```

Dentro del chat, `/mcp` muestra el estado de todas las conexiones y te deja autenticar las que lo pidan.

## Qué cambia en el día a día

Con las conexiones armadas, pedidos así funcionan directo:

- "Leé el CRM de agosto y decime cómo venimos vs target"
- "Buscá la transcripción de la call con [cliente] y resumime las objeciones"
- "Qué calls tengo mañana y armame el pre-call de cada una"
- "Creá un Doc con este guion en la carpeta de [mes]"

Y las skills los automatizan: mi `/domingo` lee CRM + calls + tracker y arma el plan semanal solo, porque las conexiones ya están hechas.

## Consejos

- **Autorizá con la cuenta correcta.** Si tu Drive del negocio es otra cuenta de Google, conectá esa.
- **Los IDs de tus archivos clave, al CLAUDE.md.** Si Claude usa siempre el mismo sheet (CRM, tracker), guardá el link o ID en el CLAUDE.md así no lo busca cada vez.
- **Sheets gigantes se truncan.** Si un sheet es enorme, mejor exportarlo (CSV/XLSX) y que Claude lo procese local con Python.
- **Todo lo que no tenga conexión, exportalo a la carpeta.** Claude lee cualquier archivo local: CSVs del CRM, exports de Meta Ads, dumps de chats. La carpeta del proyecto es tu data lake de pobre y funciona perfecto.

---

Con esto ya tenés el setup completo. El orden para arrancar en serio:

1. CLAUDE.md gordo y honesto (parte 02).
2. Conexiones de Google (esta parte).
3. Una skill simple que uses cada semana (parte 04 + carpeta [skills/](skills/)).
4. Iterar: cada error de Claude se convierte en una regla nueva en el CLAUDE.md o en la skill.
