# Proyecto de Web Scraping y API de Google Maps

## Descripción General
Este proyecto realiza web scraping del sitio web **Portal Inmobiliario** para extraer datos de propiedades en arriendo en Viña del Mar, Valparaíso. Posteriormente, se utilizan las APIs de **Google Geocoding** y **Google Places** para obtener coordenadas y lugares cercanos a cada propiedad.

## Funcionalidades Principales
- **Web Scraping con Selenium:**
  - Automatización de la búsqueda de propiedades según filtros específicos (tipo de contrato, tipo de inmueble y ubicación).
  - Extracción de información clave como título, precio, enlace y dirección.
- **Obtención de Coordenadas:**
  - Uso de la API de Geocoding para convertir direcciones de las propiedades en coordenadas (latitud y longitud).
- **Lugares Cercanos con API de Places:**
  - Identificación de lugares cercanos a cada propiedad (restaurantes, supermercados, hospitales, entre otros).
- **Almacenamiento en Base de Datos SQLite:**
  - Creación de una base de datos local con tablas para inmuebles y lugares cercanos.
  - Consultas SQL para analizar precios promedio y características de lugares cercanos.

## Requisitos
- Python 3.7+
- Google Chrome
- Controlador de ChromeDriver (compatible con la versión del navegador)
- Dependencias de Python:
  - Selenium
  - Pandas
  - Requests
  - SQLite3

## Instalación y Configuración
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/tu_usuario/tu_repositorio.git
   ```
2. Crear un entorno virtual (opcional pero recomendado):
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```
3. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
4. Configurar las credenciales de la API de Google:
   - Crear una clave de API en Google Cloud Console.
   - Habilitar **Geocoding API** y **Places API**.
   - Reemplazar `TU_API_KEY_AQUI` en el código con tu clave de API.

## Ejecución del Proyecto
1. Ejecutar el script principal:
   ```bash
   python web_scraping_inmuebles.py
   ```
2. El resultado se guardará en:
   - **inmuebles.csv**: Datos de las propiedades.
   - **lugares_cercanos.csv**: Lugares cercanos a las propiedades.
   - Base de datos **inmuebles.db** con tablas de inmuebles y lugares cercanos.

## Consultas SQL Implementadas
1. Promedio de precios de propiedades en Viña del Mar:
   ```sql
   SELECT AVG(CAST(Precio AS FLOAT))
   FROM inmuebles
   WHERE Direccion LIKE '%viña del mar%';
   ```
2. Promedio de calificación de lugares cercanos con rating mayor o igual a 4:
   ```sql
   SELECT AVG(Rating)
   FROM lugares_cercanos
   WHERE Rating >= 4;
   ```

## Estructura del Proyecto
```
/tu_repositorio
│
├── web_scraping_inmuebles.py    # Script principal de scraping y API
├── inmuebles.csv                # Archivo CSV con propiedades
├── lugares_cercanos.csv         # Archivo CSV con lugares cercanos
├── inmuebles.db                 # Base de datos SQLite
└── README.md                    # Documentación del proyecto
```

## Notas
- La extracción de datos y precisión de la API dependen de la disponibilidad de información en el portal y la base de datos de Google Maps.
- Asegúrate de no exceder los límites de solicitudes gratuitas de la API de Google.


