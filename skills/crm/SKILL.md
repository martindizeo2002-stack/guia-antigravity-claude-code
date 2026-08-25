---
name: crm
description: Crea el CRM de ventas de un mes nuevo, limpio y listo para cargar. Clona el último "CRM VENTAS" de forma nativa (conserva fórmulas, dropdowns y formato), vacía los datos cargados a mano y pre-carga las fechas del mes. Uso "/crm <mes>" — ej. "/crm agosto".
---

Tu tarea es crear el **CRM de ventas del mes** nuevo, limpio y listo para cargar.

**Contexto técnico importante:** Claude Code no puede escribir celdas de Google Sheets directamente. El truco es un **Google Apps Script deployado como Web App** que hace el trabajo pesado (clonar el sheet de forma nativa y vaciar los datos), y Claude solo lo dispara con `curl` y reporta. Ese script se arma una sola vez.

## Setup inicial (una sola vez)

Si todavía no tenés el Web App:

1. Abrí [script.google.com](https://script.google.com) y creá un proyecto nuevo.
2. Escribí (o pedile a Claude que te escriba) un script que: (a) busque el sheet "CRM VENTAS <Mes anterior>" más reciente en tu carpeta de CRMs, (b) lo clone con `makeCopy` (conserva fórmulas, dropdowns, formato), (c) vacíe los rangos que se cargan a mano (definí un mapa de rangos por pestaña), y (d) pre-cargue las fechas del mes en las pestañas diarias.
3. Deploy → Nueva implementación → Web App → ejecuta como vos, acceso "Cualquier usuario con el link".
4. Guardá la URL + un token secreto en un `config.json` del proyecto.

## Paso 1 — Leer la config

Leé `config.json`. Si `webAppUrl` está vacío, el Web App no está deployado: frená, mostrá los pasos del setup y terminá. No intentes clonar a mano.

## Paso 2 — Resolver el mes

Si no se pasó mes, usá el mes actual en [TU ZONA HORARIA]. Capitalizá en español (Julio, Agosto…).

## Paso 3 — Disparar el Web App

Por **GET** (no POST — el POST rebota en el redirect 302 de Apps Script):

```bash
curl -sL -G "<webAppUrl>" \
  --data-urlencode "token=<token>" \
  --data-urlencode "mes=<Mes>" \
  --data-urlencode "run=1"
```

La respuesta es JSON.

## Paso 4 — Reportar

- `ok:true` con `url` → decí que quedó creado, pegá el link clickeable, aclará de qué sheet clonó y qué limpió. Recordá que los targets de KPI quedaron con los del mes anterior — si cambian, editarlos a mano.
- `ok:true, alreadyExists:true` → ese CRM ya existía (no se duplicó), pasá el link.
- `ok:false` → mostrá el error tal cual.

No inventes que quedó listo si el JSON no lo confirma.

## Notas

- La fuente que clona es siempre el CRM **más reciente**, así hereda las mejoras de estructura del mes anterior.
- Pestañas de leaderboard/históricos no se limpian (recalculan solas).
