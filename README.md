**Caso práctico de estudio para Portafolio del curso "Análisis de Datos Google 2024" de Coursera - Google**

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

CONTEXTO

Bellabeat, fabricante de productos de alta tecnología orientados a la salud de la mujer. Es una empresa pequeña
exitosa, pero tiene el potencial para convertirse en un actor más grande en el mercado global de dispositivos inteligentes. 
Urška Sršen, cofundadora y directora creativa de Bellabeat, cree que analizar los datos de actividad física de los dispositivos 
inteligentes podría desplegar nuevas oportunidades de negocio para la empresa. Han pedido consentrarse en uno de 
los productos de Bellabeat y analizar los datos de los dispositivos inteligentes para conocer el uso que hacen los 
consumidores de sus dispositivos inteligentes. 

Los hallazgos que descubiertos ayudarán a orientar la estrategia de marketing de la empresa. El análisis será presentado al 
equipo ejecutivo de Bellabeat junto con las recomendaciones de alto nivel para la estrategia de marketing de Bellabeat.

1. PREGUNTAR

  1.1 Tarea Encomendada
  Identificar cómo las personas usan sus dispositivos inteligentes para aplicarlas en un producto y generar estrategias 
  de marketing que permitan el crecimiento de la compañía.

  1.2 Interesados (Stakeholders)
  - Urška Sršen / Cofundadora y directora creativa de Bellabeat.
  - Sando Mur / Matemático y cofundador de Bellabeat.

  1.3 Preguntas para el análisis
  - ¿Cuáles son algunas tendencias de uso de los dispositivos inteligentes?
  - ¿Cómo se podrían aplicar estas tendencias a los clientes de Bellabeat?
  - ¿Cómo podrían ayudar estas tendencias a influir en la estrategia de marketing de Bellabeat?

2. PREPARAR

  2.1 Datos
  
  Los datos utilizados para el estudio, se pueden revisar en el siguiente enlace: https://www.kaggle.com/arashnic/fitbit .
  (CC0: Dominio público, conjunto de datos disponibles a través de Mobius(enlace de su perfil: https://www.kaggle.com/arashnic ).
  Este conjunto de datos de Kaggle contiene el seguimiento de la actividad física personal en treinta usuarios de Fitbit. Treinta
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

  2.2 Integridad de los datos

  
  

3. PROCESAR


  
  3.1  Software de procesamiento de datos
  
  Para este análisis, se utilizará **R** version 4.4.2 (2024-10-31 ucrt) -- "Pile of Leaves"
  Copyright (C) 2024 The R Foundation for Statistical Computing Platform: x86_64-w64-mingw32/x64.
  
  Debido a la capacidad de poder operar con gran cantidad de datos y el registro que se puede llevar para luego poder replicar los análisis en casos de estudio similares.

  3.2 Paquetes usados para el análisis
  
  - library(tidyverse)
  - library(lubridate)
  - library(readr)
  - library(dplyr)
  - library(ggplot2)
  - library(janitor)


4. ANALIZAR


5. COMPARTIR


6. ACTUAR

Luego de analizar los datos proporcionados para evaluar las posibles estrategias de marketing para un productos
  









