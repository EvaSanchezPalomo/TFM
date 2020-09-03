# TFM
TFM del Master en Data Science de la edición 2018 de Kschool
1.	Objetivo

Este Trabajo de Fin de Máster, tiene como objetivo analizar la base de datos de accidentes de tráfico del ayuntamiento de Madrid desde 2010 hasta 2019, de tres maneras:
-	Con un análisis en Tableau con el fin de obtener información de nuestro data set.
-	Realizando una predicción del número de accidentes mediante el uso de series temporales. Además de evaluar el impacto del Covid en dicha predicción.
-	Visualización de los puntos de concentración de accidentes mortales en Madrid y su cruce con la localización de los radares.

2.	Fuente de datos

La fuente de los tres DataSets utilizados es el portal del datos de ayuntamiento de Madrid.
Los DataSets utilizados han sido:
-	Archivos CSV de los Accidentes de trafico por año desde 2010 a 2020 ->  https://datos.madrid.es/sites/v/index.jsp?vgnextoid=7c2843010d9c3610VgnVCM2000001f4a900aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD
-	Archivo Excel de Radares en Madrid -> https://datos.madrid.es/sites/v/index.jsp?vgnextoid=4678f7de62435510VgnVCM2000001f4a900aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD
-	Archivo Shapefile de distritos de Madrid -> https://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=46b55cde99be2410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD&vgnextfmt=default

Se encuentran descargados en la carpeta: https://github.com/EvaSanchezPalomo/TFM/tree/master/1.%20Raw de este repositorio.

3.	Recursos utilizados

Los programas o librerías utilizados han sido los siguientes:
- Python:

    - Pandas
    - Numpy 
    - Pmdarima 
    - Datetime 
    - Matplotlib 
    - Geocoder 
    - Folium 

- Tableau
- Google API Geocoding
 
4.	Estructura y orden en el tratamiento de los archivos:

-	1. Primeramente será necesario ejecutar el código de Python ‘Adaptación_Datos’ https://github.com/EvaSanchezPalomo/TFM/blob/master/2.%20Codigo/Adaptacion_Datos.ipynb donde se tratan las bases de datos de accidentes de trafico desde 2010 a 2019 para unirlos en un único dataset. Dicho DataSet se separará en tres archivos: DF, DF_Accidente y DF_Victima, según sea necesario a lo largo del resto del TFM https://github.com/EvaSanchezPalomo/Prueba/tree/master/3.%20DF
-	2. Seguidamente,  se recomienda abrir el pdf, en el punto 4 ‘Análisis del DataSet’ https://github.com/EvaSanchezPalomo/TFM/blob/master/Memoria.pdf con el fin de poder conocer el comportamiento de varias variables del DataSet, habiendo utilizado el programa Tableau.
-	3. Abrir el código ‘SerieTemporal’ https://github.com/EvaSanchezPalomo/TFM/blob/master/2.%20Codigo/SerieTemporal.ipynb. En dicho código se realizará el siguiente análisis:

    a. Análisis de la evolución del número de accidentes

     ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/1.PNG)
 
    b. Predicción del número de accidentes de tráfico. Construyendo un modelo de serie temporal que usa todo el histórico de número de accidentes, desde 2010 a 2019.
    Sin transformar y transformando la serie a estacionaria. Para ello, hemos utilizado los modelos ARIMA. Obteniendo la siguiente predicción para la serie transformada a estacionaria.

     ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/2.PNG)
       
    c. Predicción añadiendo a la serie de 2010 a 2019, los datos de los dos primeros meses de 2020. Para después,  comparar la predicción de hasta febrero de 2020 con el número de accidentes que ocurrieron durante el confinamiento (marzo, abril y mayo de 2020).

    ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/3.PNG)
 
    Vemos que debido al shock que ha supuesto el Covid19, la predicción durante los meses de marzo, abril y mayo ha sido errónea (la predicción en rojo y datos reales en verde)

-	4. Abrir el código ‘Geolocalizacion’ (en la carpeta 2. Codigo de este repositorio). En dicho código se realizará el siguiente análisis:

    a. Visualizar la localización de los puntos de concentración de accidentes mortales, que han tenido fallecidos, con el fin de detectar si hay tramos donde se concentren accidentes en las carreteras/calles de Madrid y donde se situan.

     ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/4.PNG)
     
    b. Visualizar la localización de los puntos donde se encuentran los radares situados en Madrid.
 
     ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/5.PNG)
 
    c. Cruzar la localización de ambos tipos de puntos, con el fin de saber si el posicionamiento de los radares se establece de acuerdo con la posibilidad o no de que ocurran accidentes mortales.

     ![](https://github.com/EvaSanchezPalomo/TFM/blob/master/4.%20Imagenes%20Readme/6.PNG)
     
    Observamos que solo un punto de concentración de accidentes se encuentra cerca de un radar. 

-	5. A fin de poder dar un sentido en un único archivo al trabajo realizado, se ha redactado el documento ‘Memoria’ donde se puede ver en detalle el análisis realizado de los resultados obtenidos de los puntos anteriores.

5.	Conclusiones

- Los temas que se han tenido entre manos en este TFM, han sido en general poder conocer mas sobre la conducción en Madrid y específicamente poder predecir el número de accidentes y comparar la localización de los radares con los puntos de concentración de accidentes.

- Con respecto al conocimiento general, con las visualizaciones en Tableau y del trabajo derivado del tratamiento de los datos se ha conseguido este fin.

- Con respecto a la predicción del número de accidentes, aunque parecía que la predicción si parecía bastante fiable, esta finalmente ha sido errónea. Ha sido bastante lógico que esto fuera asi, ya que el shock que ha supuesto el Covid19, era muy difícil de predecir. Como ya se comento anteriormente, esto es una prueba de que no nos podemos fiar ciegamente en los modelos y de que tenemos que tener en cuenta que puede haber errores en la predicción.

- Por último, con respecto a la localización de los puntos de concentración de accidentes, ha sido posible obtenerla y compararla con la localización de los radares. Pudiendo, dar la conclusión de que no hay evidencia de que la ubicación de los radares se establezca según la localización de los puntos de concentración de accidentes.
