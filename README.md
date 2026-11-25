# UML · Diagramas de clases y de comportamiento

Curso de modelado con UML para el módulo de Entornos de Desarrollo, creado con MkDocs Material. Continúa el curso [POO](https://rlrprofe.github.io/poo/) y usa su mismo hilo de ejemplos: una empresa de alquiler de vehículos.

## Puesta en marcha

```powershell
python -m pip install -r requirements.txt
python -m mkdocs serve
```

Visita `http://127.0.0.1:8000/`.

## Publicación

El workflow `.github/workflows/deploy.yml` construye el sitio y lo publica en la rama `gh-pages` con cada `push` a `main`.

Solo la primera vez, en GitHub: **Settings → Pages → Source: Deploy from a branch → `gh-pages` / `(root)`**.

Si prefieres desplegar a mano: `python -m mkdocs gh-deploy --force`.

## Estructura

```text
docs/
  index.md        Portada y recorrido
  capitulos/      Capítulos del curso
  anexos/         Glosario y mapa mental de notación
  img/            Imágenes y diagramas SVG
```
