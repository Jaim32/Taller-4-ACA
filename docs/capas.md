---
title: Capas y Datos Espaciales
summary: Cómo cargar, editar y consultar capas en QGIS
date: 2025-06-12
---

# Capas y Datos Espaciales en QGIS

En QGIS, la información geográfica se organiza en **capas**. Cada capa representa un conjunto de datos espaciales de un tipo específico.

## Tipos de capas

| Tipo | Formato común | Descripción |
|------|--------------|-------------|
| Vectorial | `.shp`, `.geojson`, `.gpkg` | Puntos, líneas y polígonos |
| Raster | `.tif`, `.png`, `.img` | Imágenes y grillas de valores |
| Base de datos | PostGIS, SpatiaLite | Capas desde una BD espacial |
| WMS/WFS | URL | Servicios web de mapas |

## Cargar una capa

=== "Capa vectorial"
    Ve a **Capa → Agregar capa → Agregar capa vectorial** y selecciona tu archivo `.shp` o `.geojson`.

    También puedes arrastrar el archivo directamente al lienzo de QGIS.

    ```python
    # Con PyQGIS
    capa = QgsVectorLayer("/ruta/archivo.shp", "Mi capa", "ogr")
    QgsProject.instance().addMapLayer(capa)
    ```

=== "Capa desde PostGIS"
    Ve a **Capa → Agregar capa → Agregar capa PostGIS** e ingresa:

    ```
    Host:     localhost
    Puerto:   5432
    Base de datos: mi_bd
    Usuario:  postgres
    ```

    ```python
    # Con PyQGIS
    uri = QgsDataSourceUri()
    uri.setConnection("localhost", "5432", "mi_bd", "postgres", "")
    uri.setDataSource("public", "mi_tabla", "geom")
    capa = QgsVectorLayer(uri.uri(), "PostGIS layer", "postgres")
    QgsProject.instance().addMapLayer(capa)
    ```

## Consultas y filtros

Puedes filtrar los datos de una capa usando expresiones en **Propiedades de capa → Origen → Proveedor de filtro**:

```sql
-- Filtrar municipios de un departamento específico
"departamento" = 'San Salvador'

-- Filtrar por área mayor a 100 km²
"area_km2" > 100
```

## Imagen de referencia

![Interfaz de capas en QGIS](img/logo.png)

!!! note "Nota"
    Si una capa PostGIS no se visualiza como mapa sino como tabla, verifica que la columna de geometría tenga un **SRID** asignado correctamente con:
    ```sql
    SELECT UpdateGeometrySRID('public', 'mi_tabla', 'geom', 4326);
    ```

!!! tip "Consejo"
    Usa el formato **GeoPackage (`.gpkg`)** en lugar de Shapefile cuando sea posible: soporta múltiples capas en un solo archivo y no tiene límite de 255 caracteres en nombres de columnas.

Regresa al [Inicio](index.md) o revisa la [Instalación](instalacion.md).
