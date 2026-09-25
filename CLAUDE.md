# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Qué es este repositorio

Documents Kit es una colección personal de notas, comandos y utilidades (Unix, Python/Django y herramientas como Docker, Git, tmux, Vim, bases de datos), escrita en **español** en reStructuredText y construida con Sphinx (tema `sphinx_rtd_theme`). Se publica en Read the Docs: https://documents-kit.readthedocs.io/es/latest/

No hay código de aplicación ni tests: todo el contenido vive en `docs/`. Los directorios `config/` y `documents_kit/` están vacíos (restos de la plantilla cookiecutter-django; solo se montan en el contenedor para que `sphinx-autobuild` los observe).

## Comandos

Con Docker (flujo previsto; sirve en http://localhost:7000 con recarga en vivo):

```bash
docker compose up docs
```

Sin Docker (desde `docs/`, tras `pip install -r requirements.txt`):

```bash
cd docs
make html                      # genera docs/_build/html
make html SPHINXOPTS="-W"      # tratar warnings como errores (útil para validar RST)
```

`make livehtml` asume la ruta `/app` del contenedor (`--watch $(APP)`); fuera de Docker usar `make livehtml APP=.` o `sphinx-autobuild . _build/html`.

## Estructura y convenciones

- `docs/index.rst` contiene los `toctree` por sección (`unix/`, `python/`, `packages/`). **Al añadir un `.rst` nuevo hay que registrarlo en el `toctree` correspondiente** o Sphinx no lo incluirá en la navegación (y emitirá un warning).
- Estilo habitual de las páginas: título con subrayado `=` largo, un campo `:synopsis:` con una descripción corta, secciones con `-`, y comandos en bloques `.. code-block:: bash` (o literales `::`), precedidos de una frase en español que explica qué hace el comando.
- Read the Docs construye con `.readthedocs.yaml` (Ubuntu 22.04, Python 3.12, `requirements.txt`); el Dockerfile local usa Python 3.9. Las versiones de Sphinx están fijadas en `requirements.txt`.
