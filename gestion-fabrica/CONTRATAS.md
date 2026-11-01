# Seguimiento de una contrata

Cómo llevar en un proyecto el cumplimiento de una contrata de mantenimiento: preventivos del contrato, avisos de avería (correctivos) con su plazo de atención, y el informe mensual. Kanvas recopila la información; el agente la analiza cuando la persona se lo pide.

## El proyecto

Un proyecto por contrata, por ejemplo `Contrata mantenimiento Norte`, con tres grupos:

| Grupo | Prefijo | Para qué |
|---|---|---|
| Preventivos | `PR` | Una tarea de seguimiento por mes |
| Averías | `AV` | Una tarea por aviso de avería |
| Seguimiento | `SE` | Informes mensuales, reuniones, incidencias del contrato |

En la carpeta del proyecto, un archivo `contrato.md` con lo que exige el contrato:

```markdown
# Contrato Norte · 2026–2028

## Plazos
- Atención de averías: menos de 5 horas desde el aviso.
- Cierre de averías: se mide y se informa cada mes.

## Preventivos
| Equipo | Frecuencia | Día del mes |
|---|---|---|
| Compresores nave 1 | mensual | 15 |
| Grúa puente | trimestral (ene, abr, jul, oct) | 10 |
| Extintores | anual (noviembre) | 25 |
```

El agente lo lee para saber qué toca cada mes y qué plazos medir. Si cambia el contrato, se cambia este archivo.

## Lo que hace la persona

- **Avisar una avería:** crea la tarea `AV` con lo que pasa («Fuga hidráulica prensa 4»), responsable la persona de la contrata, y arrastra a la tarjeta el correo de aviso enviado. La hora del correo es la hora del aviso.
- **Seguir la avería:** arrastra los correos que lleguen. Si algo no llega por correo, añade una nota con este formato, una por línea:
  - `Llegada: 13/11/2026 11:30`
  - `Cierre: 14/11/2026 09:00`
  
  Al cierre, la marca hecha.
- **Preventivos:** durante el mes marca en la lista de la tarea de seguimiento los preventivos que se hacen, y arrastra el parte de cada uno.
- **Pedir al agente** lo que toca, con las frases de abajo.

## Lo que hace el agente

Sigue `AGENTS.md`, con dos excepciones que la persona autoriza para estas tareas: crearlas ya aprobadas (`todo` o `review`), sin pasar por propuesta, y pasar la tarea de seguimiento de preventivos de `todo` a `review` al cerrarla.

### «Abre los preventivos de noviembre en Contrata Norte»

1. Lee `contrato.md` y saca los preventivos que tocan ese mes.
2. Crea en el grupo `PR` la tarea `Seguimiento preventivos noviembre 2026`, en `todo`, responsable `yo`, fecha límite el último día del mes.
3. En la descripción, una lista con un punto por preventivo y su fecha:

   ```markdown
   - [ ] Compresores nave 1 · 15/11
   - [ ] Extintores · 25/11
   ```

4. Si ya existe la tarea de ese mes, no crea otra: lo dice.

### «Cierra los preventivos de noviembre en Contrata Norte»

1. Lee la tarea de seguimiento de ese mes: puntos marcados, notas y correos adjuntos.
2. Un preventivo **cumple** si está marcado y su parte llegó en su fecha o antes; **incumple** si no está marcado, o llegó tarde (di cuántos días).
3. Añade una nota con el resultado:

   ```markdown
   **Preventivos noviembre 2026: 1 de 2 cumplidos (50 %)**
   - Compresores nave 1 · cumple (parte del 14/11)
   - Extintores · incumple: sin parte a 30/11
   ```

4. Pasa la tarea a `review`, para que la persona la revise y la dé por hecha.

### «Actualiza la traza de AV-12» (o «de las averías abiertas»)

1. Lee la tarea: correos (`✉ **Correo enviado/recibido** · fecha hora`) y notas `Llegada:` / `Cierre:`.
2. Aviso = el primer correo enviado por la persona. Llegada y cierre = las notas, o el correo de la contrata que lo diga.
3. Añade una nota con la traza:

   ```markdown
   **Traza AV-12**
   - Aviso: 13/11/2026 08:10
   - Llegada: 13/11/2026 11:30 · 3 h 20 min · cumple (< 5 h)
   - Cierre: 14/11/2026 09:00 · 24 h 50 min desde el aviso
   ```

4. Si falta un dato, lo dice en la nota («sin hora de llegada») en vez de suponerlo.

### «Haz el informe de noviembre de Contrata Norte»

1. Lee las tareas `PR` y `AV` del mes (una avería cuenta en el mes de su aviso).
2. Calcula:
   - preventivos cumplidos sobre los que tocaban, en %;
   - averías atendidas en menos de 5 h sobre las avisadas, en %;
   - tiempo medio y máximo de cierre de las averías cerradas;
   - averías aún abiertas.
3. Crea en el grupo `SE` la tarea `Informe noviembre 2026`, en `review`, responsable `yo`, con el informe en la descripción: los ratios arriba y debajo la lista de incumplimientos, cada uno con su código (`PR-03`, `AV-12`) para poder abrirlo.
4. Guarda una copia en la carpeta del proyecto, en `informes/2026-11.md`.
5. No inventa datos: si a una avería le falta una hora, la cuenta aparte como «sin datos» y lo dice.
