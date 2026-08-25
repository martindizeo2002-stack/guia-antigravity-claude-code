# 03 · Comandos integrados de Claude Code

Los comandos empiezan con `/` y se escriben directo en el chat. Estos vienen de fábrica (los tuyos custom se suman en la parte 04).

## Los que vas a usar todos los días

| Comando | Qué hace |
|---------|----------|
| `/init` | Genera el CLAUDE.md inicial del proyecto |
| `/clear` | Borra la conversación y arranca de cero (¡usalo seguido! contexto limpio = mejores respuestas) |
| `/compact` | Comprime la conversación larga en un resumen para seguir sin perder el hilo |
| `/resume` | Retoma una conversación anterior |
| `/memory` | Ver y editar la memoria persistente |
| `/model` | Cambiar de modelo (más potente vs más rápido/barato) |
| `/help` | Lista de todos los comandos disponibles |

## Configuración y estado

| Comando | Qué hace |
|---------|----------|
| `/config` | Panel de configuración (tema, notificaciones, modelo por defecto) |
| `/permissions` | Ver y editar qué puede hacer Claude sin preguntar |
| `/status` | Estado de la sesión (cuenta, modelo, directorio) |
| `/cost` | Cuánto llevás gastado en la sesión (si usás API) |
| `/doctor` | Diagnóstico del setup |
| `/login` / `/logout` | Cambiar de cuenta |
| `/ide` | Conectar con el editor (Antigravity) |

## Herramientas y extensiones

| Comando | Qué hace |
|---------|----------|
| `/mcp` | Ver y gestionar las conexiones MCP (Drive, Calendar, etc. — parte 05) |
| `/agents` | Ver y crear agentes especializados |
| `/vim` | Modo vim para editar mensajes (si sos de vim) |

## Trucos de uso

- **`/clear` es tu mejor amigo.** Cada tarea nueva, conversación nueva. Arrastrar una conversación de 3 horas para un pedido nuevo empeora los resultados y gasta más.
- **`/compact` cuando la tarea es larga** y no querés perder el contexto de lo que se decidió.
- **`/model`** te deja bajar a un modelo más rápido para tareas simples (renombrar, buscar, formatear) y volver al potente para las importantes.
- Claude Code también corre **sin chat**, para automatizar: `claude -p "resumime las ventas del CSV"` responde y sale. Sirve para scripts y crons.

Siguiente: [04-skills-y-agentes.md](04-skills-y-agentes.md)
