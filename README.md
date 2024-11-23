# Caso CS:GO

* Dataset 📁 [CS-GO](https://github.com/vict360/CS.GO/blob/main/B_demo_round_traces.csv)
* Presentación 📊 [PPT](https://docs.google.com/presentation/d/1u55ZxPB9UAYgjno5ME9_HUMgVoYaiwZo/edit?usp=sharing&ouid=113786428185283411378&rtpof=true&sd=true)

## Objetivo 🎯💡
* Analizar un dataset del videojuego **Counter Strike: GO** para predecir la probabilidad de que un jugador gane una partida.
* Para lograrlo, se identificarán y seleccionarán las variables más relevantes que permitan construir un modelo confiable. Este proceso incluirá responder preguntas clave derivadas del análisis exploratorio, priorizando los datos que tengan mayor impacto en el resultado de las partidas.  


## Contexto 📝
En cada partida de Counter Strike: GO dos equipos de 5 jugadores (denominados terroristas y contra-terroristas) se enfrentan. El objetivo del equipo terrorista es plantar una bomba con timer de 45 segundos en uno de dos sitios específicos dentro de un mapa.

Por otro lado, el objetivo del equipo contra-terrorista es evitar que la bomba sea plantada o desactivarla antes de que esta explote cuando ya ha sido plantada.

Los datos a utilizar corresponden a sobre 7000 partidas del juego (con un máximo de 10 jugadores c/u). Los datos han sido extraídos de replays, los cuales son archivos propietarios con la información de cada una de las acciones realizadas por cada jugador dentro de una partida.

Los replays han sido extraídos de la red utilizando un scrapper y pre-procesados utilizando un script. En este miniproyecto trabajaremos con el resultado de este pre-proceso el cual corresponde a un archivo CSV con 79157 filas, cada una correspondiente a un jugador dentro de una partida. El archivo contiene 36 columnas correspondientes a variables que describen las acciones del jugador dentro del juego.

## Preguntas Guía ❓
* ¿Cuántas victorias y derrotas tiene el DF?
* ¿Cuántas victorias hay según el equipo?
* ¿Cuántos jugadores sobrevivientes ganaron y perdieron?
* ¿Qué Team tiene más sobrevivientes victoriosos?
* ¿Cúal es el mapa con mayor victorias?
* ¿Cúal es la distribución de MatchKills por victorias?
* ¿Como se distribuye el valor del equipamiento del Team al inicio de la partida?


## Conclusiones 📋
A pesar que el algoritmo Árbol de Decisión es el más exacto en su predicción, no esta tan alejado con los resultados en las metricas de los otros algoritmos seleccionados, ya que su score varia entre 0.59 a 0.61.
Por otro lado, el Dataframe contiene muchos datos categoricos, por lo cual su transformación para poder ser utilizados en el modelo es entre 0 y 1, bajando la posibilidad de tener un mayor rango de datos númericos.

**Apreciación:**
- Podemos ver que los datos elegidos, tiene una relación inversamente proporcional con la etiqueta elegida "MatchWinner", es decir, que mayor valor tenga las variables seleccionadas en el estudio, la probabilidad de que la persona obtenga la victoria es menor.
El modelo más confiable seria el árbol de decisión junto con el algoritmo no supervisado "Clustering", en el cual, al colocar valores más altos en sus caracteristicas, la probabilidad de que pierda es mayor en ambos algoritmos.

**Sugerencias:**
- Para un mejor modelo de predección, es vital conocer mayormente los datos del equipo completo, en vez de conocer los datos individuales de los jugadores, debido a que este juego tiene la dinamica de equipo y no solo un jugador.
La mayor cantidad de los jugadores no logro pasar más de 8 minutos con vida, por ende, los datos luego de los 10 minutos son datos outliers.
Para mejor analisis de su victoria y derrota, se debería indicar el resultado de su objetivo, ya sea por parte del Team (explotar o desactivar las bombas), de esta forma se podra hacer un analisis más preciso en su victoria o derrota.

## Tecnologías y Librerías 💻

- **Python** 🐍: Lenguaje de programación de alto nivel, ampliamente utilizado en análisis de datos.
- **Numpy** 🔢: Librería para cálculos numéricos y operaciones con matrices.
- **Pandas** 🐼: Librería para la manipulación y análisis de datos en estructuras de datos como DataFrames.
- **Seaborn** 📊: Librería para visualización de datos basada en Matplotlib, ideal para gráficos estadísticos.
- **Matplotlib - pyplot** 📈: Herramienta de visualización de gráficos, ampliamente utilizada para crear gráficos estáticos.
- **Google Colab** ☁️: Entorno de desarrollo interactivo basado en la web, ideal para ejecutar Python en la nube.
- **Scikit-learn (sklearn)** 🤖: Librería para machine learning que proporciona herramientas para modelado predictivo, clasificación, regresión y preprocesamiento de datos.

## Procedimientos 🛠️  
1. 📊 **Análisis Exploratorio de Datos (EDA):**  
   - Exploración inicial para identificar patrones, relaciones y valores atípicos.  

2. 🧹 **Preprocesamiento de Datos:**  
   - Limpieza de datos, manejo de valores faltantes y creación de nuevas características.  

3. 🤖 **Construcción de Modelos:**  
   - **Aprendizaje Supervisado:** Modelos de clasificación y predicción basados en datos etiquetados.  
   - **Aprendizaje No Supervisado:** Detección de patrones y agrupaciones en datos no etiquetados.

## Diccionario de Variables 🏷️
## 📋 Variables  

| **Variable**                         | **Descripción**                                                                                      |
|--------------------------------------|------------------------------------------------------------------------------------------------------|
| **MatchWinner**                      | **Etiqueta.** True = Ganador / False = Perdedor. Indica si el jugador ganó o no la partida.          |
| **Map**                              | Nombre del mapa donde se jugó la partida.                                                           |
| **Team**                             | Nombre del equipo al que pertenece el jugador.                                                      |
| **MatchId**                          | Identificador de la partida.                                                                        |
| **RoundId**                          | Identificador de la ronda (los equipos se enfrentan en rondas de 5 partidas seguidas).              |
| **SteamID**                          | Identificador único del jugador.                                                                    |
| **MatchWinner**                      | Indica si el jugador ganó o no la partida.                                                          |
| **RoundWinner**                      | Indica si el jugador ganó o no la ronda analizada.                                                  |
| **Survived**                         | Indica si el jugador sobrevivió o no a la partida (sobrevivir no es sinónimo de ganar).             |
| **AbnormalMatch**                    | Indica si la partida tuvo un error por conexión de red.                                             |
| **TimeAlive**                        | Tiempo en segundos que el jugador estuvo vivo durante el juego.                                     |
| **ScaledTimeAlive**                  | Tiempo de vida del jugador escalado al tiempo de vida del jugador que más duró en la ronda.         |
| **AvgCentroidDistance**              | Distancia promedio del jugador al centroide del equipo.                                             |
| **TravelledDistance**                | Distancia promedio viajada por el jugador durante la partida.                                       |
| **AvgSiteDistance**                  | Distancia promedio del jugador al objetivo más cercano.                                             |
| **AvgRoundVelocity**                 | Velocidad promedio del jugador en la ronda.                                                        |
| **AvgKillDistance**                  | Distancia promedio viajada por el jugador antes de su primer kill.                                  |
| **RLethalGrenadesThrown** / **RNonLethalGrenadesThrown** | Cantidad de granadas lanzadas, categorizadas en letales y no-letales.                              |
| **PrimaryXXXX**                      | Porcentaje de uso de arma primaria (AssaultRifle, SniperRifle, SMG, Heavy, Pistol).                 |
| **[Match/Round]Assists**             | Cantidad de asistencias efectuadas por el jugador durante la partida o la ronda.                   |
| **[Match/Round]Kills**               | Cantidad de kills efectuados por el jugador durante la partida o la ronda.                         |
| **[Match/Round]FlankKills**          | Cantidad de kills efectuados por el jugador sin que la víctima lo viese durante la partida o ronda. |
| **[Match/Round]HeadShots**           | Cantidad de kills efectuados por el jugador a través de un tiro en la cabeza durante la partida o ronda. |
| **RoundStartingEquipmentValue**      | Valor del equipamiento llevado por el jugador al inicio de la ronda.                                |
| **TeamStartingEquipmentValue**       | Valor promedio del equipamiento llevado por el equipo del jugador al inicio de la ronda.            |
| **AvgMatchKillDist**                 | Distancia promedio viajada por el jugador entre kills.                                              |



## Creditos 🙌
* David Valenzuela
* Mauricio Donato
* Víctor Vargas
