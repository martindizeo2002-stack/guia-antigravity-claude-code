---
name: precall
description: Genera reportes pre-call para las próximas llamadas 1a1 con clientes. Lee Google Calendar, identifica las calls 1a1, busca la ficha del cliente en la carpeta de fichas y arma un reporte accionable con qué cubrir, preguntas clave, riesgos y compromisos a cerrar. Acepta opcionalmente un número de horas hacia adelante (default 24).
---

Tu tarea es generar reportes pre-call para las próximas llamadas 1a1 con clientes.

**Prerrequisitos:** conexión MCP de Google Calendar armada, y una carpeta `clientes/` con una ficha `.md` por cliente (quién es, estado, últimos avances, blockers).

## Paso 1 — Buscar las próximas calls 1a1

Usá la tool de Calendar (`list_events`) con:
- `timeMin`: ahora · `timeMax`: ahora + N horas (N = argumento del usuario; default 24) · tu zona horaria.

De los eventos, **filtrá solo las calls 1a1 con clientes**. Definí tu patrón de identificación, ej.:
- La description contiene "[TEXTO FIJO DE TU CALENDLY, ej. 'Sesión 1a1']"
- O el título tiene formato "Nombre Cliente and [VOS]"

Ignorá reuniones internas, clases grupales y todo lo que no matchee. Si no hay ninguna call 1a1 en el rango, decilo y terminá.

## Paso 2 — Identificar al cliente y su ficha

Extraé el nombre del título del evento. Buscá su ficha en `clientes/` con matching tolerante:
- Slug en minúsculas con guiones ("Juan Pérez" → `juan-perez`)
- Variaciones: con/sin tildes, solo nombre, solo apellido, `Glob` con `clientes/*apellido*.md`

Si encontrás la ficha, leela completa. Si NO, anotá "⚠️ Sin ficha cargada — cliente nuevo o no procesado" y devolvé solo los datos del calendar.

## Paso 3 — Generar el reporte por call

Formato exacto, una call por bloque, en orden cronológico:

```markdown
---

## 📞 [HORA] — [Nombre del cliente]

**Link de la reunión:** [extraer de la description]

### Quién es (3 líneas)
[resumen ejecutivo de la ficha]

### Estado actual
- **Fase:** [de la ficha]
- **Activo:** [sí/no/intermitente]
- **Última actividad:** [fecha; ⚠️ si hace más de 2 semanas]

### Los 3 puntos que SÍ o SÍ hay que cubrir hoy
1. [accionable concreto basado en sus blockers actuales]
2. …
3. …

### Preguntas clave para abrir la call
- [pregunta específica sobre su blocker principal, citando fechas/datos concretos]
- [seguimiento de algo puntual que dijo la última vez]

### Riesgos / cosas a evitar
- [qué NO prometerle · tema sensible si lo hay]

### Compromiso a cerrar al final
[1-2 entregables concretos para la próxima semana, con fecha]
```

## Reglas

- **Específico, no genérico.** No "preguntale por sus avances" — sí "preguntale si destrabó la verificación que estaba trabada el 28/3".
- **No inventes datos.** Si la ficha no tiene info de algo, omitilo o decí "no tengo data de X".
- Cerrá con: "Reporte generado para X calls. ¿Profundizo en alguna?"
