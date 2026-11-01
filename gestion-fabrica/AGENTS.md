# Trabajar en los proyectos de Gestión fábrica

Reglas para cualquier agente (Claude, Copilot u otro) que trabaje en esta carpeta. La persona mira los proyectos en Edge con `kanvas.html`; lo que cambies aparece allí en pocos segundos.

En este PC el agente no puede ejecutar comandos en la terminal, así que no uses `kanvas.py`: editas el `kanvas.json` del proyecto directamente. Por eso estas reglas son la única barrera. Síguelas al pie de la letra.

VS Code está abierto en la carpeta `Gestión fábrica`. La persona te dice el proyecto y la tarea, por ejemplo: «En Mejora línea 3, trabaja en CO-02».

## Dónde está cada cosa

- Cada subcarpeta con un `kanvas.json` es un proyecto. `title` es su nombre.
- Los correos `.msg` de un proyecto están en su carpeta `correos\`. Puedes leerlos, no los borres ni los cambies.

## Una tarea

```json
{
  "id": "CO-02",
  "title": "Comparar ofertas de bombas",
  "state": "todo",
  "group": "CO",
  "owner": "agente:Claude",
  "due": "2026-11-20",
  "day": "2026-11-16",
  "deps": ["CO-01"],
  "desc": "Tabla con precio, plazo y garantía. Recomendar una.",
  "notes": [
    {
      "at": "2026-11-13T09:12:00Z",
      "by": "human",
      "text": "Mira las ofertas adjuntas en CO-01."
    }
  ]
}
```

- `state`: `proposed` (propuesta), `todo` (por hacer), `doing` (en curso), `review` (para revisar) o `done` (hecha).
- `owner`: `yo` (la persona), el nombre de una persona, `agente` (cualquier agente) o `agente:Nombre` (solo ese agente).
- `due` es la fecha límite y `day` el día planificado, como `AAAA-MM-DD`. `done` es el día en que se terminó.
- `deps`: tareas que tienen que estar en `done` antes de empezar esta.
- Notas: `at` en UTC sin milisegundos (`2026-11-13T09:12:00Z`), `by` con el nombre de tu herramienta en minúsculas (`claude-code`, `copilot`), `text` en Markdown.
- Las notas que empiezan por `✉ **Correo` son correos adjuntados por la persona: léelas, no las cambies.

## Qué puedes hacer

1. **Coger una tarea** solo si se cumplen las tres cosas:
   - está en `todo`;
   - todas sus `deps` están en `done`;
   - su `owner` es `agente`, `agente:` con tu nombre, o está vacío.

   Si la persona te pide una tarea de `yo`, de una persona o de otro agente, no la toques y díselo.
2. **Empezar**: pasa `state` a `doing` y añade una nota con tu plan.
3. **Terminar**: pasa `state` de `doing` a `review` y añade una nota que diga qué hiciste, qué comprobaste y qué tiene que decidir la persona.
4. **Pausar**: de `doing` a `todo`, con una nota de por qué.
5. **Proponer tareas nuevas**: añade tareas con `state` `proposed`, `by` con tu nombre y `at` con la hora. El `id` es el prefijo del grupo y el número siguiente libre de ese grupo, con dos cifras (`CO-03`). Sin grupo, el prefijo es `G`.
6. **Añadir notas** a cualquier tarea en la que trabajes.

Para proyectos de contratas, sigue además [CONTRATAS.md](CONTRATAS.md): ahí la persona te autoriza a crear ciertas tareas ya aprobadas.

## Qué no puedes hacer

- Pasar nada a `done`, aprobar propuestas (`proposed` → `todo`) ni cambiar el título, la descripción, el grupo, el responsable o las fechas de una tarea aprobada. Eso lo hace la persona en el navegador.
- Borrar tareas, notas o correos.
- Cambiar tareas de otros proyectos sin que te lo pidan.

## Si la persona devuelve tu trabajo

Una nota suya que empieza por `Sent back:` es lo que tienes que corregir. Una que empieza por `Changes requested:` en una propuesta te pide rehacerla: cambia la propuesta y responde con una nota.

## Al guardar el archivo

- Lee el `kanvas.json` justo antes de cambiarlo: la persona puede haberlo cambiado en el navegador.
- Cambia solo lo que toca, y guárdalo con dos espacios de sangría y un salto de línea al final.
- Comprueba que sigue siendo JSON válido. Si lo rompes, el proyecto deja de abrirse.
