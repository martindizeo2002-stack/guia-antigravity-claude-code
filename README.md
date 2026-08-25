# Guía · Antigravity + Claude Code desde cero

Guía completa para arrancar a usar **Google Antigravity** con **Claude Code** adentro, mismo setup que uso yo. Incluye los comandos (skills) que uso todos los días, en versión genérica para que los adaptes a tu negocio.

## Cómo leer esta guía

Orden recomendado, una parte por vez:

| # | Archivo | Qué cubre |
|---|---------|-----------|
| 1 | [01-instalacion.md](01-instalacion.md) | Instalar Antigravity + Claude Code y loguearte |
| 2 | [02-primeros-pasos.md](02-primeros-pasos.md) | Conceptos base · permisos · CLAUDE.md · memoria |
| 3 | [03-comandos-integrados.md](03-comandos-integrados.md) | Los comandos que ya vienen con Claude Code |
| 4 | [04-skills-y-agentes.md](04-skills-y-agentes.md) | Crear tus propios comandos (skills) y agentes |
| 5 | [05-conexiones-mcp.md](05-conexiones-mcp.md) | Conectar Drive, Calendar, Gmail y otras herramientas |

## Los comandos listos para copiar

En [skills/](skills/) están mis comandos en versión genérica (sin data de mi negocio). Cada uno es una carpeta con un `SKILL.md` adentro. Para usarlos copiás la carpeta a `.claude/skills/` dentro de tu proyecto y completás los placeholders `[ENTRE CORCHETES]` con la data de tu negocio.

| Comando | Para qué sirve |
|---------|----------------|
| [/carrusel](skills/carrusel/SKILL.md) | Armar un carrusel de Instagram de punta a punta |
| [/historias](skills/historias/SKILL.md) | Armar la secuencia de historias del día/semana |
| [/domingo](skills/domingo/SKILL.md) | Ritual semanal · recopila la semana y arma el plan |
| [/mensual](skills/mensual/SKILL.md) | Cierre de mes · qué contenido trae a los que pagan |
| [/crm](skills/crm/SKILL.md) | Crear el CRM del mes nuevo, limpio y listo |
| [/precall](skills/precall/SKILL.md) | Reporte pre-call antes de cada llamada con cliente |
| [/masterclass](skills/masterclass/SKILL.md) | Montar el funnel completo de un webinar |
| [/trazabilidad-master](skills/trazabilidad-master/SKILL.md) | Cerrar los números reales de un webinar ya hecho |
| [/competencia](skills/competencia/SKILL.md) | Dossier de un competidor · YouTube + ads + landing |

En [agents/](agents/) están los 4 agentes especializados (analista de ventas, coach de clientes, marketing y competencia). Van en `.claude/agents/`.

## Arranque rápido (10 minutos)

1. Instalá todo siguiendo [01-instalacion.md](01-instalacion.md).
2. Abrí la carpeta de tu proyecto en Antigravity y corré `claude` en la terminal integrada.
3. Corré `/init` para que Claude genere tu primer `CLAUDE.md`.
4. Editá ese `CLAUDE.md` con la data de tu negocio (quién sos, qué vendés, tu equipo, tus números, tu estilo).
5. Copiá una skill de [skills/](skills/) a `.claude/skills/` y probala escribiendo `/nombre`.

La regla más importante de todo el setup: **Claude vale lo que vale su contexto**. Cuanto mejor esté armado tu CLAUDE.md y tus skills, mejores resultados. El código es lo de menos — esto sirve igual para marketing, ventas y operaciones.
