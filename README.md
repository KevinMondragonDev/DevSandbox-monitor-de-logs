# DevSandbox-monitor-de-logs

> ETL incremental en Python que procesa los logs diarios de una API y resume errores, rutas lentas y horas anómalas.

**Estado:** 🚧 sin empezar · **Categoría:** DevSandbox · **Tipo:** ETL incremental en Python · **Módulo del programa:** 04 · Retos de Python

## Qué significa el nombre

El prefijo del repositorio indica el tamaño del proyecto:

| Prefijo | Tamaño | Qué es |
|---|---|---|
| **`DevSandbox-`** ← este | Hasta 8 h | Un proyecto pequeño para practicar un tema concreto: un espacio para probar, equivocarse y terminar rápido |
| `NightBuilds-` | 8 h o más | Un proyecto grande, con varias piezas (base de datos, orquestación, nube o API) y decisiones de diseño propias |

Este es un **DevSandbox**: el reto está estimado en 6–8 h.

## La problemática

La API de un banco escribe un log por día y, cuando algo falla, alguien lo revisa a mano. Nadie sabe cuántos errores hubo ayer ni qué ruta es la más lenta. Hace falta un programa que procese cada día, resuma lo importante y no repita lo ya procesado.

## Los datos

| Dónde | Qué es |
|---|---|
| `datos/` (6 archivos) | Seis archivos de log (1 al 5 de julio de 2026, unas 2,000 líneas cada uno), con líneas malformadas, un archivo repetido y un día en el que pasó algo |

Los archivos de `datos/` son **sintéticos**, generados para practicar: no corresponden a personas ni a operaciones reales.

## Qué hay que construir

El enunciado completo, con sus hitos y cómo comprobar cada uno, está en [`RETO.md`](RETO.md). No trae solución: el diseño es tuyo.

- [`docs/REGLAS.md`](docs/REGLAS.md): cómo se trabaja un DevSandbox y qué debe tener este README al terminar.
- [`docs/RUBRICA.md`](docs/RUBRICA.md): con qué criterios se evalúa.

## Cómo se ejecuta

*Pendiente: se escribe al cerrar el primer hito. Los comandos exactos, desde `git clone`.*

## Decisiones

*Pendiente: tres decisiones técnicas y la alternativa que se descartó en cada una.*

## Qué aprendí

*Pendiente.*

---

Reto del programa de Python e ingeniería de datos: [UNIR_Python_Certification](https://github.com/KevinMondragonDev/UNIR_Python_Certification).
