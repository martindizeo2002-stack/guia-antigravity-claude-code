---
name: competencia
description: Investiga un competidor a fondo — YouTube completo, ads activos en Meta Ad Library, landing y funnel hacking — y produce un dossier accionable, más un mapa comparativo del nicho. Uso "/competencia <nombre|canal|url>" para dossier, "/competencia nicho <keywords>" para descubrir quién pauta, "/competencia refresh <slug>" para actualizar y diffear.
---

# /competencia — Investigación de competencia

Herramientas del pipeline: **yt-dlp** (instalar con `pip install yt-dlp`) para YouTube, **Meta Ad Library** ([facebook.com/ads/library](https://www.facebook.com/ads/library)) para ads activos (pública, sin login; scrapeable con Playwright), y screenshots de landings con Playwright o el navegador.

## Modos

### `/competencia <nombre | @canal | url>` — dossier completo

1. **Resolver identidad** — canal de YT (`yt-dlp "ytsearch5:<nombre>"`), página de Facebook (búsqueda en Ad Library), landing (búsqueda web si falta).
2. **YouTube completo** — listado de videos con views a `raw/yt-videos.tsv`, detectar **outliers** (views vs la mediana del canal = qué temas explotan), transcripts del top 3-5, descripciones (ahí están los links del funnel).
3. **Ads** — Ad Library por página. Ordenar por **antigüedad del ad**: los longevos son los ganadores (nadie paga meses por un ad que no convierte).
4. **Landing + funnel** — entrar a cada URL (de ads + descripciones de YT + link-in-bio). Screenshot + HTML. Seguir el funnel hasta el final (agenda/VSL/checkout/precios).
5. **Dossier** — `competencia/<slug>/dossier.md` con: quién es, oferta y precios, funnel completo paso a paso, ángulos de sus ads ganadores (copy textual), qué le funciona en YT, huecos que deja. Actualizar `competencia/_mapa-nicho.md` (tabla comparativa viva).

### `/competencia nicho <keywords>` — sweep de descubrimiento

Buscar cada keyword en Ad Library, agrupar por anunciante, contar cantidad de ads y longevidad máxima. Output: ranking de quién pauta fuerte + a quiénes hacer dossier.

### `/competencia refresh <slug>` — actualización con diff

Re-correr ads + landing del ya dossierado. Reportar: ads nuevos (qué ángulo), ads muertos, cambios de landing/precio. Actualizar el dossier con fecha.

## Reglas duras

- **Instagram orgánico: NO scrapear con tus cuentas.** El scraping anónimo está muerto y usar una cuenta propia con scripts te la puede volar. Si necesitás data de IG, usá herramientas de terceros con export manual.
- Copy de competidores siempre **TEXTUAL entre comillas** — es banco de ángulos, no resumen.
- Señal objetiva obligatoria: longevidad de ad, views relativos al canal, cantidad de ads. **Sin dato no hay veredicto.**
- Todo queda local en `competencia/`.

## Estructura de salida

```
competencia/
  _mapa-nicho.md        # tabla comparativa viva
  _sweeps/              # barridos por keyword con fecha
  <slug>/
    dossier.md          # destilado accionable
    raw/                # yt-videos.tsv, transcripts, ads.json, landing-*.png
```
