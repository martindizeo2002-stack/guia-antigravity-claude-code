# 04 · Skills y agentes — tus comandos propios

Acá está la magia del setup. Una **skill** es un comando custom: un archivo de instrucciones que Claude sigue al pie de la letra cuando escribís `/nombre`. Un **agente** es un Claude especializado con su propio rol y herramientas, al que delegás trabajo pesado.

## Skills

### Dónde viven

```
tu-proyecto/
  .claude/
    skills/
      carrusel/
        SKILL.md      ← las instrucciones
      domingo/
        SKILL.md
```

- `.claude/skills/` dentro del proyecto → disponibles en ese proyecto.
- `~/.claude/skills/` en tu home → disponibles en todos tus proyectos.

### Formato

Cada `SKILL.md` arranca con un frontmatter y sigue con las instrucciones:

```markdown
---
name: nombre-del-comando
description: Qué hace y cuándo usarlo. Claude lee esto para decidir
  cuándo activar la skill. Incluí acá el uso, ej. "/comando <argumento>".
---

Acá van las instrucciones que Claude sigue cuando lo invocás.
Escribilas como le escribirías a un empleado nuevo: rol, pasos,
reglas, formato de entrega.
```

Se invoca escribiendo `/nombre-del-comando` en el chat (con argumentos opcionales: `/carrusel hook sobre X`). Claude también puede activarla solo si detecta que tu pedido matchea la descripción.

### La anatomía que funciona (aprendida a los golpes)

Todas mis skills siguen el mismo esqueleto de 4 pasos. Copialo:

```markdown
## PASO 1 — Preguntar todo (antes de producir nada)
Listá qué información necesita la skill y ordenale a Claude que
pregunte TODO lo que falte antes de arrancar, en una sola tanda.
El error clásico es que asuma cosas y produzca algo que no era.

## PASO 2 — Producir
Los pasos concretos, con las reglas del negocio (qué decir,
qué NO decir, formatos, fuentes de datos que debe leer).

## PASO 3 — Checkpoint (esperar OK)
"Mostrá el borrador completo en el chat y esperá mi OK antes
de generar el entregable final. Si pido ajustes, iterá."

## PASO 4 — Entregar
Dónde y cómo queda el entregable (archivo, Google Doc, sheet),
y que pase el link al final.
```

Reglas de oro para escribir skills:

1. **Reglas explícitas > confianza.** Todo lo que Claude hizo mal una vez, lo escribís como regla en la skill ("PROHIBIDO X", "SIEMPRE Y"). La skill mejora con cada uso.
2. **"No inventes"** — escribilo literal. "Si un dato no está, marcalo FALTA y seguí."
3. **Fuentes de verdad nombradas.** Si la skill necesita datos, decile exactamente qué archivo leer ("los casos salen de `datos/casos.md`, no de tu memoria").
4. **Defaults.** Para cada pregunta del Paso 1, definí qué pasa si el usuario no contesta ("default 7 slides").

### Ejemplo mínimo completo

```markdown
---
name: resumen-semanal
description: Resume la semana comercial. Lee el CSV de ventas y
  arma un resumen con números vs target. Uso "/resumen-semanal".
---

Sos el analista comercial de [MI NEGOCIO].

1. Leé `datos/ventas.csv` y filtrá los últimos 7 días.
2. Calculá: ventas totales, ticket promedio, gap vs target
   semanal de [TARGET]. Si falta un dato, marcá "FALTA".
3. Entregá en el chat: 3 bullets de qué pasó + 1 recomendación
   concreta para la semana que viene. Directo, sin vueltas.
```

## Agentes

Un agente es un Claude aparte, con rol propio, que labura en paralelo sin ensuciar tu conversación. Ideal para análisis pesados (leer 50 transcripciones, revisar todos los DMs).

### Dónde viven y formato

Archivos `.md` en `.claude/agents/` (proyecto) o `~/.claude/agents/` (global):

```markdown
---
name: analista-ventas
description: Analista de ventas. Usalo cuando haya que analizar
  calls de venta — objeciones, patrones de cierre, performance
  del closer. Tiene acceso a las transcripciones.
tools: Read, Grep, Glob, Bash
---

Sos el analista de ventas de [MI NEGOCIO]. Tu fuente de verdad
son las transcripciones en `transcripciones/`.
[... rol completo, metodología, formato de respuesta ...]
```

- `description` es clave: Claude la lee para decidir cuándo delegarle trabajo a este agente.
- `tools` limita qué puede hacer (un agente de análisis no necesita escribir archivos).
- Se invocan mencionándolos: "analista-ventas: qué objeciones se repitieron este mes", o Claude los llama solo cuando corresponde.
- `/agents` te deja crearlos y editarlos guiado.

### Skills vs agentes, cuándo cada uno

- **Skill** = un flujo repetible con pasos definidos (armar el carrusel, cerrar el mes). Vos lo disparás.
- **Agente** = un especialista al que se le delega análisis abierto sobre un corpus de datos (calls, DMs, fichas de clientes).
- Se combinan: una skill puede decirle a Claude que delegue el paso pesado a un agente.

En [skills/](skills/) y [agents/](agents/) de este repo tenés mis 9 skills y 4 agentes en versión genérica para copiar y adaptar.

Siguiente: [05-conexiones-mcp.md](05-conexiones-mcp.md)
