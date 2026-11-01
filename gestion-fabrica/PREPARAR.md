# Preparar Gestión fábrica

Instrucciones para el agente (Claude, Copilot u otro en VS Code) que deja lista la carpeta de proyectos. La persona solo le dice:

> Sigue `gestion-fabrica/PREPARAR.md` y déjalo todo preparado.

El PC tiene Python. En Windows el comando puede ser `python` o `py`; prueba cuál responde con `python --version`.

## 1. Preguntar antes de crear nada

Pregunta a la persona, en una sola vez:

1. Dónde crear la carpeta. Propón `Documentos\Gestión fábrica`.
2. Qué proyectos quiere. Siempre se añade además uno llamado `Temas generales`.
3. Para cada proyecto, si quiere dividirlo en fases y cuáles (por ejemplo `Análisis`, `Compra`, `Instalación`). Si no dice nada, sin fases.

No crees nada hasta tener las respuestas.

## 2. Crear la carpeta

1. Crea la carpeta `Gestión fábrica`.
2. Copia dentro, desde este repositorio, `kanvas.html`, `kanvas.py` y la carpeta `skill` (con su `SKILL.md`). `kanvas.py` los necesita al lado para preparar cada proyecto.
3. Copia `gestion-fabrica/AGENTS.md` a la carpeta, y crea `CLAUDE.md` con una sola línea: `Lee AGENTS.md antes de tocar ningún proyecto.`

Si algo ya existe, no lo sobrescribas: díselo a la persona.

## 3. Crear cada proyecto

Desde la carpeta `Gestión fábrica`, por cada proyecto, crea su subcarpeta y prepárala:

```
mkdir "Mejora línea 3"
python kanvas.py init "Mejora línea 3"
```

Crea la subcarpeta con su `kanvas.json` (el título es el nombre de la carpeta) y las instrucciones para agentes del proyecto (`AGENTS.md` y `.agents\skills\kanvas\`). No sobrescribe nada.

Quita del nombre los caracteres que Windows no admite: `\ / : * ? " < > |`.

Si el proyecto lleva fases, crea un grupo por fase. El prefijo, de 1 a 6 letras, empieza el código de sus tareas (`AN-01`):

```
python kanvas.py add-group "Análisis" --prefix AN -b "Mejora línea 3\kanvas.json" --as claude-code
```

Firma con el nombre de tu herramienta en `--as`.

## 4. Comprobar y avisar

1. Comprueba cada proyecto con `python kanvas.py check -b "<proyecto>\kanvas.json"`.
2. Di a la persona qué has creado y dónde.
3. Explícale el primer paso: abrir `kanvas.html` con Edge (doble clic) y pulsar **Abrir carpeta de proyectos**, eligiendo `Gestión fábrica`.
