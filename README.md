# MonomerFinder
MonomerFinder es una aplicación que facilita la identificación y clasificación de microplásticos presentes en imágenes capturadas por los propios usuarios. Para esto utiliza una IA que se encarga de analizar las imágenes y señalar la cantidad de microplásticos presentes y su tipo. Esta aplicación es el resultado del Reto 5 del Hackaton Coafina 2024: 'Microplásticos: un desafío ciudadano'.

## Procedimiento
Se desarrolló MonomerFinder, que permite contar y clasificar microplásticos en imágenes que funciona de la siguiente manera:

### Preparación
1. Subir el archivo app.py y la carpeta imagenes a colab.

### Instalaciones requeridas e importación de librerías
1. Se instala las principales librerías a usar:
   - Detectron2: https://detectron2.readthedocs.io/en/latest/
   - Roboflow: https://docs.roboflow.com/
   - Folium: https://python-visualization.github.io/folium/latest/
   - Gradio: https://www.gradio.app/docs
2. Se importan las librerías de uso general, además las que correran la interfaz y las que generan el modelo de reconocimiento de imagenes

### Modelo de conteo de microplásticos
1. Descarga y Configuración: Se descarga el dataset desde Roboflow y se configura en formato COCO. Se definen las rutas para los datos de entrenamiento y validación.
2. Registro del Dataset: Se registran los datasets de entrenamiento y validación.
3. Entrenamiento: Se configura y entrena un modelo Faster R-CNN con un conjunto de parámetros predefinidos(se encuentra colocado a 3000 iteraciones).
2. Predicción: Se carga el modelo entrenado y se configura el umbral de predicción que se encuentra a 0.3.

### Mapa
1. Se define una función que ubica en un mapa las coordenadas que ingresará el usuario.
2. Se convierte al mapa a otro formato para ser visto en la página.

### Textos y filtro de color
1. Se define funciones para cada apartado de textos e imagenes que se mostrara en la página web.
2. Se define una cierta paletas de colores(filtros) para que pueda reconocer el software de forma automática el color de los microplásticos.

### Interfaz
1. Entrada: Solicita al usuario que ingrese la imagen y lee la imagen correspondiente.
3. Entrada de Datos de Ubicación: Solicita datos de ubicación y muestra un mapa con el marcador.
3. Detección y Clasificación: Detecta microplásticos en la imagen, clasifica por color y dibuja las cajas delimitadoras.

### Presentación de Resultados
1. Muestra la imagen de microplásticos con las cajas delimitadoras.
2. Muestra un gráfico de barras donde se observa el conteo de microplásticos por color.
3. Presenta un resumen de la cantidad de microplásticos por color.
4. Presenta una opción de descarga de un archivo .cvs donde se encuentra los datos de ubicación y el conteo de microplásticos.
   
## Resultados
    -Los resultados se guardan en Momomer Analisis.csv.

En general es una página web que sirve de interfaz en la cual, se hace una breve presentación de qué es MonomerFinder y algunas definicione importantes para entender la relevancia de este proyecto.

**Nota: El código fue generado usando una computadora con tarjeta GPU de colab de google, es por ello que al ejecutarlo es necesario considerar que ciertas librerías y configuraciones son estrictamente necesarias para este entorno, de ejecutarse de manera local deberá ser ajustada a sus condiciones.**

**Nota 2: La interfaz se logro usando la librería de gradio, es por ello que solo estará abierta un máximo de 72 horas despues de ejecutarse, es por ello que si la página no se abrá deberá ejecutarse denuevo, este proceso tarda de 20-25 min dependiendo las consideraciones del sistema.**

# Referencias

1. Arbic, B.K., Mahu, E., Alexander, K., Buchan, P.M., Hermes, J., Kidwai, S., Kostianaia, E., Li, L., Lin, X., Mahadeo,  S.,  Maúre,  E.d.R.,  Munga,  C.,  M-Muslim,  A.,  Sant,  G.,  Seeyave,  S.,  &  Sun,  Z.  (2024).  Ocean Decade Vision 2030 White Papers – Challenge 9: Skills, Knowledge, Technology, and Participatory Decision-Making  for  All.  Paris,  UNESCO-IOC.  (The  Ocean  Decade  Series,  51.9.). https://doi.org/10.25607/k5pt-fp54
2. Hatje, V., Rayfuse, R., Polejack, P., Goddard, C., Jiang, C., Jones, D., Faloutsos, D., Fiedler, H., Akrofi, J., Sheps, K., Leung, K., Pinheiro, L.M., Pradhan, M., Castrillejo, M., Bustamante, P., Kershaw, P., Zitoun, R., Silva, S., & Kiefer, T. (2024). Ocean Decade Vision 2030 White Papers – Challenge 1: Understand and Beat Marine Pollution. Paris, UNESCO-IOC. (The Ocean Decade Series, 51.1). https://doi.org/10.25607/6m86-s908
3. Naciones Unidas. (2018). Naciones Unidas (2018). La Agenda 2030 y los Objetivos de Desarrollo Sostenible: una oportunidad para América Latina y el Caribe (LC/G.2681-P/Rev.3), Santiago
4. NESCO/COI. (2019). La ciencia que necesitamos para el océano que queremos: El Decenio de las Naciones Unidas de las Ciencias Oceánicas para el Desarrollo Sostenible (2021–2030). París. 24 pp. (Inglés) Folleto COI 2018-7
5. https://www.conasi.eu/blog/consejos-de-salud/consejos-de-salud-consejos-de-salud/ftalatos-disruptores-hormonales/
6. https://www.canada.ca/en/health-canada/services/food-nutrition/food-safety/chemical-contaminants/environmental-contaminants/polybrominated-diphenyl-ethers-pbdes/fact-sheet-polybrominated-diphenyl-ethers-pbdes-fish.html
8. https://www.canada.ca/en/health-canada/services/environmental-workplace-health/reports-publications/environmental-contaminants/human-biomonitoring-resources/2-ethylhexyl-phthalate-canadians.html
9. https://www.canada.ca/en/health-canada/services/chemicals-product-safety/phthalates.html
10. https://www.canada.ca/en/health-canada/services/chemical-substances/fact-sheets/chemicals-glance/polybrominated-diphenyl-ethers-public-summary.html
11. https://www.canada.ca/en/health-canada/services/food-nutrition/food-safety/chemical-contaminants/environmental-contaminants/polybrominated-diphenyl-ethers-pbdes/fact-sheet-polybrominated-diphenyl-ethers-pbdes-fish.html
12. https://www.canada.ca/en/environment-climate-change/services/evaluating-existing-substances/microbeads-science-summary.html#s05
13. https://wasserdreinull.de/en/knowledge/microplastics/?gad_source=1&gclid=CjwKCAjwnei0BhB-EiwAA2xuBozZhqlqwWj2oibhaJ4ng4Q_oSjlROwAm8NNc1RQQgnVRKLoK7Y0rhoC81oQAvD_BwE
