# Siniestros viales

En este proyecto voy a simular ser un análista de datos del gobierno de Buenos Aires, analizando un archivo que contiene datos acerca de siniestros víales ocurridos en el periodo 2016-2021.

Los datos vinieron provistos en un archivo en formato .xlsx (excel) en el cuál hay dos hojas de datos, una de Hechos, que cuenta, cómo su mismo nombre indica, de ciertas columnas que contienen los datos de un siniestro víal en particular, en total, esta tabla venía originalmente con 21 columnas, algunas de las cuales eran: "ID del hecho, cantidad de víctimas, FECHA, HORA".
La otra hoja de datos se llama "Víctimas", que contiene información acerca de las personas fallecidas (o no) luego del siniestro en cuestión (relacionadas ambas tablas por su ID correspondiente).

Una de las cosas que me pedían era hacer un EDA ("Exploratory Data Analysis", Analisis exploratorio de datos, en español) para entender mejor la estructura de los datos, encontrar patrones y relaciones entre ellos. Aproveché este proceso (aún sabiendo que no es lo más correcto) para también hacer ciertas transformaciones,en ciertas columnas que consideré necesarias cambiar. Por ejemplo, el en la columna ID, de la tabla Hechos, estaba expresada de la forma "AÑO-NºHECHO", lo cuál no era un numero entero cómo normalmente son las ID, así que la cambié y lo dejé de la forma "AÑONºHECHO" y lo cambié a un tipo de dato entero.

También eliminé ciertas columnas que consideré innecesarias por la cantidad de datos vacíos que contenían en su interior, por ejemplo, la columna "Altura" de la tabla Hechos, la cuál indicaba la altura de la calle en la que sucedió el accidente, se encontraba casi en su totalidad (mas de un 80%) vacía.
En Argentina, sobre todo en la parte centrica de Buenos Aires, las calles además de nombre, están acompañadas de un número que es la altura. Según mi experiencia, la mayoría de accidentes suceden en las esquinas, no en alguna altura de cierta calle, aunque también puede darse el caso de un auto que esté estacionado por ejemplo y venga otro auto de atrás y se estrelle contra él. Me encontré con una sorpresa al enterarme que casi un 25% de los datos de la columna "Cruce" estaban vacíos (esta columna contenía las calles que cruzaban a la calle principal que había considerado quién diseñó el Dataset). 
Sin embargo, más allá de saber que tanto la columna "Altura" cómo la columna "Cruce" tenían una cantidad significativa de datos faltantes, las columnas más importantes de dirección eran 2, las cuáles tomé cómo referencia para hacer posteriormente una visualización en el Dashboard en Power BI. Estas 2 columnas de las que hablo son "pos x" y "pos y", las cuáles contenian en su interior coordenadas de longitud y latitud respectivamente, las cuáles me servían de forma mucho más sencilla para trabajar y representar en un mapa una dirección en comparación con un dato dado por calles, teniendo en cuenta que es más propenso a errores, ya que es más común que el nombre de cierta calle se repita en otra parte del mundo, la dirección exacta dada por las calles posiblemente no, pero creí que podían suceder problemas de interpretación con el software del mapa de Power BI, así que no los tuve en consideración para la representación geografica de los accidentes. 
El problema con estas columnas con coordenadas es que tenían en su interior valores faltantes, pero no cómo el resto de columnas de la tabla de Hechos, sino que, en lugar de tener un número decimal en su interior, tenían un punto, por lo cuál, decidí eliminar las filas en dónde las coordenadas tanto longitudinales cómo latitudinales eran un punto, ya que no me ofrecían una información valiosa y/o representable en un mapa. No era una cantidad muy significativa del total. Eran 4 filas, y por suerte coincidian los faltantes en ambas columnas, no se dió el caso que faltaban en una columna y en otra no.

También decidí renombrar ciertas columnas que me parecía que era más adecuado tenerlas con un nombre más "normalizado" por así decirlo. 

En el EDA muestro gráficos informativos en los que saqué ciertas conclusiones, cómo por ejemplo que el grupo más afectado por los siniestros víales son las personas que viajan en motocicleta. 
También, gracias a los datos y a los gráficos pude ver que el tipo de calle en la que suelen suceder más siniestros víales, o dicho de forma más correcta, en las que sucedieron la mayor cantidad de siniestros víales en el periodo 2016 - 2021 es en las Avenidas, con una diferencia significativa

Para ello, usé librerías cómo:
- Pandas
- Matplotlib
- Seaborn
- Numpy

En la carpeta Datasets, se encuentran las tablas con las que trabajé para este proyecto, los datos fueron proporcionados en un archivo llamado homicidios.xlsx y otro diccionario de datos también en ese mismo formato, este último archivo contenía la explicación de cada variable presente en el primer archivo mencionado. Cómo adicional, también descargué un Dataset que contenía las posiciones geográficas de las distintas comunas dentro de CABA, con el cuál, tuve problemas para representar visualmente usando el mapa disponible por Power BI, pero con ayuda de otro compañero, pude utilizar un csv que contenía datos similares, con los cuáles pude representar visualmente el mapa de una mejor manera.

Cómo conclusiones de este proyecto de análisis de datos, es importante tener consideración con uno mismo y con las otras personas que circulan en la calle, evitar a toda costa manejar cuando se ha consumido alcohol u otro tipo de estupefacientes ya que eso perjudica la habilidad para conducir. Llevar puesto casco cuando se circula en moto, que aunque no evita un accidente fatal, reduce considerablemente las posibilidades. 
También es importante evitar en lo posible o circular con precaución en caso de ser inevitable el conducir durante horarios de la madrugada, ya que allí los datos muestran que hay un mayor volumen de siniestros viales.
Otro detalle, en la epoca de las fiestas, en diciembre, también el volumen de accidentes es considerablemente mayor, por lo cuál, es importante evitar conducir largas distancias durante esos periodos festivos, dónde las personas tienden a consumir alcohol.
Otro detalle importante es que gran parte, y con diferencia, de los accidentes suceden en las avenidas, por lo cuál, al circular por estas mismas, es importante estar atento, evitar el uso del celular mientras se conduce y hacerlo de una forma consciente y prudente.

Muchas gracias.
