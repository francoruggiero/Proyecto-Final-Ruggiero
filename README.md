# Proyecto Final - Arroyo Capital

Analisis de inversion y portafolio en la industria del cine para Programacion Analitica II.

## Contenido

- datos/peliculas.csv: base historica de peliculas.
- datos/ipc_eeuu.csv: indice de precios de Estados Unidos.
- notebooks/proyecto_final_cine_Ruggiero.ipynb: analisis reproducible.
- salidas/: graficos exportados en HTML y PNG.
- salidas/correlaciones_peliculas.png: mapa de calor exportado para consultar o presentar.
- .gitignore: archivos locales que no deben subirse al repositorio.
- Proyecto Final B - Portafolio de cine.pdf: consigna del proyecto.

## Como reproducir

Verificado con Python 3.11.9 y pandas 2.2.3. Desde PowerShell, ubicarse en la carpeta raiz del proyecto y ejecutar:

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyter lab
```

Abrir `notebooks/proyecto_final_cine_Ruggiero.ipynb`, seleccionar el kernel de ese entorno y ejecutar todas las celdas en orden desde el comienzo. En VS Code se puede abrir el mismo archivo y usar «Reiniciar kernel y ejecutar todo».

La notebook usa rutas relativas a la carpeta `notebooks`, por lo que debe conservarse la estructura del repositorio. Al ejecutar la etapa IV se regeneran los archivos de `salidas/`.

## Etapas incluidas

- Etapa 1, secciones 1.1 a 1.12: carga, revision, limpieza, presupuesto faltante e IPC.
- Etapa 2, seccion 2.1: importes constantes de 2020, retorno e indicador de recuperacion segun la regla de 2,5x.
- Etapa 3, secciones 3.1 a 3.3: evolucion nominal y real, retorno por genero y franquicia, relacion con IMDb, riesgo y dominancia.
- Etapa 4, secciones 4.1 a 4.4: evolucion nominal/real, distribucion del retorno, comparacion por genero y dispersion presupuesto-recaudacion. Cada grafico tiene una conclusion debajo. La evolucion queda en una unica figura interactiva de Plotly y muestra 1980-2019; 2020 sigue en la tabla anual pero se excluye de la tendencia por tener solo 15 recaudaciones informadas entre 25 peliculas.
- Etapa 5, secciones 5.1 a 5.3: propuesta para USD 500 millones. Primero se comparan grupos, luego se explica el reparto y se verifica el costo por proyecto; después se calcula retorno y riesgo. La conclusión para inversionistas, con las decisiones y limitaciones del análisis, está en 5.3.

El 28,94 % de las peliculas de la base limpia no tiene presupuesto. Se conservan para los analisis donde no se necesita y se excluyen del retorno, la dispersion y la tesis; no se imputan como cero. En la etapa 1 se eliminan 58 duplicados exactos y 14 versiones alternativas con ID 90xxx; se corrige el signo de 11 recaudaciones y se multiplican por 1.000 los 40 presupuestos cargados en escala de miles. Estas decisiones se verificaron contra el [CSV original del autor](https://github.com/danielgrijalva/movie-stats/blob/master/movies.csv). La lista de ID corregidos queda en el notebook y la ejecucion no requiere Internet; los presupuestos bajos genuinos se conservan. En la dispersion solo entran importes positivos y conocidos; los ejes usan dolares constantes de 2020 y escala logaritmica para mostrar todos los tamanos sin recortar extremos. Los colores y la linea de referencia distinguen las peliculas que superan 2,5 veces el presupuesto de las que no.

El retorno se presenta como multiplo de recaudacion mundial sobre presupuesto de produccion. No es una ganancia neta del estudio, porque la consigna advierte que faltan marketing, distribucion y la participacion del exhibidor.

La referencia de planificación ponderando medianas es 3,09 veces y no es una promesa de ganancia neta. La frecuencia simulada de no superar el umbral de 2,5 veces es 6,8 %; depende de independencia entre proyectos y de usar el pasado como referencia. No hubo validación fuera de muestra. El conteo histórico anual no mide la oferta de franquicias accesibles al fondo.

Para la etapa 5, el riesgo de perder capital se aproxima mediante esa regla de recuperación de 2,5 veces; no es una estimación de la pérdida contractual neta del fondo. Los cortes de presupuesto se calculan sobre las 5.389 películas con retorno válido y después se seleccionan las franquicias de cada tramo.

## Lectura del análisis

Para una primera lectura, seguir los textos «Qué encontramos» y «Decisión» del cuaderno y terminar en 5.3. Para revisar un cálculo, consultar las tablas de cada etapa. Los motivos de las decisiones se explican junto al paso correspondiente, no solo al final.

La revisión local no equivale a la entrega: hay que comprobar que el repositorio de GitHub contiene esta versión, agregar al otro integrante como colaborador si corresponde y enviar el enlace por el medio solicitado. La presentación ejecutiva sigue siendo una instancia separada.
