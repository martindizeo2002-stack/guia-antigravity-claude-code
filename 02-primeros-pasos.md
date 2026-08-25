# 02 · Primeros pasos

## La sesión básica

Parado en la carpeta de tu proyecto:

```bash
claude
```

Se abre el chat en la terminal. Le hablás en lenguaje natural, como a un empleado. Claude puede leer y escribir archivos, correr comandos, buscar en la web y usar las herramientas que le conectes.

Cosas que conviene saber desde el día 1:

- **Esc** frena a Claude en el momento, sin cerrar la sesión.
- **Esc dos veces** te deja editar tu mensaje anterior.
- **Shift+Tab** rota los modos de permisos (ver abajo).
- Escribir `@` te deja referenciar un archivo puntual (te autocompleta).
- Arrancar el mensaje con `!` ejecuta un comando de bash directo, sin pasar por Claude.
- `claude --continue` retoma la última conversación. `claude --resume` te deja elegir cuál retomar.

## Modos de permisos

Claude pide permiso antes de tocar archivos o correr comandos. Con **Shift+Tab** cambiás el modo:

| Modo | Qué hace |
|------|----------|
| **Default** | Pide confirmación para cada edición o comando |
| **Accept edits** | Acepta ediciones de archivos solo; comandos sigue preguntando |
| **Plan mode** | Claude NO toca nada; investiga y te presenta un plan para aprobar |
| **Bypass permissions** | No pregunta nada. Solo para carpetas donde no haya nada que romper |

Consejo: para tareas grandes o delicadas, arrancá en **Plan mode**. Claude investiga, te muestra el plan, lo aprobás y recién ahí ejecuta.

## CLAUDE.md — el cerebro del proyecto

Es un archivo en la raíz de tu carpeta que Claude **lee automáticamente en cada sesión**. Ahí vive todo el contexto de tu negocio. La diferencia entre un Claude genérico y uno que labura como parte de tu equipo es este archivo.

Para generarlo la primera vez:

```
/init
```

Después lo editás a mano. Estructura que funciona (adaptala):

```markdown
# CLAUDE.md — [Tu negocio]

## QUIÉN SOS
Rol que le das a Claude (ej: "sos mi director de ventas y segundo cerebro").

## EL NEGOCIO
Qué vendés, a quién, a qué precio, cómo es el producto/servicio.

## EQUIPO
Quién es quién y qué hace cada uno.

## MÉTRICAS
Facturación, funnel, tasas de cierre, targets del mes.

## FUENTES DE DATOS
Qué archivos hay en la carpeta y qué contiene cada uno.

## ESTILO DE TRABAJO
Cómo querés que te hable, en qué idioma, qué NO hacer.

## OBJETIVOS DEL TRIMESTRE
Para que cada respuesta empuje hacia donde vas.
```

Regla de oro: todo lo que le repetís a Claude más de una vez, va al CLAUDE.md.

## Memoria persistente

Aparte del CLAUDE.md, Claude Code tiene memoria propia que persiste entre conversaciones. Dos formas de alimentarla:

- Arrancar un mensaje con `#` guarda eso como memoria (te pregunta dónde).
- Pedírselo directo: "acordate que X" o "guardá en memoria que Y".

Con `/memory` ves y editás lo que tiene guardado. Usala para preferencias tuyas, decisiones tomadas y datos del negocio que no están en ningún archivo.

## El flujo de trabajo que rinde

1. **Contexto primero.** Antes de pedir, asegurate de que Claude tenga la data (CLAUDE.md + archivos en la carpeta).
2. **Una cosa por vez.** Pedidos concretos y acotados salen mejor que "hacé todo".
3. **Checkpoint antes del entregable.** Pedile que te muestre el borrador en el chat antes de generar el archivo/doc final.
4. **Iterá en la misma conversación.** Claude recuerda todo lo que pasó en la sesión; correcciones sobre lo ya hecho salen rápido.
5. **Lo que funcionó, se vuelve skill.** Si un flujo lo repetís cada semana, convertilo en comando (parte 04).

Siguiente: [03-comandos-integrados.md](03-comandos-integrados.md)
