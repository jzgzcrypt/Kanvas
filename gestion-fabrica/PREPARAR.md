# Preparar Gestión fábrica

Instrucciones para el agente (Claude, Copilot u otro en VS Code) que deja lista la carpeta de proyectos. La persona solo le dice:

> Sigue `gestion-fabrica/PREPARAR.md` y déjalo todo preparado.

El PC no tiene Python ni permite ejecutar programas: todo se hace creando y copiando archivos.

## 1. Preguntar antes de crear nada

Pregunta a la persona, en una sola vez:

1. Dónde crear la carpeta. Propón `Documentos\Gestión fábrica`.
2. Qué proyectos quiere, con su nombre. Siempre se añade además uno llamado `Temas generales`.
3. Para cada proyecto, si quiere dividirlo en fases y cuáles (por ejemplo `Análisis`, `Compra`, `Instalación`). Si no dice nada, sin fases.

No crees nada hasta tener las respuestas.

## 2. Crear la carpeta

```
Gestión fábrica\
├── kanvas.html                       ← copia de kanvas.html de este repositorio
├── AGENTS.md                         ← copia de gestion-fabrica/AGENTS.md
├── CLAUDE.md                         ← una línea: Lee AGENTS.md antes de tocar ningún proyecto.
├── .github\copilot-instructions.md   ← la misma línea
├── <Proyecto 1>\
│   └── kanvas.json
├── <Proyecto 2>\
│   └── kanvas.json
└── Temas generales\
    └── kanvas.json
```

- La subcarpeta de cada proyecto lleva el nombre del proyecto. Quita de él los caracteres que Windows no admite: `\ / : * ? " < > |`.
- Si una carpeta o archivo ya existe, no lo sobrescribas: díselo a la persona.

## 3. El `kanvas.json` de cada proyecto

Sin fases, exactamente así (UTF-8, dos espacios de sangría, salto de línea al final):

```json
{
  "kanvas": 1,
  "title": "Mejora línea 3",
  "groups": [],
  "tasks": []
}
```

Con fases, cada una es un grupo con un prefijo de 1 a 6 letras mayúsculas que empezará el código de sus tareas:

```json
{
  "kanvas": 1,
  "title": "Mejora línea 3",
  "groups": [
    {
      "id": "AN",
      "name": "Análisis"
    },
    {
      "id": "CO",
      "name": "Compra"
    }
  ],
  "tasks": []
}
```

Los prefijos no se repiten dentro de un proyecto. `title` es el nombre que se ve en la pestaña Proyectos.

## 4. Comprobar y avisar

1. Abre cada `kanvas.json` y comprueba que es JSON válido.
2. Di a la persona qué has creado y dónde.
3. Explícale el primer paso: abrir `kanvas.html` con Edge (doble clic) y pulsar **Abrir carpeta de proyectos**, eligiendo `Gestión fábrica`.
4. Recuérdale que las tareas se crean desde el navegador, o pidiéndotelo a ti siguiendo `AGENTS.md`.
