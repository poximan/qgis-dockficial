# qgis-dockficial
despliegue automatico via docker-compose de un sistema qgis (server + proxy inverso).
sigue [documentacion oficial](https://docs.qgis.org/3.16/en/docs/server_manual/containerized_deployment.html)

## proyecto qgs (Quantum GiS)
deberá copiarse dentro de ./servidor/data/ con nombre `osm.qgs`

## despliegue
para desplegar ejecutar
```sh
docker-compose.exe up --build
```

## url's
en caso que el despliegue haya sido satisfactorio, y exista un proyecto QGIS cargado en ./servidor/data/, se podrán verificar las siguientes url's
- la defincion _capabilities_ debe accederse desde
> http://localhost:8080/qgis-server/?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities

- una interpretacion grafica (render) del mapa debe ser accesible desde
> http://localhost:8080/qgis-server/?request=GetMap&service=WMS&version=1.3.0&bbox=-7280626.9442,-5286843.4984,-7207247.3970,-5250344.8174&crs=EPSG:3857&width=1422&height=800&format=image/jpeg&layers=poli_manzanas

| argumento | descripcion |
| --------- | ----------- |
| bbox | Bounding box for map extent. Value is minx, miny, maxx, maxy in units of the CRS |
| crs | Coordinate reference systems (CRS). QGIS supports different CRS identifiers (has EPSG:<code>) |

## diccionario
- ¿Qué es un SRID?

Un SRID (Spatial Reference System Identifier) o Identificador de Referencia Espacial, es un identificador estándar único que hace referencia a un Sistema de Coordenadas concreto. Cada código, por tanto, se asocia de forma exclusiva a un Sistema de Coordenadas.

El SRID define todos los parámetros del Sistema de Coordenadas y la proyección de nuestros datos. El SRID es conveniente porque contiene toda la información sobre la proyección del mapa (que puede ser muy compleja) en un solo número.

Existen varios SRID que han sido definidos por el EPSG.

- ¿Qué es el EPSG?

EPSG es el acrónimo de European Petroleum Survey Group, organización relacionada con la industria petrolera en Europa. Este organismo _estuvo_ formado por especialistas en geodesia, topografía y cartografía aplicadas al área de explotación y desarrolló un repositorio de parámetros geodésicos que contiene información sobre sistemas (marcos) de referencia antiguos y modernos (geocéntricos), proyecciones cartográficas y elipsoides de todo el mundo.

Las tareas del EPSG son desarrolladas en este momento por el Subcomité de Geodesia del Comité de Geomática de la International Association of Oil and Gas Producers (OGP), aunque el conjunto de datos continúa llamándose EPSG.