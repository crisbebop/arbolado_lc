# Mapa interactivo arbolado urbano Las Condes

![[Ubicación de árboles con altura de 20 metros o más]](https://github.com/user-attachments/assets/470f6de4-19b7-4ecc-adec-a792952051e6)
Captura de pantalla del mapa interactivo, con la ubicación de los árboles con altura igual o mayor a 20 metros

V1. 04-12-2024.  
El proyecto consiste en un análisis descriptivo del arbolado urbano (calles y avenidas) de la comuna de Las Condes, Región Metropolitana, Chile, con la generación de un mapa interactivo.  
Los datos provienen de un archivo _shapefile_ obtenido del geoportal disponible en https://arcgismlc.lascondes.cl/portal/apps/mapviewer/index.html?webmap=9cd26fb71ea1448290450a9889467bc8.  
El _shapefile_ corresponde a la ubicación en coordenadas UTM Datum WGS84 huso 19S, de cada árbol en los ejes viales comuna, cada registro cuenta con datos descriptivos del ejemplar, como altura, diametro, número de ramas y estado general, entre otros. Sin embargo, no cuenta con la dirección del árbol.  

Se hizo una `Geocodificación` para agregar la dirección, en primera instancia se probó con la librería `Geopy`, que utiliza varios proveedores como OSM, GSM o BING, sin embargo, tiene un límite de 1000 request por día, por lo cual fue insuficiente para el proyecto. Por esta razón, se decidió emplear, la API de GoogleMaps dispible en GCP que cuenta con 40.000 request mensuales + 300 créditos para uso de cuentas nuevas, esto permite un total de 100.000 request mnesuales.  

El proceso tomó alrededor de 5 horas y 1927 árboles no pudieron ser geocodificados (dirección no disponible).

Información descriptiva encontrada:
* Total de árboles en calles y avenidas: 90983
* Top 5 especies:
  1. *Liquidambar styraciflua*, 19%
  2. *Acer negundo*, 8%
  3. *Liriodendron tulipifera*, 7%
  4. *Jacaranda mimosifolia*, 6%
  5. *Melia azedarach*, 5%
* Existen 150 árboles con más de 20 metros de altura  

* Top 5 calles con más árboles
  |Calle| árboles | más frecuente |
  |-----|---------|---------------|
  |Paul Harris| 1370 | Liquidámbar (197)|
  |Presidente Riesco|	1171|Platano Oriental	(356)|
  |Avenida Apoquindo|	1136|	Tulipero	(667)|
  |San Carlos de Apoquindo |1018|Liquidámbar	(457)|
  |Avenida Cristóbal Colón|	887|	Platano Oriental	(452)|  

El mapa interactivo considera los árboles con altura igual o mayor a 20 metros, el archivo html se encunetra en la carpeta `docs`. En la carpeta `data` se encuentra el archivo `catastro_LC_geocoded.csv` que cuenta con la información de cada árbol con la dirección obtenida de la geocodificación.

Copyright (c) 2024 [Mapa interactivo arbolado urbano Las Condes]


