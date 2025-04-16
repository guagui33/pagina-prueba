---
{"dg-publish":true,"permalink":"/pagina-web-prueba/0011-nosotros/"}
---




<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



### Preguntas Frecuentes sobre Inteligencia de Negocios con Excel y Power BI

**1. ¿Qué es DAX y cuál es su importancia en el contexto de Power BI y Excel?**

DAX (Data Analysis Expressions) es un lenguaje de funciones utilizado en Power BI, Power Pivot para Excel y SSAS (SQL Server Analysis Services) en su modelo tabular. Su propósito principal es extraer información valiosa de conjuntos de tablas relacionadas en un modelo de datos. DAX permite a los analistas de datos, estadísticos y cualquier persona que trabaje con grandes volúmenes de información, crear cálculos personalizados (conocidos como Medidas, Columnas Calculadas y Tablas Calculadas) para analizar, manipular y moldear los datos según sus necesidades. Estos cálculos son fundamentales para generar métricas, indicadores y análisis que respaldan la toma de decisiones empresariales informadas. La importancia de DAX radica en su capacidad para transformar datos brutos en conocimiento accionable, convirtiéndose en una herramienta esencial para la inteligencia de negocios moderna.

**2. ¿Cuáles son los tres tipos principales de cálculos DAX y en qué se diferencian?**

Los tres tipos principales de cálculos en DAX son:

- **Medidas:** Son fórmulas que se agregan al área de valores de una matriz en Power BI o al área de valores de una tabla dinámica en Excel. Las medidas realizan cálculos agregados sobre los datos, como sumas, promedios, conteos, etc., y su resultado depende del contexto en el que se utilizan dentro de una visualización. Son dinámicas y se evalúan en tiempo real en función de los filtros y el contexto de fila aplicados.
- **Columnas Calculadas:** Son columnas que se agregan a una tabla existente en el modelo de datos. La fórmula DAX para una columna calculada se evalúa fila por fila durante el procesamiento de la tabla y su resultado se almacena en la columna para cada fila. Son estáticas en el sentido de que su valor se calcula una vez (o cuando se actualiza el modelo) y permanece constante hasta la siguiente actualización. Se basan en el contexto de fila.
- **Tablas Calculadas:** Son tablas virtuales que se crean utilizando una expresión DAX. A diferencia de las tablas importadas o conectadas directamente a una fuente de datos, las tablas calculadas se derivan de los datos existentes en el modelo. Son útiles para crear tablas intermedias, resumir datos o generar secuencias de fechas, entre otros escenarios.

**3. ¿Qué son las Medidas implícitas y explícitas en Power BI y por qué se recomienda usar las explícitas?**

- **Medidas Implícitas:** Son medidas básicas que Power BI crea automáticamente cuando se arrastra un campo numérico al área de valores de una visualización sin haber creado previamente una medida DAX. Por defecto, Power BI aplica una función de agregación como suma, promedio, conteo, etc. La fórmula subyacente de una medida implícita no es visible y no se sabe con certeza si internamente utiliza DAX o algún otro algoritmo.
- **Medidas Explícitas (Manuales o Automáticas):** Son medidas creadas por el usuario utilizando el lenguaje DAX. Las medidas explícitas manuales se escriben completamente por el usuario, definiendo la fórmula DAX específica. Las medidas explícitas automáticas son una funcionalidad de Power BI para crear rápidamente ciertas medidas comunes, pero aun así generan una fórmula DAX visible y editable.

Se recomienda enfáticamente la utilización de medidas explícitas porque la fórmula DAX asociada es transparente, lo que permite comprender, reutilizar y optimizar el cálculo. Las medidas implícitas no pueden ser referenciadas o reutilizadas en otras medidas, lo que limita su flexibilidad y dificulta la creación de análisis más complejos.

**4. ¿Qué es el lenguaje M y cuál es su rol en Power BI y Excel?**

El lenguaje M es el lenguaje de fórmulas utilizado en Power Query para Excel y Power BI. Su principal rol es la preparación y transformación de datos. Con M, los usuarios pueden conectarse a diversas fuentes de datos, limpiar, dar forma y combinar datos para prepararlos para el modelado y el análisis en Power BI o Excel. Permite realizar operaciones complejas de transformación de datos a través de una sintaxis funcional, incluyendo la extracción, transformación y carga (ETL) de datos. Aunque este libro se centra en DAX para el análisis, el lenguaje M es fundamental en las etapas iniciales del proceso de inteligencia de negocios para asegurar la calidad y la estructura adecuada de los datos.

**5. ¿Cuáles son los tres pasos primordiales que se deben entender para dominar DAX?**

Para comprender cómo el motor DAX evalúa las expresiones, es crucial internalizar tres pasos primordiales:

1. **Identificar Filtros:** Para cada valor en el área de valores de una medida, el motor DAX identifica los filtros que están activos en ese contexto particular. Estos filtros provienen de las filas y columnas de la visualización (contexto de filtro).
2. **Aplicar Filtros:** Una vez identificados, estos filtros se aplican a las tablas del modelo de datos, reduciendo el conjunto de datos que se considerará para el cálculo. La propagación de filtros a través de las relaciones entre tablas también ocurre en este paso.
3. **Ejecutar Expresión DAX:** Finalmente, la expresión DAX de la medida se ejecuta sobre el subconjunto de datos filtrado. El resultado de esta ejecución es el valor que se muestra en la visualización.

Entender que estos tres pasos se aplican de forma independiente para cada "casilla" en una visualización es fundamental para predecir y comprender los resultados de las medidas DAX.

**6. ¿Qué son el Contexto de Filtro y el Contexto de Fila en DAX y cómo influyen en los cálculos?**

- **Contexto de Filtro:** Es el subconjunto de datos que está visible para una expresión DAX en una medida debido a los filtros aplicados por los elementos de una visualización (filas, columnas, filtros de página, etc.) y la propagación de estos filtros a través de las relaciones del modelo de datos. Define el entorno en el que se evalúa una medida.
- **Contexto de Fila:** Existe principalmente en el contexto de las columnas calculadas y en ciertas funciones de iteración (como las funciones con el sufijo 'X'). Representa la fila actual que se está procesando durante la evaluación de una expresión DAX. En una columna calculada, la fórmula se evalúa para cada fila de la tabla, teniendo en cuenta los valores de esa fila en particular.

Ambos contextos son cruciales para entender cómo DAX llega a los resultados de los cálculos. El contexto de filtro determina qué datos se agregan o analizan en una medida, mientras que el contexto de fila influye en los cálculos que se realizan a nivel de cada registro en columnas calculadas o dentro de funciones de iteración. A veces, ambos contextos coexisten y se combinan para la evaluación de una expresión DAX (contexto de evaluación).

**7. ¿Qué son las funciones de iteración (con sufijo X) y las funciones ALLxxxx en DAX y para qué se utilizan?**

- **Funciones de Iteración (con sufijo X):** Son un conjunto de funciones DAX que realizan una operación (como SUM, AVERAGE, COUNT, MIN, MAX) sobre cada fila de una tabla o una expresión tabular y luego agregan los resultados de esas iteraciones para devolver un valor único. Ejemplos comunes incluyen SUMX, AVERAGEX, COUNTX, etc. Su sintaxis general implica especificar una tabla y una expresión que se evalúa para cada fila de esa tabla. Se utilizan cuando se necesita realizar cálculos basados en el valor de cada fila y luego agregar esos resultados.
- **Funciones ALLxxxx:** Son una familia de funciones tabulares en DAX (como ALL, ALLEXCEPT) que tienen la característica de ignorar o eliminar los filtros del contexto de filtro.
- **ALL(Tabla):** Devuelve todas las filas de una tabla, ignorando cualquier filtro que pueda estar aplicado.
- **ALL(Columna1, Columna2, ...):** Devuelve una tabla con todas las combinaciones únicas de los valores de las columnas especificadas, ignorando los filtros.
- **ALLEXCEPT(Tabla, Columna1, Columna2, ...):** Devuelve todas las filas de una tabla, pero preserva los filtros aplicados a las columnas especificadas.

Estas funciones son esenciales para realizar cálculos como porcentajes del total general, comparaciones con valores no filtrados y en escenarios donde se necesita manipular el contexto de filtro dentro de una medida, a menudo en combinación con la función CALCULATE.

**8. ¿Cuál es la importancia de la función CALCULATE en DAX y cómo se utiliza para modificar el contexto de filtro?**

La función CALCULATE es una de las funciones más poderosas y fundamentales en DAX, considerada la "crema y nata" de las funciones. Su principal importancia radica en su capacidad única para modificar el contexto de filtro durante la evaluación de una expresión. Permite realizar cálculos bajo condiciones de filtro diferentes a las que están actualmente activas en la visualización.

La sintaxis básica de CALCULATE es:

CALCULATE(<Expresión>, [<Filtro1>], [<Filtro2>], ...)

- <Expresión>: Es la expresión DAX que se va a evaluar (generalmente una medida agregada).
- [<Filtro1>], [<Filtro2>], ...: Son las condiciones de filtro que se aplicarán para modificar el contexto existente. Estos filtros pueden ser expresiones que devuelven una tabla, filtros directos sobre columnas o incluso el resultado de otras funciones (como FILTER o ALL).

Cuando se utiliza CALCULATE, el motor DAX primero evalúa el contexto de filtro actual, luego aplica los filtros especificados en los argumentos de CALCULATE (reemplazando o añadiendo filtros según sea necesario), y finalmente evalúa la <Expresión> dentro de este nuevo contexto de filtro modificado. Esto permite crear medidas que calculan valores basados en filtros específicos, independientemente de los filtros aplicados en la visualización, lo que es crucial para análisis avanzados como cálculos de participación, ventas por categoría específica, o acumulados en el tiempo.

convert_to_textConvertir en fuente

Es posible que NotebookLM muestre información imprecisa. Verifica las respuestas.

</div></div>


