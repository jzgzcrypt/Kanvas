# Trabajar en los proyectos de Gestión fábrica

Cada subcarpeta con un `kanvas.json` es un proyecto. La persona los mira en Edge con `kanvas.html`, en la pestaña **Hoy**, y lo que cambies aparece allí en pocos segundos.

1. **Trabaja dentro de la carpeta del proyecto** y sigue su `AGENTS.md` y `.agents\skills\kanvas\SKILL.md`. Usa siempre los comandos de `.agents\skills\kanvas\kanvas.py`; no edites `kanvas.json` a mano.
2. **Firma con el nombre de tu herramienta** en cada comando: `--as claude-code`, `--as copilot`.
3. **Solo las tareas para un agente.** La persona elige el responsable de cada tarea: ella misma (`yo`), una persona, `agente` (cualquiera) o `agente:Claude` / `agente:Copilot`. `ready` solo te muestra las tuyas y `start` rechaza las demás. Si te piden una que no es tuya, díselo a la persona.
4. **No arranques `serve`.** La persona ya tiene el tablero abierto en Edge desde `kanvas.html`.
5. **Correos.** Las notas que empiezan por `✉ **Correo` son correos que la persona adjuntó a la tarea, y los `.msg` están en la carpeta `correos` del proyecto. Léelos si te sirven; no los cambies ni los borres.
6. **Fechas.** `due` es la fecha límite y `day` el día planificado; los pone la persona. Tenlos en cuenta para decirle qué corre prisa.
