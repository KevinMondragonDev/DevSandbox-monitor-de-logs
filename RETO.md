# 🚀 Sideproject — Monitor de logs

**Repositorio:** `sideproject-monitor-de-logs` · **Tipo:** ETL incremental en Python · **Tiempo:** 6–8 h · **Después de:** los retos 1 a 14

> Reglas, README y lista de cierre: [`SIDEPROJECTS.md`](docs/REGLAS.md). Evaluación: [`RUBRICA.md`](docs/RUBRICA.md). **No hay solución: el diseño es tuyo.**

## El caso

La API de un banco escribe un archivo de log por día. Cuando algo falla, alguien abre el archivo y busca a mano. Nadie sabe cuántos errores hubo ayer, qué ruta es la más lenta ni si el martes pasó algo raro. Te piden un programa que procese los logs de cada día y deje un resumen que cualquiera pueda leer, sin volver a procesar lo que ya procesó.

## Datos

`datos/`: seis archivos, del 1 al 5 de julio de 2026, con unas 2,000 líneas cada uno. Cada línea tiene esta forma:

```
2026-07-01T10:00:01Z GET /api/cuentas/12 200 35ms usuario=ana
```

Como en la vida real, hay líneas que no cumplen el formato, un archivo llega dos veces y en uno de los días pasó algo. Son datos sintéticos.

## Qué practicas

| Retos | Dónde aparece |
|---|---|
| 3, 7 | Procesar texto y logs línea a línea |
| 4, 6, 13 | Validar, limpiar y medir la calidad |
| 8 | Funciones pequeñas con una sola tarea |
| 9, 10 | Configuración fuera del código y reintentos |
| 11, 12 | Extraer, transformar y cargar; salida en JSON |
| 14 | Procesar solo lo nuevo |

## Hitos

**Hito 1 — Una línea.** Una función que convierte una línea en un diccionario con sus campos tipados, y que distingue con claridad una línea válida de una que no lo es.
*Comprueba:* pruébala con 5 líneas buenas y 5 malas escritas por ti.

**Hito 2 — Un archivo.** Procesa un día completo sin cargarlo entero en memoria. Las líneas inválidas se cuentan y se guardan aparte con su motivo.
*Comprueba:* válidas + inválidas = líneas del archivo.

**Hito 3 — El resumen.** Por día: peticiones totales, porcentaje de errores, las tres rutas más lentas y las tres con más errores. Se guarda en JSON.
*Comprueba:* verifica dos números a mano con `grep` y `wc`.

**Hito 4 — Solo lo nuevo.** El programa recuerda qué archivos procesó. Ejecutarlo otra vez no repite trabajo, y el archivo que llega dos veces no cuenta doble.
*Comprueba:* la segunda ejecución dice «0 archivos nuevos».

**Hito 5 — Lo raro.** Una regla que marque cuándo un día o una hora se sale de lo normal. La definición de «normal» la decides tú y va en la configuración.
*Comprueba:* tu programa señala por sí solo el día y las horas en que pasó algo, sin que se lo digas.

**Hito 6 — Para otros.** Configuración en un archivo, mensajes con `logging` y un README con cómo ejecutarlo.
*Comprueba:* cambiar la carpeta de entrada no toca el código.

## Preguntas para defenderlo

- ¿Cómo sabe tu programa que un archivo ya fue procesado: por el nombre o por el contenido? ¿Qué pasa en cada caso con el reenvío?
- ¿Qué haces con una línea inválida y por qué no detener el programa?
- ¿Qué rutas agrupaste como «la misma» (`/api/cuentas/12` y `/api/cuentas/40`)? ¿Cómo?
- ¿Tu regla de «raro» habría avisado un día normal con mucho tráfico?

## Súbelo de nivel

- Una gráfica por día con las peticiones y los errores por hora.
- Cuando termines el módulo 05, vuelve y guarda los resúmenes en PostgreSQL y los logs limpios en Parquet.
