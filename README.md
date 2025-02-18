# **Caso práctico de estudio para Portafolio del curso "Análisis de Datos Google 2024" de Coursera - Google**

BELLABEAT : ¿Cómo puede hacer una empresa tecnológica para el bienestar, para tomar decisiones inteligentes?
________________________________________________________________________________________________________________________
Por: **José Molina Huerta - Febrero 2025**
________________________________________________________________________________________________________________________
El caso se analizará de acuerdo con los 6 pasos para el proceso de análisis de datos:

1. Preguntar

2. Preparar

3. Procesar

4. Analizar

5. Compartir

6. Actuar
________________________________________________________________________________________________________________________

# **CONTEXTO**

Bellabeat, fabricante de productos de alta tecnología orientados a la salud de la mujer. Es una empresa pequeña
exitosa, pero tiene el potencial para convertirse en un actor más grande en el mercado global de dispositivos inteligentes. 
Urška Sršen, cofundadora y directora creativa de Bellabeat, cree que analizar los datos de actividad física de los dispositivos 
inteligentes podría desplegar nuevas oportunidades de negocio para la empresa. Han pedido consentrarse en uno de 
los productos de Bellabeat y analizar los datos de los dispositivos inteligentes para conocer el uso que hacen los 
consumidores de sus dispositivos inteligentes. 

Los hallazgos que descubiertos ayudarán a orientar la estrategia de marketing de la empresa. El análisis será presentado al 
equipo ejecutivo de Bellabeat junto con las recomendaciones de alto nivel para la estrategia de marketing de Bellabeat.

# **1. PREGUNTAR**

##  1.1 Tarea Encomendada
  Identificar cómo las personas usan sus dispositivos inteligentes para aplicarlas en un producto y generar estrategias 
  de marketing que permitan el crecimiento de la compañía.

##  1.2 Interesados (Stakeholders)
  - Urška Sršen / Cofundadora y directora creativa de Bellabeat.
  - Sando Mur / Matemático y cofundador de Bellabeat.

##  1.3 Preguntas para el análisis
  - ¿Cuáles son algunas tendencias de uso de los dispositivos inteligentes?
  - ¿Cómo se podrían aplicar estas tendencias a los clientes de Bellabeat?
  - ¿Cómo podrían ayudar estas tendencias a influir en la estrategia de marketing de Bellabeat?

# **2. PREPARAR**

##  2.1 Datos
  
  Los datos utilizados para el estudio, se pueden revisar en el siguiente enlace: https://www.kaggle.com/arashnic/fitbit .
  (CC0: Dominio público, conjunto de datos disponibles a través de Mobius(enlace de su perfil: https://www.kaggle.com/arashnic ).
  Este conjunto de datos de Kaggle contiene el seguimiento de la actividad física personal en treinta usuarios de Fitbit. Treinta y tres
  usuarios elegibles de Fitbit prestaron su consentimiento para el envío de datos personales de seguimiento que incluyen rendimiento
  de la actividad física en minutos, ritmo cardíaco y monitoreo del sueño. Incluye información sobre la actividad diaria, pasos y
  ritmo cardíaco que se puede usar para explorar los hábitos de los usuarios.

  Los datos mencionados para el análisis, están contenidos en 18 archivos CSV los cuales están en formato largo. A continuación se 
  presenta el resumen de datos de acuerdo al acercamiento ROCCC (Reliability, Original, Comprehensive, Current, Cited - en español
  R:Confiabilidad, O: Originalidad, C: Integridad, C: Actualidad, C: Citación):

  - Fiabilidad - BAJA: Los datos provienen de 33 usuarios de Fitbit que dieron su consentimiento para la presentación de datos de su rastreador personal, incluyendo resultados por minuto para la actividad física, la frecuencia cardíaca y el monitoreo del sueño.
  - Originalidad - BAJA: Datos recolectados por terceros utilizando Amazon Mechanical Turk.
  - Integralidad - MEDIA: El conjunto de datos contiene múltiples campos sobre la intensidad de la actividad diaria, calorías usadas, pasos diarios, tiempo de sueño diario y registro de peso.
  - Actualidad - BAJA: Estos datos son de marzo de 2016 a mayo de 2016. Los datos no son actuales, lo que significa que los hábitos de los usuarios pueden haber cambiado a la fecha de hoy.
  - Citación - BAJA: Los datos fueron recolectados de un tercero, por lo tanto, se desconoce la fuente.

##  2.2 Integridad de los datos

  Debido a la limitación del tamaño de la muestra (33 usuarios) y a no tener ningún detalle de la información demográfica, esto podría generar un sesgo de muestreo. No estamos seguros de si la muestra es representativa de la población en su conjunto. Otro problema que         encontraríamos es que el conjunto   de datos no es actual y también la limitación de tiempo de la encuesta (2 meses). Es por eso que le daremos a nuestro estudio de caso un enfoque operativo de acuerdo con los datos compartidos.

  
# **3. PROCESAR**
  
##  3.1  Software de procesamiento de datos
  
  Para este análisis, se utilizará **R** version 4.4.2 (2024-10-31 ucrt) -- "Pile of Leaves"
  Copyright (C) 2024 The R Foundation for Statistical Computing Platform: x86_64-w64-mingw32/x64.
  

##  3.2 Paquetes usados para el análisis
  
  - library(tidyverse)
  - library(lubridate)
  - library(readr)
  - library(dplyr)
  - library(ggplot2)
  - library(janitor)

##  3.3 Revisión y limpieza de datos

###  3.3.1 Archivos cargados al espacio de trabajo
  
  Para la carga de los archivos, se renombraron para el posterior manipulación:

```
 actividad_diaria <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/dailyActivity_merged.csv")
 
 calorias_diaria <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/dailyCalories_merged.csv")
 
 intensidad_diaria <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/dailyIntensities_merged.csv")
 
 pasos_diaria <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/dailySteps_merged.csv")
 
 latidos_psegundo <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/heartrate_seconds_merged.csv")
 
 calorias_hora <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/hourlyCalories_merged.csv")
 
 intensidades_hora <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/hourlyIntensities_merged.csv")
 
 pasos_hora <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/hourlySteps_merged.csv")
 
 calorias_min_reducido <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteCaloriesNarrow_merged.csv")
 
 calorias_min_ancho <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteCaloriesWide_merged.csv")
 
 intensidad_min_reducido <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteIntensitiesNarrow_merged.csv")
 
 intensidad_min_ancho <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteIntensitiesWide_merged.csv")
 
 METs_min_reducido <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteMETsNarrow_merged.csv")
 
 sueño_min <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteSleep_merged.csv")
 
 pasos_min_reducido <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteStepsNarrow_merged.csv")
 
 pasos_min_ancho <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/minuteStepsWide_merged.csv")
 
 sueño_diaria <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/sleepDay_merged.csv")

 peso_log <- read_csv("...- Datos crudos/Fitabase Data 4.12.16-5.12.16/weightLogInfo_merged.csv")
 
```

Luego de la carga comencé a revisar los dataframes para conocer mejos los datos y de la forma que fueron recompilados, para comenzar
a pensar en las respuestas a las preguntas planteadas por la compañía. Decido revisar y formatear todos los archivos para que estén listos
para análisis posteriores.

###  3.3.2 Revisión de formato de los datos 

```
#Revisión de formato de los datos
str(actividad_diaria)
str(calorias_diaria)
str(intensidad_diaria)
str(pasos_diaria)
str(latidos_psegundo)
str(calorias_hora)
str(intensidades_hora)
str(pasos_hora)
str(calorias_hora)
str(intensidades_hora)
str(calorias_min_reducido)
str(calorias_min_ancho)
str(intensidad_min_reducido)
str(intensidad_min_ancho)
str(METs_min_reducido)
str(sueño_min)
str(pasos_min_reducido)
str(pasos_min_ancho)
str(sueño_diaria)
str(peso_log)

```

Muestra de la composición de los datos en los data frames cargados :

```
> str(pasos_hora)
spc_tbl_ [22,099 × 3] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ Id          : num [1:22099] 1.5e+09 1.5e+09 1.5e+09 1.5e+09 1.5e+09 ...
 $ ActivityHour: chr [1:22099] "4/12/2016 12:00:00 AM" "4/12/2016 1:00:00 AM" "4/12/2016 2:00:00 AM" "4/12/2016 3:00:00 AM" ...
 $ StepTotal   : num [1:22099] 373 160 151 0 0 ...
 - attr(*, "spec")=
  .. cols(
  ..   Id = col_double(),
  ..   ActivityHour = col_character(),
  ..   StepTotal = col_double()
  .. )
 - attr(*, "problems")=<externalptr> 
> str(calorias_hora)
spc_tbl_ [22,099 × 3] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ Id          : num [1:22099] 1.5e+09 1.5e+09 1.5e+09 1.5e+09 1.5e+09 ...
 $ ActivityHour: chr [1:22099] "4/12/2016 12:00:00 AM" "4/12/2016 1:00:00 AM" "4/12/2016 2:00:00 AM" "4/12/2016 3:00:00 AM" ...
 $ Calories    : num [1:22099] 81 61 59 47 48 48 48 47 68 141 ...
 - attr(*, "spec")=
  .. cols(
  ..   Id = col_double(),
  ..   ActivityHour = col_character(),
  ..   Calories = col_double()
  .. )
 - attr(*, "problems")=<externalptr> 
> str(intensidades_hora)
spc_tbl_ [22,099 × 4] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ Id              : num [1:22099] 1.5e+09 1.5e+09 1.5e+09 1.5e+09 1.5e+09 ...
 $ ActivityHour    : chr [1:22099] "4/12/2016 12:00:00 AM" "4/12/2016 1:00:00 AM" "4/12/2016 2:00:00 AM" "4/12/2016 3:00:00 AM" ...
 $ TotalIntensity  : num [1:22099] 20 8 7 0 0 0 0 0 13 30 ...
 $ AverageIntensity: num [1:22099] 0.333 0.133 0.117 0 0 ...
 - attr(*, "spec")=
  .. cols(
  ..   Id = col_double(),
  ..   ActivityHour = col_character(),
  ..   TotalIntensity = col_double(),
  ..   AverageIntensity = col_double()
  .. )
 - attr(*, "problems")=<externalptr> 
> str(calorias_min_reducido)
spc_tbl_ [1,325,580 × 3] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ Id            : num [1:1325580] 1.5e+09 1.5e+09 1.5e+09 1.5e+09 1.5e+09 ...
 $ ActivityMinute: chr [1:1325580] "4/12/2016 12:00:00 AM" "4/12/2016 12:01:00 AM" "4/12/2016 12:02:00 AM" "4/12/2016 12:03:00 AM" ...
 $ Calories      : num [1:1325580] 0.786 0.786 0.786 0.786 0.786 ...
 - attr(*, "spec")=
  .. cols(
  ..   Id = col_double(),
  ..   ActivityMinute = col_character(),
  ..   Calories = col_double()
  .. )
 - attr(*, "problems")=<externalptr>
```

Como se puede observar el número de usuario está en formato num y la fecha en formato con hora en algunos casos. Para efectos de análisis, se 
cambió el formato de Id, a chr y la fecha se separó en dos columnas, una en formato fecha y la otra con la hora en formato H:M:S :

```
#Formateo de Id
> actividad_diaria$Id <- as.character(actividad_diaria$Id)
> calorias_diaria$Id <- as.character(calorias_diaria$Id)
> intensidad_diaria$Id <- as.character(intensidad_diaria$Id) 
> pasos_diaria$Id <- as.character(pasos_diaria$Id)
> latidos_psegundo$Id <- as.character(latidos_psegundo$Id)
> calorias_hora$Id <- as.character(calorias_hora$Id)
> intensidades_hora$Id <- as.character(intensidades_hora$Id)
> pasos_hora$Id <- as.character(pasos_hora$Id)
> calorias_min_reducido$Id <- as.character(calorias_min_reducido$Id)
> calorias_min_ancho$Id <- as.character(calorias_min_ancho$Id)
> intensidad_min_reducido$Id <- as.character(intensidad_min_reducido$Id)
> intensidad_min_ancho$Id <- as.character(intensidad_min_ancho$Id)
> METs_min_reducido$Id <- as.character(METs_min_reducido$Id)
> sueño_min$Id <- as.character(sueño_min$Id)
> pasos_min_reducido$Id <- as.character(pasos_min_reducido$Id)
> pasos_min_ancho$Id <- as.character(pasos_min_ancho$Id)
> sueño_diaria$Id <- as.character(sueño_diaria$Id)
> peso_log$Id <- as.character(peso_log$Id)

#Formateo fechas
> actividad_diaria$ActivityDate <- as.POSIXct(actividad_diaria$ActivityDate,
+                                          format = "%m/%d/%Y",
+                                          tz = Sys.timezone())
> calorias_diaria$ActivityDay <- as.POSIXct(calorias_diaria$ActivityDay,
+                            format = "%m/%d/%Y",
+                            tz = Sys.timezone())
> intensidad_diaria$ActivityDay <- as.POSIXct(intensidad_diaria$ActivityDay,
+                                             format = "%m/%d/%Y",
+                                             tz = Sys.timezone())
> pasos_diaria$ActivityDay <- as.POSIXct(pasos_diaria$ActivityDay,
+                                       format = "%m/%d/%Y",
+                                       tz = Sys.timezone())
> latidos_psegundo$Time <- as.POSIXct(latidos_psegundo$Time,
+                                     format = "%m/%d/%Y %H:%M:%S",
+                                     tz = Sys.timezone())
> latidos_psegundo$Fecha <- date(latidos_psegundo$Time)
> latidos_psegundo$Hora <- format(latidos_psegundo$Time, format = '%H:%M:%S %p')
> calorias_hora$ActivityHour <- as.POSIXct(calorias_hora$ActivityHour,
+                                          format = "%m/%d/%Y %H:%M:%S",
+                                          tz = Sys.timezone())
> calorias_hora$Fecha <- date(calorias_hora$ActivityHour)
> calorias_hora$Hora <- format(calorias_hora$ActivityHour, format = '%H:%M:%S %p')
> intensidades_hora$ActivityHour <- as.POSIXct(intensidades_hora$ActivityHour,
+                                             format = "%m/%d/%Y %H:%M:%S",
+                                             tz = Sys.timezone())
> intensidades_hora$Fecha <- date(intensidades_hora$ActivityHour)
> intensidades_hora$Hora <- format(intensidades_hora$ActivityHour, format = '%H:%M:%S %p')
> pasos_hora$ActivityHour <- as.POSIXct(pasos_hora$ActivityHour,
+                                       format = "%m/%d/%Y %H:%M:%S",
+                                       tz = Sys.timezone())
> pasos_hora$Fecha <- date(pasos_hora$ActivityHour)
> pasos_hora$Hora <- format(pasos_hora$ActivityHour, format = '%H:%M:%S %p')
> calorias_min_reducido$ActivityMinute <- as.POSIXct(calorias_min_reducido$ActivityMinute,
+                                                    format = "%m/%d/%Y %H:%M:%S",
+                                                    tz = Sys.timezone())
> calorias_min_reducido$Fecha <- date(calorias_min_reducido$ActivityMinute)
> calorias_min_reducido$Hora <- format(calorias_min_reducido$ActivityMinute, format = '%H:%M:%S %p')
> calorias_min_ancho$ActivityHour <- as.POSIXct(calorias_min_ancho$ActivityHour,
+                                               format = "%m/%d/%Y %H:%M:%S",
+                                               tz = Sys.timezone())
> calorias_min_ancho$Fecha <- date(calorias_min_ancho$ActivityHour)
> calorias_min_ancho$Hora <- format(calorias_min_ancho$ActivityHour, format = '%H:%M:%S %p')
> intensidad_min_reducido$ActivityMinute <- as.POSIXct(intensidad_min_reducido$ActivityMinute,
+                                                      format = "%m/%d/%Y %H:%M:%S",
+                                                      tz = Sys.timezone())
> intensidad_min_reducido$Fecha <- date(intensidad_min_reducido$ActivityMinute)
> intensidad_min_reducido$Hora <- format(intensidad_min_reducido$ActivityMinute, format = '%H:%M:%S %p')
> intensidad_min_ancho$ActivityHour <- as.POSIXct(intensidad_min_ancho$ActivityHour,
+                                                 format = "%m/%d/%Y %H:%M:%S",
+                                                 tz = Sys.timezone())
> intensidad_min_ancho$Fecha <- date(intensidad_min_ancho$ActivityHour)
> intensidad_min_ancho$Hora <- format(intensidad_min_ancho$ActivityHour, format = '%H:%M:%S %p')
> METs_min_reducido$ActivityMinute <- as.POSIXct(METs_min_reducido$ActivityMinute,
+                                                format = "%m/%d/%Y %H:%M:%S",
+                                                tz = Sys.timezone())
> METs_min_reducido$Fecha <- date(METs_min_reducido$ActivityMinute)
> METs_min_reducido$Hora <- format(METs_min_reducido$ActivityMinute, format = '%H:%M:%S %p')
> sueño_min$date <-  as.POSIXct(sueño_min$date,
+                               format = "%m/%d/%Y %H:%M:%S",
+                               tz = Sys.timezone())
> sueño_min$Fecha <- date(sueño_min$date)
> sueño_min$Hora <- format(sueño_min$date, format = '%H:%M:%S %p')
> pasos_min_reducido$ActivityMinute <- as.POSIXct(pasos_min_reducido$ActivityMinute,
+                                                 format = "%m/%d/%Y %H:%M:%S",
+                                                 tz = Sys.timezone())
> pasos_min_reducido$Fecha <- date(pasos_min_reducido$ActivityMinute)
> pasos_min_reducido$Hora <- format(pasos_min_reducido$ActivityMinute, format = '%H:%M:%S %p')
> pasos_min_ancho$ActivityHour <- as.POSIXct(pasos_min_ancho$ActivityHour,
+                                            format = "%m/%d/%Y %H:%M:%S",
+                                            tz = Sys.timezone())
> pasos_min_ancho$Fecha <- date(pasos_min_ancho$ActivityHour)
> pasos_min_ancho$Hora <- format(pasos_min_ancho$ActivityHour, format = '%H:%M:%S %p')
> sueño_diaria$SleepDay <- as.POSIXct(sueño_diaria$SleepDay,
+                                     format = "%m/%d/%Y %H:%M:%S",
+                                     tz = Sys.timezone())
> sueño_diaria$Fecha <- date(sueño_diaria$SleepDay)
> sueño_diaria$Hora <- format(sueño_diaria$SleepDay, format = '%H:%M:%S %p')
> peso_log$Date <- as.POSIXct(peso_log$Date,
+                        format = "%m/%d/%Y %H:%M:%S",
+                        tz = Sys.timezone())
> peso_log$Fecha <- date(peso_log$Date)
> peso_log$Hora <- format(peso_log$Date, format = '%H:%M:%S %p') 

```

Revisión de duplicados de todos los archivos:

```
#Se revisan dataframes buscando datos duplicados de todos los archivos

dupl_actividaddiaria <- actividad_diaria %>%
  filter(duplicated(.))

print(dupl_actividaddiaria)

dupl_caloriasdiaria <- calorias_diaria %>%
  filter(duplicated(.))

```

Se detectaron datos duplicados en los siguientes data frames:

```
#data frames con duplicados
sueño_min
sueño_diaria

#Quitando duplicados
sueño_min_nodupl <- sueño_min %>%
  distinct()

sueño_diar_nodupl <- sueño_diaria %>%
  distinct()

```


# **4. ANALIZAR**

Para comenzar el análisis, se identifica cuántos usuarios compartieron los datos con la plataforma de FitBit, por archivo de recolección de datos:

```
> n_distinct(actividad_diaria$Id)
[1] 33
> n_distinct(calorias_diaria$Id)
[1] 33
> n_distinct(intensidad_diaria$Id)
[1] 33
> n_distinct(pasos_diaria$Id)
[1] 33
> n_distinct(latidos_psegundo$Id)
[1] 14
> n_distinct(calorias_hora$Id)
[1] 33
> n_distinct(intensidades_hora$Id)
[1] 33
> n_distinct(pasos_hora$Id)
[1] 33
> n_distinct(calorias_hora$Id)
[1] 33
> n_distinct(intensidades_hora$Id)
[1] 33
> n_distinct(calorias_min_reducido$Id)
[1] 33
> n_distinct(calorias_min_ancho$Id)
[1] 33
> n_distinct(intensidad_min_reducido$Id)
[1] 33
> n_distinct(intensidad_min_ancho$Id)
[1] 33
> n_distinct(METs_min_reducido$Id)
[1] 33
> n_distinct(sueño_min$Id)
[1] 24
> n_distinct(pasos_min_reducido$Id)
[1] 33
> n_distinct(pasos_min_ancho$Id)
[1] 33
> n_distinct(sueño_diaria$Id)
[1] 24
> n_distinct(peso_log$Id)
[1] 8

```




Del cuadro anterior, podemos observar que en algunos archivos no está la misma cantidad de usuarios, como resumen (insertar tabla ?)




# **5. COMPARTIR**



# **6. ACTUAR**

Luego de analizar los datos proporcionados para evaluar las posibles estrategias de marketing para un productos
  









