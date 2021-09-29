# crear_gcp_list
Crea un archivo gcp_list.txt para OpenDroneMap a partir de un pafs.xml de Agisoft Metashape

----

Los Puntos de Apoyo Fotogramétrico pueden ser exportados de la aplicación Agisoft Metashape en un archivo estructurado XML.
Los mismos se pueden incorporar a un procesamiento fotogramétrico en OpenDroneMap, como un archivo de texto llamado gcp_list.txt.

Los PAFs fueron cargados en Metashape en coordenadas geográficas con 6 decimales (indeterminación de 10 cm en las longitudes).
Para mejorar la precisión, se realizó un relevamiento GNSS de solución fija en postprocesamiento diferencial, en coordenadas POSGAR 2007 / Argenitna Faja 5, con marco de referencia vertical SRVN16.

Esta notebook Jupyter lee los puntos del relevamiento, los transforma a coordenadas geográficas WGS84 utilizando la transformación EPSG:5351.
A los puntos del relevamiento transformados, se les cambia el marco de referencia vertical para convertir las alturas ortométricas en elipsoidales en el marco WGS84.

Lee el archivo pafs.xml exportado por Metashape y crea diferentes DataFrames para los elementos 'markers', 'cameras' y 'locations'.
Combina las marcas con las coordenadas transdformadas y corregidas anteriormente y luego combina los DataFrames para crear el archivo de salida con la estructura requerida por OpenDroneMap.  
