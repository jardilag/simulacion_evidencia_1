Figura 3. Comparación de puntajes promedio.# Simulación Monte Carlo del Juego de Yahtzee para Dos Jugadores

Este proyecto implementa una simulación Monte Carlo del popular juego de dados Yahtzee para dos jugadores, utilizando Python. El objetivo principal es analizar estadísticamente los resultados del juego, las distribuciones de puntuaciones, y la probabilidad de victoria de cada jugador bajo una estrategia de juego predefinida. Además, se realiza una prueba estadística para determinar la significancia de las diferencias en las victorias.

## 📋 Tabla de Contenidos

- [1. Introducción al Método de Monte Carlo](#1-introducción-al-método-de-monte-carlo)
- [2. Explicación del Modelo de Simulación](#2-explicación-del-modelo-de-simulación)
- [3. Instalación de Librerías y Configuración Inicial](#3-instalación-de-librerías-y-configuración-inicial)
- [4. Implementación del Modelo de Simulación](#4-implementación-del-modelo-de-simulación)
  - [4.1. Funciones Auxiliares para el Juego](#41-funciones-auxiliares-para-el-juego)
  - [4.2. Lógica del Turno y la Partida](#42-lógica-del-turno-y-la-partida)
- [5. Análisis de Resultados y Visualización](#5-análisis-de-resultados-y-visualización)
  - [5.1. Distribución de Puntuaciones](#51-distribución-de-puntuaciones)
  - [5.2. Probabilidad de Victoria](#52-probabilidad-de-victoria)
  - [5.3. Estadísticas Descriptivas de Puntuaciones](#53-estadísticas-descriptivas-de-puntuaciones)
  - [5.4. Gráfico de Dispersión de Puntuaciones](#54-gráfico-de-dispersión-de-puntuaciones)
- [6. Exportación de Resultados a Excel](#6-exportación-de-resultados-a-excel)
- [7. Conclusiones Académicas](#7-conclusiones-académicas)
- [8. Cómo ejecutar el proyecto](#8-cómo-ejecutar-el-proyecto)


## 1. Introducción al Método de Monte Carlo

El método de Monte Carlo es una técnica computacional que se basa en la repetición de muestreos aleatorios para obtener resultados numéricos. Es ideal para problemas con componentes estocásticos o complejos, como la simulación de juegos de azar.

En este proyecto, aplicamos Monte Carlo para simular el juego de Yahtzee, permitiendo un análisis estadístico profundo de las puntuaciones, probabilidades de victoria y la variabilidad inherente al juego.

## 2. Explicación del Modelo de Simulación

El modelo de simulación abarca las reglas fundamentales de Yahtzee para dos jugadores:

1.  **Lanzamiento de Dados**: Simulación de cinco dados de seis caras, con probabilidad uniforme.
2.  **Turno de Jugador**: Cada jugador tiene 13 turnos, con hasta 3 lanzamientos de dados por turno y la posibilidad de relanzar dados seleccionados.
3.  **Sistema de Puntuación**: 13 categorías de puntuación disponibles (Unos a Seises, Tres/Cuatro Iguales, Full House, Escaleras, Yahtzee, Chance). Cada categoría solo puede usarse una vez.
4.  **Partida Completa**: Ambos jugadores completan sus 13 turnos, y se comparan las puntuaciones finales.
5.  **Simulación Monte Carlo**: El modelo se ejecuta un número determinado de veces (ej. 1000 partidas) para generar una distribución de resultados y extraer conclusiones estadísticas.

## 3. Instalación de Librerías y Configuración Inicial

Las siguientes librerías son necesarias para ejecutar el proyecto:

- `openpyxl`: Requerido por pandas para exportar a Excel.
- `random`: Para la generación de números aleatorios (lanzamiento de dados).
- `collections`: Para facilitar el conteo de dados (`collections.Counter`).
- `pandas`: Para el manejo y análisis de datos.
- `numpy`: Para operaciones numéricas.
- `matplotlib.pyplot`: Para la visualización de datos.
- `seaborn`: Para visualizaciones estadísticas avanzadas.
- `scipy.stats`: Para realizar pruebas estadísticas (e.g., Chi-cuadrado).

```bash
pip install openpyxl pandas numpy matplotlib seaborn scipy
```

## 4. Implementación del Modelo de Simulación

El código se estructura en funciones Python para simular los diferentes aspectos del juego:

### 4.1. Funciones Auxiliares para el Juego

- `lanzar_dados(num_dados)`: Simula el lanzamiento de dados.
- `calcular_puntuacion_categoria_numeros(dados, numero)`: Calcula puntuaciones para categorías numéricas.
- `calcular_puntuacion_tres_o_cuatro_iguales(dados, cantidad_minima)`: Calcula puntuaciones para 'Tres iguales' o 'Cuatro iguales'.
- `calcular_puntuacion_full_house(dados)`: Calcula puntuación para 'Full House'.
- `calcular_puntuacion_escalera_pequena(dados)`: Calcula puntuación para 'Escalera Pequeña'.
- `calcular_puntuacion_escalera_grande(dados)`: Calcula puntuación para 'Escalera Grande'.
- `calcular_puntuacion_yahtzee(dados)`: Calcula puntuación para 'Yahtzee'.
- `calcular_puntuacion_chance(dados)`: Calcula puntuación para 'Chance'.
- `calcular_puntuacion_yahtzee_general(dados, categoria)`: Función central para calcular la puntuación de cualquier categoría.

### 4.2. Lógica del Turno y la Partida

- `decidir_dados_a_mantener(dados, ronda)`: Implementa una estrategia simple para decidir qué dados mantener para relanzamientos, priorizando Yahtzee, escaleras y full house.
- `jugar_turno(jugador, categorias_usadas)`: Gestiona un turno completo de un jugador, incluyendo lanzamientos y selección de categoría.
- `jugar_partida()`: Simula una partida completa entre dos jugadores.
- `simular_juegos_montecarlo(num_simulaciones)`: Ejecuta múltiples partidas y consolida los resultados.

## 5. Análisis de Resultados y Visualización

Los resultados de la simulación se analizan y visualizan para extraer conclusiones:

### 5.1. Distribución de Puntuaciones

Se muestran histogramas para la distribución de puntuaciones finales de ambos jugadores, utilizando `seaborn` y `matplotlib`.

### 5.2. Probabilidad de Victoria

Un gráfico de barras muestra el porcentaje de victorias para cada jugador y el porcentaje de empates.

### 5.3. Estadísticas Descriptivas de Puntuaciones

Se presentan estadísticas como el promedio, la desviación estándar, el mínimo, el máximo y los cuartiles para las puntuaciones de cada jugador.

### 5.4. Gráfico de Dispersión de Puntuaciones

Un diagrama de dispersión visualiza la relación entre las puntuaciones de los dos jugadores en cada partida simulada.

## 6. Exportación de Resultados a Excel

Todos los resultados consolidados (resumen de partidas, detalle de turnos, estadísticas descriptivas y probabilidades de victoria) se exportan a un archivo Excel (`Ardila_JuanCarlos_Ruiz_EdwinAlberto_Echavarria_JorgeAndres_Resultados_Montecarlo.xlsx`) en diferentes hojas, para facilitar un análisis posterior.

## 7. Conclusiones Académicas

La simulación Monte Carlo con 1000 partidas reveló:

- **Distribución de Puntuaciones**: Puntuaciones finales concentradas alrededor de 150-160 puntos para ambos jugadores.
- **Probabilidad de Victoria**: Una ligera ventaja para el Jugador 1 (aprox. 51%) sobre el Jugador 2 (aprox. 48%), con un bajo porcentaje de empates. Una prueba Chi-cuadrado no encontró una diferencia estadísticamente significativa en las victorias, sugiriendo que la pequeña ventaja observada podría ser aleatoria o insignificante bajo esta estrategia.
- **Estadísticas Descriptivas**: Promedios y desviaciones estándar muy similares entre jugadores, indicando una estrategia equitativa.

**Implicaciones**: El método Monte Carlo es efectivo para analizar juegos de azar. La estrategia simple implementada es consistente. Para futuras investigaciones, se podría optimizar la estrategia de toma de decisiones de los dados o aumentar el número de simulaciones.

## 8. Cómo ejecutar el proyecto

Para ejecutar este proyecto, sigue estos pasos:

1.  **Clona el repositorio**:
    ```bash
    git clone <URL_DEL_REPOSITORIO>
    cd <NOMBRE_DEL_REPOSITORIO>
    ```
2.  **Crea un entorno virtual (opcional pero recomendado)**:
    ```bash
    python -m venv venv
    source venv/bin/activate  # En Windows: venv\Scripts\activate
    ```
3.  **Instala las dependencias**:
    ```bash
    pip install -r requirements.txt
    # Si no tienes requirements.txt, puedes instalar manualmente:
    # pip install openpyxl pandas numpy matplotlib seaborn scipy
    ```
4.  **Ejecuta el Notebook de Colab**:
    Abre el archivo `.ipynb` en Google Colab o Jupyter Notebook y ejecuta todas las celdas en orden. Asegúrate de que todas las funciones se definan y las simulaciones se ejecuten correctamente.

Los resultados de la simulación y los análisis se mostrarán en las celdas de salida del notebook y se exportarán a un archivo Excel en el directorio del proyecto.