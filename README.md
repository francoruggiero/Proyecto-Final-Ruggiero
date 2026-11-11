# Proyecto Final — Arroyo Capital

Trabajo individual de Programación Analítica II sobre inversión en la industria del cine.

El objetivo es proponer cómo distribuir USD 500 millones entre proyectos cinematográficos durante tres años. Para fundamentar la propuesta, analizo la calidad de los datos, comparo resultados y riesgos, y presento los principales hallazgos con gráficos.

## Archivos del proyecto

- [Notebook del proyecto](notebooks/proyecto_final_cine_Ruggiero.ipynb): análisis completo, código, resultados y conclusiones.
- [Películas](datos/peliculas.csv): base histórica utilizada en el análisis.
- [IPC de Estados Unidos](datos/ipc_eeuu.csv): índice utilizado para expresar los importes en dólares constantes de 2020.
- [Gráficos exportados](salidas/): figuras en PNG y gráficos interactivos en HTML.
- [Dependencias](requirements.txt): paquetes y versiones del entorno utilizado.
- [Archivos excluidos de Git](.gitignore): entornos locales, archivos temporales y material personal.

La consigna de referencia es «Proyecto Final B — Portafolio de cine», proporcionada en el curso.

## Cómo ejecutar el análisis

El notebook se verificó con Python 3.11.9. Para reproducirlo en VS Code:

1. Abrir la carpeta del proyecto y tener instaladas las extensiones Python y Jupyter de VS Code.
2. Desde una terminal de PowerShell ubicada en esa carpeta, crear un entorno e instalar las dependencias:

   ```powershell
   py -3.11 -m venv .venv
   .\.venv\Scripts\python.exe -m pip install -r requirements.txt
   ```

3. Abrir el [notebook](notebooks/proyecto_final_cine_Ruggiero.ipynb) y seleccionar como kernel el entorno `.venv` recién creado.
4. Usar «Reiniciar kernel y ejecutar todo», ejecutando las celdas desde el comienzo.

Hay que conservar la estructura de carpetas: el notebook busca los CSV en `../datos/` y guarda las figuras en `../salidas/`, tomando como punto de partida su carpeta. En la etapa 4 se regeneran los gráficos exportados. La ejecución utiliza los archivos locales y no necesita descargar datos; la instalación inicial de paquetes sí puede requerir Internet.

## Organización del notebook

- **Etapa 1 — Revisión y limpieza (1.1–1.12):** carga de archivos, tipos de datos, duplicados, valores incorrectos, faltantes y unión con el IPC.
- **Etapa 2 — Variables para comparar (2.1):** presupuesto y recaudación constantes, retorno y recuperación según la regla del caso.
- **Etapa 3 — Análisis de resultados y riesgos (3.1–3.3):** evolución de la recaudación, comparación por género y franquicia, relación con IMDb y comparación de segmentos.
- **Etapa 4 — Visualización (4.1–4.4):** evolución nominal y real, distribución del retorno, comparación por género y dispersión entre presupuesto y recaudación. Cada gráfico tiene su conclusión.
- **Etapa 5 — Propuesta de inversión (5.1–5.3):** definición de grupos, distribución de los USD 500 millones, cantidad y costo de los proyectos, estimación del retorno y del riesgo, y conclusión para los inversionistas.

## Gráficos para consultar

Los archivos HTML se pueden abrir en un navegador y permiten consultar información al pasar el cursor:

- [Evolución de la recaudación nominal y real](salidas/evolucion_industria_interactiva.html).
- [Retorno mediano por género](salidas/retorno_mediano_por_genero_interactiva.html).
- [Presupuesto y recaudación](salidas/presupuesto_recaudacion_interactiva.html).

También se incluyen la [distribución del retorno](salidas/distribucion_retorno.png) y el [mapa de correlaciones](salidas/correlaciones_peliculas.png). GitHub puede mostrar el código de los HTML en lugar del gráfico: para interactuar con ellos, descargar el archivo y abrirlo en un navegador.

## Decisiones importantes para interpretar los resultados

- **Presupuestos faltantes:** el 28,94 % de las películas de la base limpia no tiene presupuesto informado. Esas películas se conservan donde el análisis no necesita ese dato, pero se excluyen del cálculo del retorno, de la dispersión y de la propuesta de inversión. No se reemplazan los faltantes por cero.
- **Correcciones de la base:** se eliminan 58 duplicados exactos y 14 versiones alternativas con ID 90xxx. Se corrige el signo de 11 recaudaciones y se multiplican por 1.000 los 40 presupuestos identificados en escala de miles. El detalle queda en la etapa 1; no se modifican los CSV originales ni se corrigen todos los presupuestos pequeños por igual. Los casos se cotejaron con la [base original de películas](https://github.com/danielgrijalva/movie-stats/blob/master/movies.csv).
- **Comparación entre años:** los importes reales se expresan en dólares de 2020. El gráfico de evolución muestra 1980–2019; 2020 permanece en la tabla, pero no en la curva porque solo tiene 15 recaudaciones informadas entre 25 películas.
- **Qué significa el retorno:** es la recaudación mundial dividida por el presupuesto de producción. Por ejemplo, 3 veces significa recaudar USD 3 por cada USD 1 de presupuesto, no ganar USD 3 netos. Para considerar recuperada una película, la regla de la consigna exige superar 2,5 veces el presupuesto.
- **Dispersión:** solo se muestran presupuestos y recaudaciones positivos y conocidos. La escala logarítmica permite ver películas de tamaños muy diferentes, y la línea de referencia y los colores distinguen cuáles superan el umbral de 2,5 veces.
- **Propuesta de inversión:** usando las medianas de los grupos, la referencia de recaudación es 3,09 veces el capital. En la simulación, el 6,8 % de las carteras no supera 2,5 veces. Esa frecuencia se usa como aproximación al riesgo de no recuperar según la regla del caso, no como una medición de la pérdida neta contractual del fondo.

## Alcance y limitaciones

La recaudación de boletería no es ganancia neta: faltan costos y condiciones de distribución para calcular cuánto recibiría el inversionista. Además, los resultados dependen de los datos disponibles, del comportamiento histórico y del supuesto de independencia entre proyectos en la simulación. No se realizó una validación fuera de muestra ni se demuestra que el fondo tenga acceso a los proyectos propuestos.

La conclusión final está en 5.3. La propuesta sirve para orientar una decisión y explicar sus riesgos, no para garantizar un rendimiento.