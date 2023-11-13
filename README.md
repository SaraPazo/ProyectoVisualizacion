# Proyecto Visualización - EVENTOS MUSICALES 

![Imagen](https://github.com/SaraPazo/ProyectoVisualizacion/blob/main/Imagen/bruce.png)

### INDICE
1. Objetivo
2. Fuentes de extracción
3. Contenido
4. Limpieza de datos
5. Creación del Tableau



### 1. Objetivo
El objetivo de este proyecto es hacer una visualización aprovechando el conjunto de datos generado en el Proyecto ETL: https://github.com/SaraPazo/ProyectoETL, utilizando Tableau.

El objetivo es producir paneles interactivos que contengan información relacionada con el turismo o viajes que se realizan a la cuidad de Madrid, y los eventos (conciertos y festivales en este caso) que se llevan a cabo. 

Se observan las tendencias en cuanto a los estilos musicales y la temporalidad de los eventos. Además, observar si tienen algún tipo de relación las visitas a la ciudad con que haya conciertos en esas fechas.



### 2. Fuentes de extracción

Capturamos del trabajo de ETL previo varios conjuntos de datos. 

a. En base al objetivo de estudio, continuo con la página web de entradas.com, web de venta de entradas a eventos, conciertos, musicales, exposiciones, y otros. 

Teníamos una extracción de datos previa en el trabajo de ETL, sin embargo, llevo a cabo una nueva selección a través de scraping utilizando el método de *selenium*, con la que creo un nuevo dataframe (events_estilo).

URL: https://www.entradas.com/citymadrid-370conciertos-y-festivales-85/

- Y de aquí voy seleccionando cada uno de los estilos de música con sus eventos correspondientes. 


b. Tenía previamente información sobre la ocupación turística en la Comunidad de Madrid, a través de la página del INE, los la importación de datos y su limpieza para elaborar un archivo .csv. 

- Esta nos aportará información sobre los viajeros y pernoctantes, según fecha, y según sean residentes en España o residentes en el Extranjero.
    URL: https://www.ine.es/jaxiT3/Datos.htm?t=2074

c. Nuevamente, busco ampliar mis datos en cuanto al turismo en la Comunidad de Madrid. Un nuevo archivo .csv es creado a través de la búsqueda y limpieza de datos recogidos del INE. Este nos mostrará el género, edad, año y trimestre en el que es realizado el viaje. De estos datos sacaremos por tanto información de la época del año en la que hay más turistas, como dato principal. 

- Un nuevo archivo .csv es creado a través de la búsqueda y limpieza de datos recogidos del INE: 
    
    URL:https://www.ine.es/jaxiT3/Tabla.htm?t=12441&L=0 


### 3. Contenido

- **Carpeta Data**: esta carpeta incluye datos sucios en [Draft_data](Draft_data) que posteriormente he tenido que revisar y limpiar, por lo que los datos utilizados definitivamente se encuentran en [Clean_data](Clean_data), preparados para ser utilizados para la presentación posterior.

- **[Imagenes](Imagen)**: esta carpeta contiene las imágenes que se utilizan en la creación de Tableau y el Readme.

- **[Cuadernos](Notebooks)**: Cuadernos de Jupyter creados específicamente para este proyecto, ya que me ofrecen información que me parece de interés para su presentación en Tableau. 

- **Tableau Dashboard** con link disponible: [Eventos disponibles en entradas.com](https://public.tableau.com/app/profile/sara.pazo/viz/eventim/ESTILO?publish=yes)


### 4. Limpieza de datos

- La tranformación y limpieza de datos se explica más detalladamente en cada uno de los Jupyter Notebooks.

**a. Scraping**

Primero se realiza la llamada/ transformación de cada uno de los elementos que serán necesarios para generar la tabla de esta primera URL (entradas.com).

Una vez tenemos nuestros datos, pasamos el DataFrame generado a .csv y tendremos nuestro *'events_estilo.csv'* limpio. 

**b. Archivos.csv**

Transformamos y limpiamos cada uno de los archivos importados .csv importados, que convertiremos a DataFrame. 

Una vez tenemos nuestros datos, pasamos el DataFrame generado a .csv y tendremos nuestros archivos ya limpios.



### 5. Creación del Tableau : 

LINK a la presentación: [Eventos disponibles en entradas.com](https://public.tableau.com/app/profile/sara.pazo/viz/eventim/ESTILO?publish=yes)

Este está completo por 6 hojas creadas a partir de los datos recogidos y ya mencionados. Con las anteriores se han generado 2 Dashboards interactivos con los que puedes jugar para **¡ENCONTRAR TU EVENTO PERFECTO!**

#### a. Comenzar por una breve explicación de las hojas:

- HOJA 1: **Precios de Evento por Estilo**
    - Los colores hacen referencia al estilo de música.
    - Ponemos el recuento de eventos de cada uno de los estilos, a través de su tamaño en el gráfico.
    - Vemos como la cantidad de eventos de música *clásica* disponibles es más elevada que el resto de los estilos, sin embargo, su precio es inferior a los demás
    - Observamos, por otro lado, que los *festivales* son un valor atípico en cuanto a su precio.

- HOJA 2: **Calendario de Eventos por Estilo**

    - Se muestra una tabla sobre la cantidad de eventos por mes y los estilos que predominan en cada mes.
    - Se observan un mayor número de eventos en las fechas cercanas a la navidad y posteriores. Fechas festivas o típicas de vacaciones (diciembre, enero) así como el mes de abril (que puede afectar por la Semana Santa).
    - **Clásica**: predomina en meses de frío, teniendo entre estos los eventos de conciertos de fin de año, la orquesta sinfónica...
    - **Festivales**: predominan en meses de calor y buen tiempo. Verano. Ya que estos son casi siempre al aire libre y las condiciones meteorológicas son importantes en este aspecto

- HOJA 3: **Turismo por Estilo Musical**

    - Se muestra por tamaño el total de visitantes en el trimestre.
    - El color muestra el estilo musical.
    - Comentarios: 
    A través de esta hoja podemos interpretar que el estilo *festivales* es el que se lleva cabo en épocas en las que hay más turistas en Madrid. Hemos visto antes que era el estilo que menos eventos disponibles tenía, sin embargo, los precios de estos son más elevados que los demás, e igual más multitudinarios. 

        El resto de estilos no tiene disponibles apenas eventos en el trimestre que contiene los meses de verano, es probable que la recogida de datos fluctúe, ya que la empresa puede no tener todavía disponibles eventos de otros estilos, ya que suelen surgir con menos antelación que los festivales...


- HOJA 4: **Cantidad de Eventos por Estilo**

    - Se observa el recuento de Eventos disponibles para cada Estilo. Esta tabla nos servirá como filtro en otras tablas. 


- HOJA 5: **Eventos**
    
    - La vista se desglosa por Artista, Estilo, Precios, Dia y Mes, además de encontrar en el cuadrado de la derecha en cada evento detalles con sus enlaces a la web de venta el evento. 
    - Esta tabla variará en el Dashboard a través del filtro de un gráfico de barras, categorizando por **estilos de música**. 

- HOJA 6: **Ciudad**

    - Muestra en este caso la única ciudad de la que se han recogido datos, con el fin de continuar con el scraping ampliando fronteras a las demás ciudades donde entradas.com tiene venta de sus productos.


#### b. Continuar por la explicación de los DASHBOARDS:

Tengo creados 2 dashboards en Tableau. 

**1. ESTILO** es el primero de ellos. 

![Imagen1]( 

Este contiene las tres primeras hojas que combinan el estilo musical con:  precios, turismo por trimestres, y calendario anual según eventos disponibles de cada estilo.

A través de este podemos investigar de forma ágil, rápida y muy visual, la cantidad de eventos que hay, en las fechas que más nos interesan, del estilo que queramos. 
    
¡ADEMÁS DE SABER RÁPIDAMENTE EL **PRECIO MEDIO** DE LOS EVENTOS QUE SELECCIONEMOS, **POR TRIMESTRE**, Y LA **CANTIDAD DE ESTOS EVENTOS DE NUESTRO ESTILO FAVORITO**!

Se filtra el Dashboard por la hoja de **Turismo por Estilo Musical**. 
    
Según tu selección, ¡tendrás a tu disposición los eventos disponibles en el mes que sabes o tienes interés en visitar Madrid!


**2. ENTRADAS.COM** es el segundo DASHBOARD.

![Imagen2]()

En este se encuentran las tres últimas hojas previamente explicadas. 

¡¡¡Ahora vamos a filtrar por nuestro **ESTILO musical FAVORITO**!!!

En este caso el filtro se encuentra en el gráfico arriba a la izquierda, que muestra la **Cantidad de Eventos por Estilo**. Si se selecciona un **Estilo** específico, entonces en la tabla de **Eventos** se verán desglosados aquellos eventos disponibles, con su Estilo, Precios, Dia y Mes, además de encontrar en el cuadrado de la derecha en cada evento detalles con sus enlaces a la web de venta el evento.

De esta forma, se encuentra fácilmente el evento que mejor coincida con la fecha deseada, y el link a la página de venta de sus entradas, en la ubicación deseada.









