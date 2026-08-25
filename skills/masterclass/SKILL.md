---
name: masterclass
description: Arma el funnel completo de una masterclass tipo webinar. Pregunta primero todo lo que falte (fecha, premisa, presupuesto, hero con opciones), clona el template de landing + página de gracias + .ics, crea tracking VIRGEN por edición (UTMs por canal para medir ROAS ads vs orgánico), deploya, y entrega calendario de ejecución + checklist. Uso "/masterclass" o "/masterclass <fecha>".
---

Sos el orquestador de masterclasses de [TU NEGOCIO]. Cada masterclass se monta con **tracking 100% virgen por edición** — NUNCA se mezclan datos de una edición con otra.

**Regla de oro #1:** no toques nada hasta terminar el Paso 1 (preguntar). El hero SIEMPRE se elige entre opciones con preview — el error clásico es deployar un headline flojo sin consultar.
**Regla de oro #2:** cada edición tiene su `masterId` único (`<negocio>-<ddmmm>`, ej. `mc-21jul`). El masterId define: pestaña de la planilla de registros, nombre del form, `utm_campaign` y carpeta de trabajo. Tracking viejo jamás se pisa ni se reutiliza.

## PASO 1 — Preguntar todo (en una tanda)

1. **Fecha + hora** de la clase (día de semana explícito).
2. **Premisa / promesa** (qué se demuestra o enseña en vivo). De acá sale el hero.
3. **Presupuesto de ads** (referencia: split 90% captación / 10% retargeting a registrados).
4. **Hero** — proponé 3-4 opciones con preview (eyebrow + H1 + sub). Ángulos que funcionan: demostración cruda ("mirame armarlo en vivo"), reto de tiempo ("en 60 minutos armo…" — doble especificidad, suele convertir mejor en frío), anti-guru. Si el usuario delega, elegí por especificidad + coherencia con los ads y fundamentá.
5. **Canal de comunidad** (grupo de WhatsApp/Telegram) — SIEMPRE grupo nuevo por edición.
6. **Video de la thank-you page** — reusar el anterior o esperar uno nuevo.

## PASO 2 — Montar la edición

- Cloná tu carpeta `template/` del funnel (landing + gracias + evento.ics) a la carpeta de la edición.
- Actualizá el bloque CONFIG de la landing: `masterId` nuevo, pixel, webhook de registros, nombre del form, redirect.
- `gracias.html`: fecha/hora ISO de la clase, link del grupo, video.
- `evento.ics`: UID nuevo, DTSTART/DTEND en UTC.
- Verificá TODAS las menciones de fecha: title, meta, eyebrow, gracias, .ics, botón de calendario.

## PASO 3 — Tracking virgen (el corazón del skill)

- Registros a una **planilla maestra** vía Apps Script Web App (se deploya UNA vez; cada `masterId` nuevo crea sola su pestaña con el primer registro).
- El form manda `master`, `nombre`, `email`, `whatsapp` + los 5 UTMs. Sin UTM = "directo".
- **Links por canal** (entregarlos SIEMPRE en tabla; `utm_campaign` = masterId):

| Canal | Query string |
|-------|-------------|
| Ads Meta | `?utm_source=meta&utm_medium=ads&utm_campaign=<masterId>&utm_content={{ad.name}}` |
| Historias | `?utm_source=ig_stories&utm_medium=organico&utm_campaign=<masterId>` |
| DMs | `?utm_source=dm&utm_medium=organico&utm_campaign=<masterId>` |
| Bio | `?utm_source=bio&utm_medium=organico&utm_campaign=<masterId>` |

El `{{ad.name}}` va literal en "Parámetros de URL" del anuncio → después medís ROAS por creativo.

## PASO 4 — Deploy + QA

- Deploy a tu hosting ([Netlify/Vercel]; si usás CLI, con el site explícito para no pisar otro proyecto).
- Verificar con `curl` en la URL canónica: hero nuevo, fecha nueva, form nuevo.
- QA de flujo: registro de prueba con `?utm_source=test` → verificar la fila en la pestaña del masterId → marcarla TEST.

## PASO 5 — Calendario de ejecución (entregar al final, siempre)

Hacia atrás desde el día D de la clase:
- **D-8 a D-6:** producir creativos (la mayor cantidad posible — 9 de cada 10 fallan), grupo nuevo, secuencia de mails/wpp, guion del bloque de cierre.
- **D-5 a D-3:** lanzar captación (90% del presupuesto, corre hasta 2hs antes). Menos días de campaña = más show-up.
- **Día 2 de campaña:** encender retargeting (10%, audiencia SOLO registrados; creativos = testimonios / razones para asistir).
- **D-1 y D:** mensajes diarios al grupo. Recordatorios mañana / 2hs antes / al aire.
- **D:** la clase. El bloque de cierre (pitch + bonuses + Q&A + urgencia) es EL punto crítico del revenue — no improvisarlo.
- **D+1 a D+3:** seguimiento a registrados no-show + deadline de la oferta.

Cerrá con checklist de pendientes con dueño.

## PASO 6 — Post-master

El ROAS se cierra con la skill /trazabilidad-master 7-14 días después: pestaña del masterId (registros por utm_source) × CRM (cierres).
