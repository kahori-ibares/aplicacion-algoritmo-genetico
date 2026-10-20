Optimización de rutas en Acapulco mediante un algoritmo genético

Descripción del proyecto

Este proyecto implementa un modelo computacional para resolver una variante del Problema de Ruteo de Vehículos Capacitados (CVRP, por sus siglas en inglés). El objetivo es encontrar una distribución eficiente de rutas para una flota de vehículos que debe atender la demanda de distintas colonias de Acapulco, considerando restricciones de capacidad y número de viajes.

La solución utiliza un algoritmo genético, una metaheurística inspirada en los principios de selección natural y evolución, para explorar distintas configuraciones de rutas y buscar soluciones que reduzcan la distancia total recorrida.

Objetivos

- Modelar la distribución de mercancías desde un depósito hacia distintas colonias de Acapulco.
- Construir rutas que respeten las restricciones de capacidad de los vehículos y el número máximo de viajes.
- Minimizar la distancia total estimada de recorrido.
- Generar resultados tabulares y visuales que faciliten el análisis de la solución obtenida.

Características del modelo

La configuración inicial del programa considera los siguientes parámetros:

| Parámetro | Valor |

| Colonias consideradas | 37 |
| Vehículos disponibles | 12 |
| Capacidad por vehículo y viaje | 10 toneladas |
| Máximo de viajes por vehículo | 3 |
| Demanda total modelada | 250 toneladas |
| Tamaño de la población | 150 individuos |
| Número de generaciones | 500 |
| Individuos élite por generación | 6 |
| Semilla aleatoria | 42 |

Estos parámetros se encuentran definidos al inicio del archivo cvrp_definitivo.py y pueden modificarse para experimentar con distintas configuraciones.

¿Cómo funciona el algoritmo?

El procedimiento se divide en las siguientes etapas:

1. Representación del problema. Cada solución se representa mediante una permutación de las colonias que deben visitarse.
2. Generación de la población inicial. Se crean diferentes ordenamientos de las colonias para formar las soluciones candidatas.
3. Evaluación de soluciones. Se calcula la distancia total de los recorridos y se utiliza una función de aptitud que favorece las distancias menores.
4. Selección. Se emplea selección por torneo para elegir individuos que participarán en la siguiente generación.
5. Cruza. Se utiliza el operador Order Crossover (OX) para combinar soluciones y conservar permutaciones válidas.
6. Mutación. Se aplican intercambios de posiciones y una operación de inversión de segmentos basada en la idea de 2-opt.
7. Elitismo. Se conservan las mejores soluciones de cada generación.
8. Generación de resultados. La mejor solución encontrada se transforma en rutas y se exporta a archivos de Excel y de imagen.

El algoritmo realiza 500 generaciones con la configuración predeterminada. Como ocurre con las metaheurísticas, la solución obtenida es la mejor encontrada durante la ejecución y no necesariamente el óptimo global.

Tecnologías utilizadas

- Python: implementación del modelo y del algoritmo genético.
- Matplotlib: generación del mapa visual de las rutas.
- OpenPyXL: creación y formato del archivo de Excel.
- Bibliotecas estándar de Python: random, math y copy.

Estructura del proyecto

aplicacion-algoritmo-genetico/
├── cvrp_definitivo.py
├── mapa_rutas_acapulco.png
└── ruteo_acapulco.xlsx


- cvrp_definitivo.py: código fuente del modelo y del algoritmo genético.
- mapa_rutas_acapulco.png: representación visual de las rutas generadas.
- ruteo_acapulco.xlsx: reporte tabular de la solución, con información de los vehículos, viajes, cargas y distancias.

Los dos últimos archivos corresponden a resultados generados por una ejecución previa; pueden regenerarse al ejecutar el programa.

Instalación y ejecución

1. Requisitos

Se requiere Python 3 y las siguientes bibliotecas externas:

bash
pip install matplotlib openpyxl


 2. Ejecutar el programa

Desde una terminal ubicada en la carpeta del proyecto, ejecuta:

bash
python cvrp_definitivo.py


El programa ejecuta el algoritmo genético, obtiene la distribución de rutas, genera los reportes y muestra un resumen de los resultados en la terminal.

Nota sobre las rutas de salida: el código utiliza actualmente las rutas /mnt/user-data/outputs/ruteo_acapulco.xlsx y /mnt/user-data/outputs/mapa_rutas_acapulco.png. Para ejecutarlo en un equipo local con Windows u otro entorno, es necesario adaptar estas rutas y asegurarse de que la carpeta de salida exista.

Consideraciones y limitaciones

Este proyecto constituye un modelo computacional experimental y presenta las siguientes limitaciones:

- Demanda sintética: las demandas por colonia se generan mediante números pseudoaleatorios y se ajustan para representar un total de 250 toneladas. No deben interpretarse como registros reales de demanda comercial.
- Distancias aproximadas: las distancias se calculan a partir de coordenadas geográficas mediante la fórmula de Haversine. Representan distancias geográficas aproximadas, no distancias reales por carretera.
- Ruteo simplificado: el modelo no incorpora tiempos de tráfico, sentidos de circulación, cierres viales ni restricciones específicas de la infraestructura urbana.
- Calidad de la solución: el algoritmo genético busca reducir la distancia total, pero no garantiza encontrar el óptimo global.

Por estas razones, los resultados deben interpretarse como una aproximación experimental y no como un plan de distribución listo para implementarse en operaciones reales.

Posibles mejoras

- Incorporar datos reales de demanda por colonia.
- Utilizar distancias y tiempos de recorrido obtenidos de una red vial.
- Comparar el algoritmo genético con otros métodos de optimización.
- Analizar el efecto de los parámetros del algoritmo sobre la calidad de las soluciones.
- Incorporar restricciones operativas y económicas adicionales.

Autoría y propósito académico

Proyecto de programación y modelación computacional orientado al estudio de los algoritmos genéticos y su aplicación al problema de ruteo de vehículos capacitados(CVRP).

Referencias:
Galarcio, J. D., Buelvas, M. P., Nisperuza, P. A., López, J. M., & Hernández, H. E. (2017). Una nueva metaheurística aplicada al problema de ruteo de vehículos capacitados (CVRP) para la distribución de productos perecederos. Ingeniería e Innovación, 5(1), 60–72. https://doi.org/10.21897/23460466.1107
Mancera Quiroz, J. A., & Brito Lievano, M. A. (2024). Optimización de rutas para la gestión de residuos sólidos con algoritmos genéticos.
Moratilla, A., Fernández, E., Sánchez, J. J., & Vicario, B. (2014). Selección óptima de operadores para el tratamiento de problemas VRP con algoritmos genéticos. En Proceedings of the 2014 International Multi-Conference on Complexity, Informatics and Cybernetics (IMCIC 2014). International Institute of Informatics and Systemics. https://www.iiis.org/CDs2014/CD2014IMC/CICIC_2014/PapersPdf/CB973YI.pdf
Navarro Rodríguez, C. D. (2021). Resolución del Multi Depot Cumulative Capacitated Vehicle Routing Problem mediante computación evolutiva [Trabajo de fin de grado, Universidad de La Laguna]. Repositorio Institucional de la Universidad de La Laguna. https://riull.ull.es/xmlui/bitstream/handle/915/25441/Resolucion%20del%20Multi%20Depot%20Cumulative%20Capacitated%20Vehicle%20Routing%20Problem%20mediante%20Computacion%20Evolutiva.pdf
Oliveira, R. R. de. (2023). Solucionando o problema de roteamento de veículos capacitado com uso de algoritmos genéticos e paralelismo [Trabajo de fin de grado, Instituto Federal do Espírito Santo]. Repositorio Institucional do Instituto Federal do Espírito Santo. https://repositorio.ifes.edu.br/bitstream/handle/123456789/3946/MONOGRAFIA_CVRP_Algoritmo_Genetico_paralelismo.pdf
Orrego Cardozo, J. P., Ospina Toro, D., & Toro Ocampo, E. M. (2016). Solución al problema de ruteo de vehículos con capacidad limitada (CVRP) usando una técnica metaheurística. Scientia et Technica, 21(3), 225–233. https://doi.org/10.22517/23447214.9013
Vidal, T. (2022). Hybrid genetic search for the CVRP: Open-source implementation and SWAP* neighborhood. Computers & Operations Research, 140, Article 105643. https://doi.org/10.1016/j.cor.2021.105643
