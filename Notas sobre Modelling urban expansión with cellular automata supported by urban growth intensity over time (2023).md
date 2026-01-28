### Notas sobre Modelling urban expansión with cellular automata supported by urban growth intensity over time (2023)
[[Modelling urban expansion with cellular automata supported by urban growth intensity over time.pdf]]

Los **autómatas celulares (AC)** son una herramienta importante para simular cómo crecen y cambian las ciudades.
Sin embargo, como el crecimiento urbano es **irregular** en diferentes lugares (**heterogeneidad espacial**) y cambia con el tiempo de forma distinta en cada ciudad (**heterogeneidad temporal**), es difícil encontrar ==reglas claras que expliquen cómo se expande una ciudad==.
El desafío principal ha sido descubrir esas **reglas de expansión urbana** para hacer que las simulaciones con AC sean más precisas y reflejen mejor la realidad.

Para poder sobrellevar estas problemáticas a la hora de utilizar AC se han empleados diferentes métodos:
###### **Heterogeneidad Espacial y temporal:**
Existen dos enfoques
1) Uso de las características del vecindario:
	-  Conteo directo de celdas urbanas vecinas:
		- Se calcula cuántas celdas urbanas hay en un área específica alrededor de la celda analizada.
		- Se puede expresar como un número absoluto o una proporción.
		- Es el método más simple y directo.
	- Regresión ponderada geográficamente (GWR)
		- Permite analizar cómo la relación entre variables urbanas cambia en diferentes partes de la ciudad.
		- Útil para detectar patrones espaciales en la expansión urbana.
	- Autocorrelación espacial
		- Mide qué tan similar es una celda a sus vecinas en términos de urbanización.
		- Métodos como el **Índice de Moran** ayudan a identificar zonas con crecimiento similar.

2) División del área en regiones:
	- División por parches de tierra urbana
		- Se usan imágenes satelitales para identificar áreas urbanizadas.
		- Se asume que la expansión urbana está relacionada con el tamaño de estos parches
		- Luego, se asignan nuevas celdas urbanas en función de esta relación
	- División en zonas homogéneas
		- Se agrupan áreas con características urbanas similares (por ejemplo, densidad de población, uso de suelo o accesibilidad) ==Se podria usar el indice que dice que tan diverso es el uso de suelo?==
		- Se modela la expansión dentro de cada zona en lugar de tratar toda la ciudad como un solo sistema
	- Uso de grillas o subdivisiones administrativas
		- Se divide la ciudad en cuadriculas o en unidades espaciales predefenidas (barrios, distritos, municipios, etc)
		- Cada unidad se modela por separado para reducir el efecto de la heterogeneidad espacial

En general, **cada estudio elige un método de división según la escala del análisis y la disponibilidad de datos**. Algunos modelos pueden combinar métodos (por ejemplo, usar parches de tierra urbana dentro de zonas homogéneas) para mejorar la precisión.

Zhai et al. (2021) propusieron una mejora al enfoque 1 al incluir la **tasa de crecimiento anual** en el análisis del vecindario. Básicamente, en lugar de solo contar cuántas celdas urbanas hay alrededor, también consideraron **cómo ha cambiado la urbanización con el tiempo** en cada área.

Para esto, generaron **dos capas de heterogeneidad espacial**, lo que significa que agregaron más información para capturar mejor las diferencias entre vecindarios. Esto ayudó a mejorar las reglas de transición de los autómatas celulares, es decir, **las reglas que determinan si una celda cambiará de estado (de no urbana a urbana)**.

Sin embargo, a pesar de estas mejoras, **todavía no está completamente claro** cómo las características del vecindario afectan la probabilidad de que una nueva celda se urbanice. Esto sugiere que hay factores adicionales que influyen en la expansión urbana y que aún no se han modelado con precisión.

Aunque los métodos existentes han abordado la **heterogeneidad espacial** del crecimiento urbano desde diferentes enfoques (**vecindario, parches de tierra y partición de áreas**), todavía falta una comprensión profunda sobre **cómo varía la intensidad del crecimiento urbano a lo largo del tiempo en diferentes regiones**.
###### **Puntos clave del problema
1. **Las mismas condiciones espaciales pueden producir resultados diferentes**
    - Dos áreas pueden tener **las mismas características de vecindario** (es decir, el mismo número de celdas urbanas vecinas), pero su evolución urbana puede ser completamente diferente.
    - Esto sugiere que hay **otros factores en juego**, posiblemente **factores temporales**.

2. **Áreas con alta heterogeneidad espacial pueden evolucionar al mismo ritmo**
    - A pesar de que dos regiones pueden ser **muy distintas en su configuración espacial**, pueden **crecer a la misma velocidad**.
    - Esto indica que el **factor tiempo** influye en la evolución de la ciudad, además de la heterogeneidad espacial.

3. **El efecto del tiempo ha sido poco estudiado**
    - Algunos estudios han mencionado que el tiempo es clave para explicar la heterogeneidad espacial (**Song, Shi y Wang 2020; Shafizadeh-Moghadam y Helbich 2015**).
    - Sin embargo, los modelos de simulación urbana rara vez integran **cómo cambian las características urbanas a lo largo del tiempo** (**Li et al. 2021**).

###### **Cómo se ha abordado el tiempo en los modelos**
Los modelos existentes generalmente usan el crecimiento urbano pasado para predecir el crecimiento futuro:
- **Li y Yeh (2000)**: Propusieron establecer una cantidad fija de crecimiento urbano en cada período para controlar la expansión.
- **He et al. (2015)**: Diseñaron un modelo de autómatas celulares adaptativo combinado con inteligencia artificial para ajustar automáticamente las reglas de evolución en función del tiempo.
- **Shu et al. (2017)**: Usaron un **algoritmo genético** para ajustar dinámicamente los factores de influencia en cada período de tiempo.

###### **Conclusión**
Aunque algunos métodos han incorporado el **factor temporal**, todavía no se ha explorado completamente cómo la **intensidad del crecimiento urbano varía en el largo plazo**.  
Los estudios han trabajado con datos temporales, pero **no han analizado las tendencias a largo plazo** que podrían explicar mejor la evolución urbana.

###### **Área de estudio: Huizhou, China**

- **Ubicación**:
    - Coordenadas: 22°24′ −23°57′ N y 113°51′ −115°28′ E.
    - Huizhou está en la provincia de Guangdong, China.

- **Características**:
    - **Crecimiento urbano**: Desde la implementación de políticas de apertura y reforma en 1978, la ciudad ha experimentado un crecimiento rápido y continuo.
    - **Población**: La población residente de Huizhou ha superado los 6 millones.
    - **Orientación estratégica**: En 2018, la ciudad se enfocó en la planificación para convertirse en una ciudad de primera clase en China y en la planificación de la **Área de la Bahía de Guangdong, Hong Kong y Macao**.
    - **Urbanización**: Huizhou está experimentando una rápida urbanización.
- **Importancia**: Estudiar la evolución de la expansión urbana en Huizhou es crucial para comprender su desarrollo y planificar su futuro crecimiento.
    
###### **Materiales de datos utilizados**:

1. **Datos de tierra urbana**:
    - **Fuente**: Datos de cambios en los asentamientos humanos publicados en 2020, desarrollados por el equipo de Gong.
    - **Resolución**: 30 × 30 metros por píxel.
    - **Cobertura temporal**: Datos de 1986 a 2018, utilizados en periodos de 2001-2006 y 2006-2011 para simulación.

2. **Datos de pendiente**:
    - **Fuente**: Datos DEM proporcionados por Geospatial Data Cloud, Centro de Información de Redes de Computadoras, Academia China de Ciencias.
    - **Método de cálculo**: Usado el software **QGIS**.
    - **Origen de los datos DEM**: Publicados por **NASA** y el **Ministerio de Economía de Japón** en 2009, mediante procesamiento estereoscópico de imágenes ópticas ASTER (1.3 millones de escenas).
    - **Precisión**:
        - **Vertical**: 20 metros.
        - **Horizontal**: 30 metros.

3. **Datos geográficos básicos**:
    
    - **Fuente**: Servicios de mapas **Tianditu**, proporcionados por el **Servicio Nacional de Catálogo para Servicios Geográficos**.
    - **Contenido**: Datos sobre transporte, ríos, parques verdes, etc.
    - **Escala de los datos vectoriales**: 1:250000 (producción en 2017).
    - **Proceso de conversión**: Los datos vectoriales fueron convertidos en imágenes rasterizadas con una resolución de 30 × 30 metros por píxel para facilitar el procesamiento.

---

Este conjunto de datos permitió una simulación detallada de la expansión urbana en Huizhou, con énfasis en la interacción entre la tierra urbana, la pendiente y las características geográficas en la evolución de la ciudad.

###### **Estimación del área de crecimiento urbano con series de datos de alta resolución temporal

Primero, supongamos que X es la serie temporal de datos sobre la evolución del tamaño urbano a lo largo de los años:

X=⟨x<sub>1</sub>,x<sub>2</sub>,x<sub>3</sub>,...,x<sub>T</sub>⟩

Dado que el desarrollo de una ciudad es periódico, es razonable ajustar los datos de la serie temporal dividiéndolos en diferentes segmentos. Supongamos que la serie de datos X se divide en K segmentos, entonces X puede expresarse de la siguiente manera:

![[Formula.png]]

Donde:

- F<sub>i</sub> representa la función de ajuste para los datos del segmento i.
- α={α<sub>1</sub>,...,α<sub>k</sub>,...,α<sub>T</sub>} es el conjunto de puntos de división de la serie temporal X.
- e<sub>i</sub>(t) representa el ruido con media cero de la serie temporal.

**1. ¿Qué significa esta ecuación?**  
Esta ecuación representa cómo se modelan los datos de crecimiento urbano (X) en función del tiempo (t). En lugar de asumir que el crecimiento es uniforme a lo largo de todo el período (T), el tiempo se divide en segmentos (K segmentos).

Cada segmento tiene su propia función de ajuste F<sub>i</sub>(t,W<sub>i</sub>), que modela la tendencia del crecimiento en ese período específico. Además, se añade un término de ruido e<sub>i</sub>(t), que representa pequeñas fluctuaciones aleatorias que no siguen un patrón claro.

**2. ¿Qué significa cada término?**

- F<sub>i</sub>(t,W<sub>i</sub>): Es la función de ajuste para el segmento i. Puede ser, por ejemplo, una regresión lineal, exponencial o cualquier otro modelo matemático que describa la tendencia del crecimiento en ese período.

- W<sub>i</sub>: Son los parámetros de la función de ajuste F<sub>i</sub>, por ejemplo, coeficientes en una ecuación matemática.

- e<sub>i</sub>(t): Es el ruido aleatorio con media cero, lo que significa que en promedio no afecta la tendencia general. Representa variaciones impredecibles en los datos.
	- Con el ruido no se hace nada, solo se registra.
	- Que la media sea cero significa que las desviaciones positivas y negativas se cancelan en promedio. Si el ruido no tiene media cero, el modelo tiene un sesgo y debe mejorarse.

- α={α<sub>1</sub>,...,α<sub>k</sub>,...,α<sub>T</sub>}: Son los puntos en el tiempo donde se divide la serie temporal en segmentos.

###### **Ejemplo para entenderlo mejor**

Imagina que estamos analizando el crecimiento urbano de una ciudad desde el año 2000 hasta el 2020.

- **De 2000 a 2005**, el crecimiento fue rápido, así que ajustamos una función exponencial: 
F<sub>1</sub>(t,W<sub>1</sub>)=a<sub>1</sub>e<sup>b<sub>1</sub>t</sup>
- **De 2005 a 2015**, el crecimiento fue más estable, así que usamos una función lineal: 
F<sub>2</sub>(t,W<sub>2</sub>)=a<sub>2</sub>t+b<sub>2</sub>
- **De 2015 a 2020**, el crecimiento se desaceleró, y usamos otra función diferente.

En cada uno de estos períodos, hay pequeñas variaciones impredecibles que se representan con e<sub>i</sub>(t)

> **Conclusión**  
> En lugar de asumir que el crecimiento urbano sigue un solo patrón a lo largo de todo el período, el modelo divide el tiempo en segmentos y ajusta funciones específicas para cada período. Esto permite una mejor predicción del crecimiento urbano futuro.

>  ¿Para qué sirve esto?
> - Permite **predecir el crecimiento urbano** con mayor precisión al considerar los cambios de tendencia a lo largo del tiempo.
> - Evita errores en modelos tradicionales que asumen un crecimiento uniforme sin considerar los cambios en la dinámica urbana.
> - Es útil para la planificación urbana, modelando cómo ha crecido la ciudad y proyectando su expansión futura.


Por las características del crecimiento anual de la ciudad de estudio, los métodos anteriores de simulación y predicción con intervalos de 5 o 10 años muestran grandes inestabilidades y es probable que causen desviaciones en las predicciones del modelo. Es razonable simular el crecimiento urbano basándose en el método de ajuste por segmentos, y lo más importante es detectar automáticamente los puntos de cambio. 

```
Crecimiento urbano desigual. En general, la expansión urbana de Huizhou ha pasado por cinco etapas. Desde 1985 hasta 1990, la escala y la velocidad del crecimiento urbano mostraron una ligera tendencia a la baja. El primer período de expansión rápida comenzó entre 1991 y 1993, después del cual comenzó a declinar nuevamente. La tasa de expansión urbana disminuyó cada año hasta 1997. Desde 1998 hasta 2011, experimentó una fase de crecimiento rápido con aumentos año tras año, y a partir de 2012 entró en una fase de declive. 
```


![[Grafico de crecimiento 1985-2018.png]]


 ###### **los métodos de simulación y predicción con intervalos de 5 o 10 años:**
- Si divides 30 años de crecimiento en intervalos fijos (por ejemplo, bloques de 5 o 10 años), puedes perder información importante porque:
	- **Ignoras cambios de tendencia dentro de cada intervalo**: Por ejemplo, si en un bloque de 5 años hay 2 años de crecimiento rápido y 3 años de estancamiento, el modelo promediará estos comportamientos y no capturará la variabilidad real.
	- **No detectas puntos de cambio críticos**: Si un cambio importante (como un estancamiento o una aceleración) ocurre en el medio de un intervalo, el modelo no lo identificará.

- Ventaja del método de ajuste por segmentos:
	El método de ajuste por segmentos resuelve estos problemas al:
	- **Detectar automáticamente cambios en la tendencia**: Usando técnicas como **medias móviles** o **ventanas deslizantes**, el método identifica cuándo el crecimiento cambia de dirección (por ejemplo, de crecimiento a estancamiento).
	- **Dividir la serie temporal en segmentos significativos**: Cada segmento representa un período con un comportamiento homogéneo (por ejemplo, crecimiento constante, estancamiento, declive).


###### **Ejemplo práctico:**
Supongamos que tienes 30 años de datos de crecimiento urbano y aplicas el método de ajuste por segmentos. El proceso sería:

a) **Detectar cambios en la tendencia**:
- Usas una **ventana móvil** para analizar la serie temporal y detectar cuándo el crecimiento cambia significativamente.
- Por ejemplo:
  - Del **año 1 al 8**: Crecimiento constante.
  - Del **año 9 al 13**: Estancamiento.
  - Del **año 14 al 20**: Crecimiento acelerado.
  - Del **año 21 al 30**: Declive.

b) **Crear segmentos**:
- Segmento 1: Años 1-8 (crecimiento constante).
- Segmento 2: Años 9-13 (estancamiento).
- Segmento 3: Años 14-20 (crecimiento acelerado).
- Segmento 4: Años 21-30 (declive).

c) **Ajustar funciones a cada segmento**:
- Para cada segmento, ajustas una función que describa el comportamiento:
  - Segmento 1: Función lineal
  - Segmento 2: Función constante
  - Segmento 3: Función exponencial
  - Segmento 4: Función lineal con pendiente negativa

###### **4. ¿Por qué es mejor este método?**
- **Captura la variabilidad real**: Al dividir la serie en segmentos significativos, el modelo refleja mejor los cambios en el crecimiento.
- **Evita promedios engañosos**: No promedia comportamientos distintos en un solo bloque.
- **Identifica puntos de cambio críticos**: Detecta cuándo el crecimiento cambia de dirección, lo que es crucial para hacer predicciones precisas.

---

Relación no lineal entre el crecimiento urbano y los años:
   - Según la inspección visual de la Figura anterior, se determina que la relación entre el número de píxeles de crecimiento urbano y los años no es lineal.
   - ==Esto significa que el crecimiento no sigue una tendencia constante (por ejemplo, no aumenta o disminuye de manera uniforme año tras año).==

Análisis de ajuste (fitting):
   - Se probaron varios métodos de ajuste, como:
     - **Ajuste polinómico**
     - **Ajuste exponencial**
     - **Ajuste lineal**
   - Sin embargo, los valores de R<sup>2</sup> (coeficiente de determinación) fueron menores que 0.5, lo que indica que estos métodos no explican bien la variabilidad de los datos.

```
El análisis de ajuste se refiere al proceso de encontrar una función matemática (como una línea recta, una parábola o una curva exponencial) que se aproxime lo mejor posible a un conjunto de datos. En el contexto del crecimiento urbano, esto significa buscar una ecuación que describa cómo ha evolucionado la superficie urbana a lo largo del tiempo.  
```

> R<sup>2</sup> (Coeficiente de determinación):
> Es una medida estadística que indica **qué tan bien el modelo explica la variabilidad de los datos**. Su valor oscila entre **0 y 1**:  
> - R<sup>2</sup>= 1: El modelo explica el 100% de la variabilidad (ajuste perfecto).  
> - R<sup>2</sup>= 0: El modelo no explica nada de la variabilidad.  

Método de la media móvil:
   - ==Debido a la volatilidad interanual del crecimiento urbano==, se selecciona el **método de la media móvil** para predecir el crecimiento a lo largo del tiempo.
   - Para Huizhou, se prueba una **ventana móvil de 3 años**, que resulta adecuada para detectar puntos de cambio en los datos de series temporales.

Detección de puntos de cambio:
   - Primero, se calcula la pendiente en cada punto usando ese punto y los dos siguientes.
   - Luego, se determina si la pendiente cambia de positiva a negativa (o viceversa).
   - En el programa, si el signo de la pendiente cambia y aparecen dos signos iguales consecutivos, ese punto se considera un **punto de cambio**.

Segmentación y regresión:
   - Los puntos de cambio se utilizan para dividir la serie de datos en segmentos.
   - Cada segmento representa una tendencia de desarrollo diferente (ej: crecimiento rápido, estancamiento, declive).
   - Se realiza una **regresión segmentada** para ajustar una función a cada segmento y predecir el crecimiento urbano.

> La **regresión** es una técnica matemática para encontrar una **función** (como una línea recta o una curva) que se ajuste a un conjunto de datos. En el contexto de la regresión segmentada, la regresión se usa para crear la función que describe cada segmento.

Precisión del método:
   - Con datos de alta resolución temporal, este método de regresión segmentada es **más preciso** para estimar el crecimiento urbano, ya que captura mejor las fluctuaciones y cambios de tendencia.

###### **¿Por qué se usó el método de media móvil en Huizhou?**  
Dado que los modelos tradicionales R<sup>2</sup> < 0.5  no funcionaban, se optó por un enfoque más flexible:  
1. **Ventana móvil de 3 años**: Analiza grupos pequeños de datos (ej: años 2000-2002, 2001-2003, etc.).  
2. **Detecta cambios de tendencia**: Si la pendiente de crecimiento cambia de positiva a negativa (o viceversa), se marca un **punto de cambio**.  
3. **Divide la serie temporal en segmentos**: Cada segmento tiene su propia función de ajuste, lo que mejora la precisión.  

Con esto método de ajustar la función por periodo se resuelve lo de la heterogeneidad temporal. ahora como se resuelve lo de la heterogeneidad espacial

###### **Intensidad del crecimiento espacial urbano basada en el análisis de densidad kernel del crecimiento urbano**

El desequilibrio del crecimiento espacial urbano se manifiesta primero en la inconsistencia de la intensidad del crecimiento. Es decir, algunas regiones crecen rápidamente, mientras que otras crecen de manera gradual. Identificar la intensidad del crecimiento urbano en diferentes regiones ayuda a simular la forma urbana real. 

A diferencia del método de dividir la ciudad en círculos concéntricos o sectores, cuantificamos la intensidad del crecimiento espacial urbano según la estimación de densidad kernel del crecimiento urbano. La estimación de densidad kernel es un método para el análisis y detección de áreas calientes. Se calcula en función del número de puntos de eventos en una ubicación, donde un mayor número de puntos agrupados resulta en valores más altos. Una superficie de densidad suave de eventos puntuales para toda la ciudad puede generarse mediante la estimación de densidad. Para el crecimiento urbano, el estado de una celda que cambia de no urbana a urbana puede considerarse como un evento puntual. 

Tomando Huizhou como ejemplo, los eventos puntuales de cambio urbano pueden generarse convirtiendo los píxeles raster en puntos vectoriales. La Figura 3 muestra los puntos de eventos de crecimiento urbano de 2001 a 2006.

![[Mapa eventos de crecimiento.png]]
Según los experimentos realizados por Liao et al. en 2016, el mejor rendimiento del modelo se obtiene cuando el vecindario es de 1.36 km. Para simplificar el cálculo, en nuestro estudio establecimos el valor de r en 1,000 m. La Figura 4 muestra la intensidad del crecimiento urbano de 2001 a 2006, de la cual se puede ver claramente que el crecimiento urbano es obviamente no estacionario. 

El crecimiento urbano en la mayoría de los lugares no es fuerte, con solo unas pocas regiones siendo áreas calientes de expansión urbana de 2001 a 2006. La intensidad del crecimiento urbano refleja bien la tendencia de evolución urbana en el espacio 2D. ==Si la ciudad continúa con esta tendencia de crecimiento, la intensidad del crecimiento urbano será una buena variable auxiliar para el modelo de autómatas celulares (CA) urbano.==

![[Kernel density eventos de crecimiento.png]]

---

###### Explicación:

1. **Intensidad del crecimiento urbano**:
   - El crecimiento urbano no es uniforme; algunas áreas crecen más rápido que otras.
   - Para entender este crecimiento, se utiliza un método llamado **estimación de densidad kernel**, que identifica "áreas calientes" de crecimiento.

2. **Estimación de densidad kernel**:
   - Es una técnica que calcula la densidad de eventos (en este caso, cambios de no urbano a urbano) en un área.
   - Si hay muchos eventos cercanos, la densidad es alta; si hay pocos, la densidad es baja.

3. **Aplicación en Huizhou**:
   - Se convirtieron píxeles de imágenes raster (mapas) en puntos vectoriales para representar los cambios urbanos.
   - Se utilizó un radio de búsqueda de 1,000 metros para calcular la densidad kernel.

4. **Resultados**:
   - El crecimiento urbano no es uniforme; solo unas pocas áreas son "calientes" (de rápido crecimiento).
   - Esta información es útil para modelar el crecimiento futuro de la ciudad usando autómatas celulares (CA).

5. **Importancia**:
   - La intensidad del crecimiento urbano ayuda a entender cómo evoluciona la ciudad en el espacio y puede usarse para mejorar los modelos de simulación urbana.

---
###### **3. 4 Allocation probablility of new urban cells form neighbouhood**

El tamaño del crecimiento urbano puede estimarse utilizando un método de regresión por tramos. Sin embargo, este tamaño urbano predicho representa el crecimiento total de una ciudad. Además del aumento en el número total de píxeles, la precisión en la asignación espacial de nuevos píxeles urbanos es una métrica importante para medir los resultados de la simulación de la expansión urbana. ==Muchos factores, especialmente el número de píxeles urbanos en el vecindario, se han utilizado para estimar la probabilidad de que una celda cambie a estado urbano. Anteriormente, se ha utilizado un vecindario de 3 × 3 o de 5 × 5 para calcular el efecto del vecindario en la generación de nuevas celdas urbanas== (Chen et al. 2014; Ku 2016; Mustafa et al. 2018). La probabilidad derivada del efecto del vecindario siempre se ha calculado mediante una ecuación, como la Ecuación (3):
![[Probabilidad_vecindario_1.png]]
donde **P** representa la probabilidad de transición de la celda central de suelo no desarrollado a suelo desarrollado; **S<sub>i</sub>** es el valor del estado de la _i_-ésima celda dentro del rango del vecindario, y dicho valor de estado suele ser **1** para representar una celda desarrollada y **0** para una no desarrollada; y **m** es el radio del vecindario. Aunque existen algunas variaciones para calcular el efecto del vecindario, el método de cálculo es prácticamente el mismo.

La Figura 5 muestra tres distribuciones diferentes de celdas urbanas en un vecindario. De acuerdo con la Ecuación (2) para el cálculo de la probabilidad a partir del vecindario, la Figura 5(a) presenta la **probabilidad mínima de evolución** para la celda gris central, ya que solo hay una celda urbana en el área del vecindario. En cambio, la celda central en la Figura 5(c) tendrá la **probabilidad más alta de evolucionar** a una celda urbana; mientras que la Figura 5(b) tendrá una **probabilidad intermedia**, al tener la mitad del número de celdas urbanas en el vecindario.

Este método de cálculo de probabilidad, utilizado por muchos estudios previos, **parece razonable**, pero ignora el patrón habitual de la distribución espacial urbana. Tomando como ejemplo la Figura 5(c), la distribución espacial de los píxeles urbanos es muy densa, y las celdas no evolucionadas podrían estar siendo usadas como **espacios para actividades urbanas**, como un parque o un área verde. En este caso, la celda gris central de la Figura 5(c) **nunca evolucionaría** a una celda urbana.
En otras palabras, **una alta densidad de píxeles urbanos en el vecindario no implica necesariamente que el píxel central tenga una mayor probabilidad de evolucionar**.
Para descubrir la relación entre la **densidad de celdas urbanas** y la **probabilidad de que celdas no urbanas cambien a urbanas** dentro de un vecindario, se utilizó un vecindario con dimensiones de **5 × 5**. Las celdas urbanas en **Huizhou** desde **2007 hasta 2012** se usaron, respectivamente, para contar las **densidades urbanas vecinales** y el **número de nuevas celdas urbanas**.
Para simplificar el cálculo, se utilizó el **número de celdas urbanas** como medida de la **densidad** en el vecindario, ya que todos los datos tenían el mismo tamaño de vecindario. La probabilidad para una determinada densidad se puede calcular de la siguiente forma:

$$
P_{den} = \frac{\sum_{n=0}^{N_{den}} U_{new}}{N_{den}}
$$

P<sub>den</sub>: Es la **probabilidad promedio** de que emerjan nuevas celdas urbanas en barrios con una densidad urbana inicial específica (**den**).

N<sub>den</sub>: Es el número total de **vecindarios** que tenían exactamente esa densidad urbana (**den**) al inicio del período de análisis.

U<sub>new</sub>: Es el **número de celdas urbanas nuevas** que emergieron en un barrio específico (**el barrio n**) durante el periodo analizado


Donde **Pden** representa la **probabilidad de aparición de nuevas celdas urbanas** para una densidad determinada **den**; **Nden** es el **número total de vecindarios** que tenían exactamente esa cantidad de celdas urbanas (**den**) al inicio del período de crecimiento, por ejemplo, en **2007** para la fase 2007–2012; y **Unew** representa el **número de nuevas celdas urbanas** que surgieron en el _n-ésimo vecindario.

Esta ecuación también puede interpretarse como el **número promedio de nuevas celdas urbanas** que emergen en vecindarios con una determinada densidad.

La **Figura 6** muestra la relación entre la **densidad en un vecindario** y la **probabilidad calculada con la Ecuación 4**, tanto para vecindarios de **5 × 5** como de **10 × 10**. Se puede observar que un mayor número de celdas urbanas, lo que indica una mayor densidad urbana en el vecindario, **no garantiza** una mayor probabilidad de aparición de nuevas celdas urbanas.

Por ejemplo, si el número de celdas urbanas en un vecindario de 5 × 5 está en el rango de **5 a 10**, se pueden obtener **probabilidades comparativamente más altas**. De forma similar, en vecindarios de 10 × 10, las probabilidades más altas se observan cuando el número de celdas urbanas está entre **20 y 40**.

Sin embargo, **ambos tamaños de vecindario presentan el mismo patrón de tendencia**. Para cada tamaño de vecindario, se pueden ajustar ecuaciones correspondientes, y con base en dichas ecuaciones ajustadas, se puede calcular fácilmente la **probabilidad de evolución** de una celda desde un estado no urbano a uno urbano, utilizando simplemente el número de celdas urbanas en el área del vecindario.

1. **Crecimiento urbano y asignación espacial**:
   - El crecimiento urbano no solo se trata de cuánto crece una ciudad, sino también de **dónde** crece.
   - La **asignación espacial** de nuevas celdas urbanas es crucial para simular la expansión urbana de manera realista.

2. **Efecto del vecindario**:
   - La probabilidad de que una celda no urbana se convierta en urbana depende de cuántas celdas urbanas hay en su vecindario.
   - Se utilizan vecindarios de 3 × 3 o 5 × 5 para calcular esta probabilidad.

3. **Cálculo de probabilidad**:
   - La probabilidad se calcula con una ecuación que considera el número de celdas urbanas en el vecindario.
   - Por ejemplo, si hay muchas celdas urbanas cerca, la probabilidad de que una celda no urbana se convierta en urbana es mayor.

4. **Limitaciones del método tradicional**:
   - El método tradicional no considera que áreas muy densas (como parques) pueden no convertirse en urbanas, incluso si están rodeadas de celdas urbanas.

5. **Nuevo enfoque**:
   - Se utiliza un vecindario de 5 × 5 para analizar la relación entre la densidad urbana y la probabilidad de cambio (con datos reales).
   - Se descubre que la probabilidad más alta de cambio ocurre cuando el número de celdas urbanas en el vecindario está en un rango específico (5-10 para 5 × 5 y 20-40 para 10 × 10).

   
![[Grafico vecinos optimos.png]]
1. **Aplicación**:
   - Con las ecuaciones ajustadas, se puede predecir la probabilidad de que una celda no urbana se convierta en urbana basándose en la densidad del vecindario.

---

En resumen:
El efecto del vecindario es clave para predecir dónde ocurrirá el crecimiento urbano. Sin embargo, es importante considerar que no todas las áreas densas se convertirán en urbanas, especialmente si son áreas verdes o parques. Este enfoque mejora la precisión de las simulaciones de expansión urbana.

---

**Reglas de transición con el apoyo de series de datos de alta resolución temporal**

1. **Reglas de transición en el modelo CA**:
   - El modelo CA urbano tiene dos partes principales:
     - **Condición de terminación**: La simulación se detiene cuando se alcanza un número predeterminado de celdas urbanas.
     - **Probabilidad de evolución**: Determina la probabilidad de que una celda no urbana se convierta en urbana.

2. **Factores que influyen en la probabilidad de evolución**:
   - Además de factores tradicionales (como la proximidad a carreteras o zonas industriales), se incluyen dos nuevos factores:
     - **Intensidad del crecimiento espacial urbano**: Mide qué tan fuerte es el crecimiento en una zona.
     - **Probabilidad de asignación espacial**: Basada en los efectos del vecindario (cuántas celdas urbanas hay cerca).

3. **Uso de aprendizaje automático**:
   - Se utiliza un modelo de aprendizaje automático para predecir si una celda se convertirá en urbana.
   - Las características de la celda (como su ubicación y entorno) son las **entradas**, y el estado futuro (urbano o no urbano) es la **salida**.

4. **Incertidumbre en el crecimiento urbano**:
   - El crecimiento urbano es impredecible debido a factores como políticas gubernamentales o cambios económicos.
   - La variable \( R \) introduce esta incertidumbre en el modelo, simulando perturbaciones aleatorias.

5. **Celdas restringidas**:
   - Algunas áreas, como parques o tierras agrícolas protegidas, no pueden convertirse en urbanas.
   - Estas celdas se marcan como **restringidas** y no cambian durante la simulación.

6. **Objetivo del modelo CA**:
   - El modelo evoluciona las celdas no urbanas hasta que se alcanza el número esperado de celdas urbanas, siguiendo las reglas de transición.

---

En resumen:
El modelo CA urbano utiliza reglas de transición basadas en aprendizaje automático para simular cómo crece una ciudad. Considera factores como la densidad del vecindario, la intensidad del crecimiento y la incertidumbre, y excluye áreas protegidas. El objetivo es predecir de manera realista la expansión urbana.

---
**Implementación y evaluación del modelo**

1. **Selección de características**:
   - Las características utilizadas en el modelo CA se seleccionan en función de los datos disponibles.
   - En este estudio, se utilizaron **12 características**, que incluyen:
     - Efectos del vecindario (ej: número de celdas urbanas en un vecindario de 5×5).
     - Condiciones naturales (ej: pendiente).
     - Proximidad espacial (ej: distancia a carreteras, cuerpos de agua, parques).
     - Estimación de densidad kernel (ej: densidad de crecimiento urbano).

2. **Implementación del modelo**:
   - El modelo se implementó en **QGIS** (para procesamiento de datos geográficos) y **Python** (para el análisis y la predicción).
   - Se utilizaron bibliotecas como **scikit-learn** para aplicar algoritmos de aprendizaje automático, como SVM, redes neuronales y regresión logística.

3. **Evaluación del modelo**:
   - El modelo se evaluó como un problema de **clasificación binaria** (celdas urbanas vs. no urbanas).
   - Se utilizó una **matriz de confusión** para medir el rendimiento del modelo, calculando métricas como:
     - **Precisión**: Proporción de predicciones correctas.
     - **Sensibilidad**: Proporción de celdas urbanas correctamente identificadas.
     - **Especificidad**: Proporción de celdas no urbanas correctamente identificadas.
     - **Puntaje F1**: Combinación de precisión y sensibilidad, útil para evaluar el equilibrio del modelo.

---

En resumen:
El modelo CA se implementó utilizando datos geográficos y técnicas de aprendizaje automático, y se evaluó mediante métricas de clasificación binaria. Esto permite predecir de manera precisa cómo crecerá una ciudad y evaluar el rendimiento del modelo.

---
Resultados

1. **Pronóstico del área de crecimiento urbano**:
   - Se utilizó el método de regresión segmentada para estimar el crecimiento urbano entre 1985 y 2018.
   - Se identificaron puntos de cambio automáticamente y se ajustaron líneas de regresión para cada segmento.
   - El período de 2001 a 2011 mostró un crecimiento constante, lo que lo hace adecuado para la simulación.

2. **Datos de entrenamiento y parámetros**:
   - Se dividió el período en dos etapas: 2001-2006 (entrenamiento) y 2006-2011 (validación).
   - Se utilizó un método de muestreo equilibrado para entrenar los modelos de aprendizaje automático (SVM, LR, ANN).
   - El algoritmo ANN (Redes Neuronales Artificiales) mostró la mayor precisión y se integró en el modelo CA.

3. **Resultados de la simulación urbana**:
   - Las simulaciones para 2001-2006 y 2006-2011 mostraron una alta concordancia con los datos reales.
   - El modelo se evaluó utilizando el puntaje F1, que fue de 0.42 para las nuevas celdas urbanas, lo cual es aceptable.
   - La precisión general del modelo fue muy alta (al menos 0.93), ya que la mayoría de las celdas no cambiaron de estado.

---
###### Dudas

**1. ¿Por qué se utiliza el período 2001-2011?**
- **Antes de 2001**, el crecimiento urbano no era constante. Como mencionas, el crecimiento subía y bajaba, lo que significa que no seguía una tendencia clara. Esto dificulta la aplicación de modelos de regresión, ya que estos funcionan mejor con tendencias consistentes.
- **De 2001 a 2011**, el crecimiento urbano fue más estable y constante, lo que lo hace ideal para aplicar el método de **regresión segmentada** y predecir el crecimiento futuro.

---

 **2. ¿Qué es el método de muestreo equilibrado?**
[[Notas Metodologia Modelos#3. Diseño de Muestreo, desbalance y CV (idéntico para ambos periodos).]]

El **muestreo equilibrado** es una técnica utilizada en aprendizaje automático para asegurarse de que el conjunto de datos de entrenamiento tenga una proporción equilibrada de clases (en este caso, celdas urbanas y no urbanas). Aquí te explico cómo funciona:
- **Problema**: En los datos de crecimiento urbano, la mayoría de las celdas son **no urbanas**, y solo unas pocas se convierten en urbanas. Esto crea un desequilibrio en los datos.
- **Solución**: El muestreo equilibrado selecciona una cantidad igual de celdas urbanas y no urbanas para entrenar el modelo. Por ejemplo, si hay 10,000 celdas no urbanas y 1,000 celdas urbanas, el método selecciona 1,000 celdas no urbanas y 1,000 celdas urbanas.
- **Objetivo**: Evitar que el modelo se sesgue hacia la clase mayoritaria (no urbana) y mejorar la precisión en la predicción de celdas urbanas.

---

**3. ==¿Qué son SVM, LR y ANN?**==
==Estos son algoritmos de aprendizaje automático utilizados para predecir si una celda se convertirá en urbana o no:==
- ==**SVM (Máquinas de Vectores de Soporte)**: Un algoritmo que clasifica datos encontrando la mejor línea (o hiperplano) que separa las clases (urbanas vs. no urbanas).==
- ==**LR (Regresión Logística)**: Un algoritmo que predice la probabilidad de que una celda sea urbana usando una función logística.==
- ==**ANN (Redes Neuronales Artificiales)**: Un modelo inspirado en el cerebro humano que aprende patrones complejos en los datos. Fue el que mostró la mayor precisión en este estudio.==

---

**4. ¿El puntaje F1 de 0.42 es bajo?**
El **puntaje F1** es una métrica que combina **precisión** y **sensibilidad** (recall). Su rango es de **0 a 1**, donde:
- **1**: Predicciones perfectas.
- **0**: Predicciones completamente incorrectas.
- **0.42**: Es un valor moderado. No es excelente, pero es aceptable en problemas complejos como la predicción de crecimiento urbano, donde hay muchos factores impredecibles (políticas, economía, etc.).
- **Nota**: El puntaje F1 se calcula solo para las **nuevas celdas urbanas**, que son las más difíciles de predecir. La precisión general del modelo fue mucho más alta (0.93), ya que la mayoría de las celdas no cambiaron de estado.

---

**5. Explicación del gráfico (Figura 7)**

a) **Puntos azules**:
   - Representan el **número real de celdas urbanas nuevas** añadidas cada año desde 1985 hasta 2018.
   - Por ejemplo, en 2005, el gráfico muestra cuántas celdas se convirtieron en urbanas ese año.

b) **Líneas sólidas**:
   - Son las **líneas de ajuste** generadas por el método de **regresión segmentada**.
   - Cada línea representa una función matemática (por ejemplo, una línea recta) que se ajusta a los datos en un segmento específico.
   - Estas líneas muestran la **tendencia de crecimiento** predicha por el modelo para cada período.

c) **Puntos rojos**:
   - Son los **puntos de cambio** detectados automáticamente por el programa.
   - Indican cuándo la tendencia de crecimiento cambia (por ejemplo, de crecimiento lento a rápido).
   - Por ejemplo, si en 2005 hay un punto rojo, significa que la tendencia de crecimiento cambió ese año.

---

**6. ¿Cómo interpretar el gráfico?**
- **Antes de 2001**: Los puntos azules suben y bajan, lo que indica un crecimiento irregular. Las líneas de ajuste no funcionan bien aquí.
- **De 2001 a 2011**: Los puntos azules muestran un crecimiento constante, y las líneas de ajuste (líneas sólidas) siguen bien esta tendencia.
- **Puntos rojos**: Marcan los años en los que la tendencia de crecimiento cambió (por ejemplo, de crecimiento lento a rápido).

---

**2. Figura 9: Probabilidad de aparición de nuevas celdas urbanas en un vecindario de (5 x 5)**

Esta figura muestra cómo la **probabilidad de que una celda no urbana se convierta en urbana** varía según el número de celdas urbanas en su vecindario de ( 5 x 5).

-  **Líneas**:
   - Cada línea representa un período de tiempo diferente:
     - **2001-2006**: Probabilidad de cambio durante este período.
     - **2001-2008**: Probabilidad de cambio durante este período.
     - **2001-2011**: Probabilidad de cambio durante este período.

-  **Interpretación**:
	- La probabilidad de cambio **aumenta** a medida que hay más celdas urbanas en el vecindario, pero solo hasta un cierto punto.
	  - Por ejemplo, en un vecindario de (5 x 5), la probabilidad es más alta cuando hay entre **5 y 10 celdas urbanas**.
	  - Si hay **más de 10 celdas urbanas**, la probabilidad disminuye, porque es probable que las celdas no urbanas restantes sean **espacios verdes o áreas protegidas**.
	- Este patrón es consistente en todos los períodos (2001-2006, 2001-2008, 2001-2011).

---

**1. ¿Por qué se excluyen las celdas urbanas originales?**

Las **celdas urbanas originales** (las que ya eran urbanas al inicio del período de simulación) se excluyen de la evaluación del modelo por las siguientes razones:

a) **Objetivo del modelo**:
   - El modelo CA está diseñado para predecir **nuevo crecimiento urbano**, es decir, cómo las celdas no urbanas se convierten en urbanas.
   - Las celdas que ya eran urbanas no cambian de estado, por lo que no son relevantes para evaluar la capacidad del modelo para predecir cambios.

b) **Enfoque en la dinámica de crecimiento**:
   - Al excluir las celdas urbanas originales, el modelo se evalúa únicamente en su capacidad para predecir **nuevas urbanizaciones**, que es el aspecto más desafiante y útil para la planificación urbana.

c) **Evitar sesgos**:
   - Si se incluyeran las celdas urbanas originales, la precisión general del modelo sería artificialmente alta, ya que la mayoría de las celdas no cambian de estado (son no urbanas). Esto ocultaría el rendimiento real del modelo en la predicción de nuevas urbanizaciones.

---

**2. ¿Qué rangos de precisión para las celdas urbanas serían aceptables?**

La **precisión** para las celdas urbanas depende del contexto y la complejidad del problema. Aquí te doy una guía general:
a) **Precisión aceptable**:
   - **0.5 a 0.7**: Un valor en este rango se considera **moderadamente bueno** para problemas complejos como la predicción de crecimiento urbano.
   - En el estudio, la precisión para las celdas urbanas fue de **0.34 a 0.47**, lo cual es **bajo**, pero no inesperado dada la complejidad del problema.
b) **Precisión excelente**:
   - **0.7 a 0.9**: Un valor en este rango indicaría que el modelo es **muy preciso** en la predicción de nuevas celdas urbanas.
   - Sin embargo, alcanzar este nivel de precisión es difícil en problemas de crecimiento urbano debido a la influencia de factores impredecibles (políticas, economía, etc.).
c) **Precisión inaceptable**:
   - **Menos de 0.3**: Un valor en este rango sugiere que el modelo tiene **serias limitaciones** y no es confiable para la predicción de nuevas urbanizaciones.

---
**5. ¿Cómo mejorar el modelo?**

Si el modelo tiene un rendimiento bajo en la predicción de nuevas celdas urbanas, se pueden tomar las siguientes medidas:
a) **Mejorar los datos**:
   - Incluir más variables (ej: políticas urbanas, datos socioeconómicos).
   - Usar datos de mayor resolución temporal y espacial.
b) **Ajustar los algoritmos**:
   - Probar otros algoritmos de aprendizaje automático (ej: Random Forest, Gradient Boosting).
   - Ajustar los hiperparámetros del modelo para mejorar su rendimiento.
 c) **Incluir más contexto**:
   - Considerar restricciones físicas (ej: áreas protegidas, ríos) y políticas (ej: zonificación).

---

###### Discusión  
**5.1 Estimación del área de crecimiento urbano**  
En estudios previos, algunos investigadores han realizado predicciones de escenarios calculando el área de crecimiento según diferentes hipótesis (Bharath et al., 2018; Siddiqui et al., 2018; Liang et al., 2018). Sin embargo, este método artificial carece de una base estadística suficiente, por lo que su valor de orientación para la planificación urbana es limitado. En este artículo, proponemos un método para estimar el área de crecimiento urbano utilizando una serie de datos de alta resolución temporal. Este método considera el desequilibrio del desarrollo urbano a lo largo del tiempo y diseña un programa automático para identificar los puntos de cambio en la tendencia del desarrollo urbano, proporcionando así una herramienta de análisis para la simulación y predicción del espacio urbano. Tomando como ejemplo los períodos de 2001 a 2006 y de 2006 a 2011, el número de celdas urbanas nuevas generadas en el primer período es de 43.160, mientras que en el segundo período es de 68.094, siendo el primero significativamente menor que el segundo. Si solo seguimos la misma tendencia para la simulación de autómatas celulares (CA) urbanos, habrá una gran desviación respecto a la situación real. En consecuencia, la predicción mediante una fórmula de regresión segmentada muestra una clara coherencia con el crecimiento real.  

**5.2 Distribución de nuevas celdas urbanas afectadas por el vecindario**  
El vecindario, utilizado en casi todos los modelos de CA, tiene un impacto significativo en la evolución de la celda central. Sin embargo, esto no significa que una mayor cantidad de celdas urbanas en el vecindario (es decir, una mayor densidad de celdas urbanas) genere una mayor probabilidad de que la celda central evolucione a una celda urbana. La Figura 9 muestra la proporción de celdas centrales que se convierten en urbanas según diferentes densidades de celdas urbanas en el vecindario. En la Figura 9, demostramos tres condiciones bajo diferentes cantidades de píxeles de crecimiento urbano: aproximadamente 10.000, 40.000 y 10.000. Estos números corresponden a tres períodos: 2001-2003, 2001-2006 y 2001-2011. Se observa que la probabilidad de aparición de nuevas celdas urbanas sigue una **distribución normal**. Tomando un vecindario de 5 × 5 como ejemplo, cuando el número de celdas urbanas existentes en el vecindario está entre 8 y 10, la celda central tiene la **tasa de conversión más alta**. Por el contrario, cuando hay demasiadas o demasiado pocas celdas urbanas en el vecindario, la probabilidad de aparición de nuevas celdas urbanas es sustancialmente menor. En comparación con el cálculo tradicional del efecto de vecindario, este método evita eficazmente la generación de celdas demasiado densas durante el proceso de iteración evolutiva.  

---  
**Notas clave:**  
1. **Regresión segmentada**: Permite modelar tendencias cambiantes en el tiempo, mejorando la precisión de las predicciones.  
2. **Efecto de vecindario**: La densidad óptima de celdas urbanas en el vecindario maximiza la conversión, pero densidades extremas la reducen.  
3. **Distribución normal**: Refleja que la probabilidad de conversión no es lineal, sino que tiene un punto óptimo intermedio.  

Este enfoque ofrece una herramienta robusta para la planificación urbana, integrando dinámicas temporales y espaciales de manera más realista.

**5.3 Decisión del umbral y número de iteraciones**  

De acuerdo con las características relacionadas con la celda central de la cuadrícula, se calcula una **probabilidad de transición**. El umbral afecta directamente si la celda central evoluciona a un estado urbano y también influye en el número de iteraciones. Para evitar que el umbral establecido sea demasiado alto o demasiado bajo, primero simulamos una vez el proceso y calculamos el **valor promedio** y la **desviación estándar** de las probabilidades de evolución de todas las celdas. Luego, definimos un umbral adecuado según el número esperado de celdas a evolucionar.  

La Figura 10 muestra la diferencia entre los resultados de simulación con una sola iteración y con siete iteraciones. En la Figura 10(a), el umbral se establece en **0.0031**, un valor muy bajo, lo que permite que suficientes celdas no urbanas se conviertan en urbanas en una sola iteración. Sin embargo, la distribución de las nuevas celdas urbanas está altamente concentrada. En contraste, en la Figura 10(b), el umbral es **0.038**, y se requieren siete iteraciones para alcanzar el número esperado de celdas urbanas evolucionadas. Se observa que, a mayor número de iteraciones, más dispersa será la distribución de las celdas urbanas. Según la distribución espacial urbana real en 2011, el resultado de una sola iteración coincide mejor con la realidad, por lo que este estudio utiliza únicamente una iteración.  

**5.4 Predicción de escenarios futuros**  
Como se mencionó, la tasa de crecimiento de la expansión urbana de Huizhou varió en distintos períodos: un rápido aumento entre 2002 y 2006 y un declive entre 2013 y 2018. Según la tendencia histórica, inferimos que el desarrollo futuro podría seguir múltiples trayectorias. Siguiendo a Chen et al. (2020), que proyectan una expansión acelerada de suelo urbano global hasta la década de 2040, planteamos tres escenarios para los 10 años posteriores a 2018:  

4. **Desarrollo estable**: Crecimiento constante sin cambios significativos.  
5. **Declive lento**: Reducción gradual de la tasa de expansión.  
6. **Crecimiento acelerado**: Expansión urbana rápida.  

Bajo estos supuestos, el número total de celdas urbanas proyectadas sería de **21.085**, **38.060** y **104.715**, respectivamente. La Figura 11 ilustra las tendencias de crecimiento para cada escenario (baja, moderada y alta velocidad).  

Utilizando el método de **intensidad de crecimiento espacial basado en análisis de densidad kernel** (Sección 3.3), calculamos la distribución de intensidad (Figura 12). Partiendo de la distribución de celdas urbanas en 2018, proyectamos la expansión bajo los tres escenarios. Las Figuras 13 y 14 muestran la expansión predicha para 2028 con tasas de crecimiento en declive y estable, respectivamente. ==En ambos casos, la expansión se concentra alrededor del área urbana principal. Para el tercer escenario (Figura 15), la aceleración genera un aumento drástico de celdas urbanas, extendiéndose incluso a suburbios periféricos==.  

La predicción de escenarios combina dos elementos clave:  
7. **Estimación de áreas de crecimiento** mediante series temporales de alta resolución.  
8. **Mapas de intensidad** basados en análisis de densidad kernel.  

Los resultados demuestran coherencia entre las simulaciones y las tendencias de intensidad espacial, lo que sugiere que estos mapas influyen significativamente en la precisión de las predicciones. Este enfoque integrado ofrece una herramienta robusta para la planificación urbana estratégica, adaptándose a dinámicas temporales y espaciales complejas.

---  
**Notas clave:**  
- **Umbral de transición**: Balancea precisión y eficiencia en simulaciones.  
- **Escenarios futuros**: Desde estabilidad hasta expansión acelerada, reflejando incertidumbre en tendencias urbanas.  
- **Densidad kernel**: Herramienta clave para mapear patrones de crecimiento realistas.

###### Conclusión  
Modelar la expansión urbana es un método importante para la planificación urbana y el desarrollo sostenible. Diferentes características pueden tener un gran impacto en los resultados de la simulación. Para extraer características más efectivas, este estudio analizó los aspectos clave para mejorar el modelo de autómatas celulares (CA) desde tres perspectivas:  

1. **Estimación del área de crecimiento urbano**:  
   Se propuso estimar las áreas de crecimiento urbano utilizando series de datos de alta resolución temporal. El método de **regresión segmentada** se empleó para predecir la cantidad total de crecimiento urbano.  

2. **Intensidad del crecimiento urbano**:  
   Se cuantificó la intensidad del crecimiento urbano en diferentes regiones utilizando un **método de estimación de densidad kernel**. La intensidad del crecimiento diseñada en este estudio ayudó a simular la forma urbana real.  

3. **Probabilidad de asignación de nuevas celdas urbanas**:  
   Se analizó la probabilidad de asignación de nuevas celdas urbanas basada en los **efectos del vecindario**.  

Al incorporar estas características, se implementó un nuevo modelo de CA que demostró ser efectivo en la simulación y predicción de la expansión urbana en Huizhou, China. Los resultados experimentales muestran que:  

- El área de crecimiento urbano predicha mediante el método de regresión segmentada es la más consistente con el crecimiento real.  
- La **intensidad del crecimiento espacial urbano** mejora efectivamente la distribución espacial del crecimiento y aumenta la precisión del modelo de CA.  
- Respecto a los efectos del vecindario, se observó que una mayor cantidad de celdas urbanas en el vecindario no necesariamente implica una mayor probabilidad de que la celda central evolucione. Por el contrario, demasiadas o demasiado pocas celdas urbanas en el vecindario reducen la probabilidad de que surjan nuevas celdas urbanas. En un vecindario de 5 × 5, la **tasa de conversión más alta** se alcanzó cuando el número de celdas urbanas en el vecindario estuvo entre 8 y 10.  

Este enfoque integral proporciona una herramienta robusta para la planificación urbana, permitiendo simulaciones más precisas y realistas de la expansión urbana.

---  
**Notas clave:**  
- **Regresión segmentada**: Predice con precisión el crecimiento urbano total.  
- **Densidad kernel**: Mejora la distribución espacial del crecimiento.  
- **Efectos del vecindario**: La densidad óptima maximiza la conversión, pero extremos la reducen.  

Este estudio subraya la importancia de integrar múltiples dimensiones (temporal, espacial y de vecindario) para modelar dinámicas urbanas complejas.

Modelado de expansión urbana mediante autómatas celulares y redes neuronales artificiales° https://search.app/7Q4pu15kth3UMo7g7