
<h1 align='center'>
 <b>PROYECTO INDIVIDUAL Nº2</b>

 Miguel Zabaraín

 DS_FT-18

 Ene 2024
</h1>
 
# <h1 align="center">**`Siniestros viales`**</h1>

La presentación a continuación corresponde al segundo proyecto individual exigido por HENRY como parte de los requisitos para la graduación como Data Scientist. En esta ocasión, se adelantará el trabajo asumiendo el rol de un ***Data Analyst***.
<p align='center'>
<img src = 'https://static.lajornadaestadodemexico.com/wp-content/uploads/2022/08/Siniestros-viales.jpg' height = 500>
<p>

## **Descripción del problema y del trabajo a realizar**
---
Los siniestros viales, también conocidos como accidentes de tráfico o accidentes de tránsito, son eventos que involucran vehículos en las vías públicas y que pueden tener diversas causas, como colisiones entre automóviles, motocicletas, bicicletas y peatones, además de choques con objetos fijos y caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales, hasta lesiones graves e incluso fatales para uno o varios de los involucrados. Estos últimos, son el objeto del presente estudio.

En el contexto de la Ciudad Autónoma de Buenos Aires (CABA), los siniestros viales pueden ser una preocupación importante debido al alto volumen de tráfico y la densidad poblacional. Estos accidentes fatales pueden tener un impacto significativo en la seguridad de los residentes y visitantes de la ciudad, así como en la infraestructura vial y los servicios de emergencia.

Las tasas de mortalidad relacionadas con siniestros viales suelen ser un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes o por cada cierta cantidad de vehículos registrados. Reducir estas tasas es un objetivo clave para mejorar la seguridad vial y proteger la vida de las personas en la ciudad.

Es importante destacar que la prevención de siniestros viales involucra medidas como la educación vial a través de campañas que fomenten el cumplimiento de las normas de tráfico, el ajuste de la regulación vigente -y sanción de otras nuevas de llegar a requerirse-, la infraestructura segura de carreteras y calles -incluido los puentes y pasos peatonales-, la señalización vial, y hasta la promoción de vehículos más seguros. 

De lo anterior se desprende que es fundamental producir estadísticas y análisis de los datos disponibles, que lleven a insights y conclusiones que sirvan de fundamento para la implementación de medidas que sean no solo pertinentes, sino también eficaces y eficientes, de manera que se de el mejor uso posible a los recursos públicos mientras se logra disminuir -y de ser posible llevar a cero- el número de víctimas fatales con origen en accidentes viales. 


### **Acerca de la fuente de datos suministrada**
El `Observatorio de Movilidad y Seguridad Vial` (OMSV), centro de estudios que se encuentra bajo la órbita de la ***Secretaría de Transporte*** del Gobierno de la Ciudad Autónoma de Buenos Aires, suministra el archivo Excel 'homicidios.xlsx', que contiene dos hojas o tablas, a saber, 'HECHOS' y 'VICTIMAS'. 

Cada registro de 'HECHOS' tiene datos de un accidente con fatalidad, donde en términos generales encontramos columnas con datos relativos al lugar, fecha y hora, y los participantes involucrados en el accidente.

Por otro lado, 'VICTIMAS' tiene por cada registro, datos relativos a las víctimas del accidente registrado en algún registro de 'HECHOS'. Estos dos set de datos se encuentran relacionados por las columnas 'ID' en 'HECHOS' y la columna 'ID_hecho' en 'VICTIMAS'.

### **Requerimientos**
1. Se nos pide por un lado, un informe tipo EDA en torno a las hojas HECHOS y VICTIMAS del archivo Excel 'homicidios.xlsx'. Este informe deberá realizarse en un NoteBook Interactivo de Python -archivo con extensión '.ipynb'. Este documento se desarrolló y alojó en [EDA.ipynb](Code/EDA.ipynb).

2. Como segunda medida, debemos realizar un DashBoard interactivo con base en los hallazgos encontrados durante la realización del EDA. Para garantizar la interactividad, el DashBoard debe tener filtros relevantes para la apropiada selección de los datos que fungen como fuente de las visualizaciones.

Un aspecto relevante exigido para el DashBoar son los siguientes KPI's:

- *Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior*.
  
  Se definió a la **tasa de homicidios en siniestros viales** como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico.
  La fórmula presentada fue: (Número de homicidios en siniestros viales / Población total) * 100,000
  
- *Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior*.
  
  Definimos a la **cantidad de accidentes mortales de motociclistas en siniestros viales** como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal.
  Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior) * 100

  
## **Desarrollo del trabajo y conclusiones**
---
### EDA
Se realizó la carga de las tablas para una exploración inicial con los métodos de DataFrame 'head()', 'info()', 'describe()', y 'nunique()'. Con los resultados obtenidos de la exploración inicial, se realizan observaciones sobre las Columnas con valores nulos, los Tipos de datos de las columnas, Estadísticas descriptivas de columnas numéricas, Manejo de datos geoespaciales, se identificaron las Columnas categóricas y la Cantidad de datos únicos.

Posteriormente se hacen algunas transformaciones básicas pero pertinentes, como el cambio de tipo de dato de algunas columnas, se busca eliminar aqiellas filas donde todas las columnas tengan valores nulos, tambien las filas duplicadas, y algunas filas que se identificaron como problemáticas y por tanto no se justificaba mantenerlas.

Este trabajo de limpieza, consecuencia de los hallazgos iniciales del EDA, termina con la carga de datos limpios en la carpeta '../Datasets/Clean'.

Luego, se adelantan análisis para la obtención de insights e información de valor para el proyecto, los cuales se clasificaron y organizaron como se presenta en la siguiente estructura...

1. Análisis de tendencia
- Evolución anual de accidentes fatales

2. Análisis de estacionalidad
- Análisis de franjas horarias
- Análisis por día de la semana
- Análisis por mes del año

3. Análisis de localización de los accidentes
- Ubicación geográfica de accidentes fatales en Ciudad Autónoma de Buenos Aires
- Análisis por Comuna
- Análisis de accidentalidad en cruces

4. Análisis demográfico de victimas
- Análisis por Sexo de la víctima
- Análisis por rango etario de las víctimas

5. Análisis de causalidad asociada al medio de movilización
- Análisis según el medio de movilización de las víctimas
- Análisis según el medio de movilización de los acusados

6. álisis de severidad

El detalle de este trabajo lo encuentran en el documento que contempla el [EDA](Code/EDA.ipynb)

Como conclusión relevante resultado del EDA, se respalda la validez de la hipótesis tácitamente sugerida por el requerimiento del segundo KPI, relativa a que gran parte de la accidentalidad con fatalidad converge en el uso de Motos. Sin embargo, también se encontró algo no esperado, y tiene que ver con el hecho que gran parte del problema de fatalidades en accidentes viales gira en torno a Peatones y Pasajeros. En el primer caso, la persona resulta ser víctima fatal, y en el segundo, resulta acusado del accidente que termina en la muerte de otra persona. Esto se puede ver con claridad en el 'Análisis según el medio de movilización de las víctimas', y el 'Análisis según el medio de movilización de los acusados'.

### DashBoard
El DashBoard fue desarrollado y lo encuentra en este repositorio con el nombre de 'PI_DA.pbix'.
Los KPI's se desarrollaron exitosamente, y fueron nombrados:
1. Disminución Fatalidad Semestral, con Meta igual a 0,1 (10%).
2. Disminución Fatalidad Anual Moto, con Meta igual a 7 (representa 7%).

Adicionalmente, se agregó un gráfico de linea que muestra la tendencia bajista de la accidentalidad, y es nombrado 'Evolución Anual De La Accidentalidad'.

Finalmente, se atiende al hallazgo observado en el EDA y se incluyen dos gráficos de barras verticales, a saber, 'Accidentes Fatales Vs. medio de movilización de la víctima' y 'Accidentes Fatales Vs. medio de movilización del acusado'.  


## Fuente de datos
- [Buenos Aires Data](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales): Solamente el dataset denominado `Homicidios`





