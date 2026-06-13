---
title: Instalación y Configuración
summary: Guía de instalación de QGIS en diferentes sistemas operativos
date: 2025-06-12
---

# Instalación y Configuración de QGIS

## Versiones disponibles

| Versión | Tipo | Recomendada para |
|---------|------|-----------------|
| QGIS 3.x LTR | Long Term Release | Producción y uso académico |
| QGIS 3.x Latest | Última versión | Nuevas funcionalidades |
| QGIS 2.x | Antigua | No recomendada |

## Instalación por sistema operativo

=== "Windows"
    1. Descarga el instalador desde [qgis.org/download](https://qgis.org/download).
    2. Elige la versión **QGIS Standalone Installer (LTR)**.
    3. Ejecuta el instalador y sigue los pasos.

    ```bash
    # Alternativa con winget
    winget install QGIS.QGIS
    ```

=== "macOS"
    ```bash
    # Con Homebrew
    brew install --cask qgis
    ```

    O descarga el `.dmg` directamente desde [qgis.org/download](https://qgis.org/download).

=== "Ubuntu/Debian"
    ```bash
    sudo apt update
    sudo apt install qgis qgis-plugin-grass
    ```

    Para la versión más reciente vía repositorio oficial:
    ```bash
    sudo add-apt-repository ppa:ubuntugis/ppa
    sudo apt update
    sudo apt install qgis
    ```

## Configuración inicial

Al abrir QGIS por primera vez se recomienda:

1. Ir a **Configuración → Opciones → SRC** y definir el sistema de referencia por defecto (ej. `EPSG:4326` para WGS84).
2. Activar el panel **Explorador** desde **Ver → Paneles**.
3. Instalar plugins esenciales desde **Complementos → Administrar e instalar complementos**.

!!! tip "Consejo"
    Instala el plugin **QuickMapServices** para agregar fondos de mapa como OpenStreetMap directamente en QGIS.

!!! warning "Advertencia"
    En macOS, QGIS puede pedir permisos de seguridad la primera vez. Ve a **Preferencias del Sistema → Seguridad** y permite su ejecución.

Continúa con [Capas y Datos Espaciales](capas.md).
