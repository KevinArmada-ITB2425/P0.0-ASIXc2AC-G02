El archivo `equipamientos_educativos.csv` es un archivo de texto plano delimitado por **tabuladores (`\t`)**.

A continuación, se detalla la estructura de datos (columnas y tipos de datos inferidos) basándose en las cabeceras y los valores de las primeras filas del archivo:

| Columna | Tipo de Dato Inferido | Descripción |
| :--- | :--- | :--- |
| **`register_id`** | Identificador (Texto/Entero) | ID único del registro del equipamiento. |
| **`name`** | Texto (`String`) | Nombre del equipamiento educativo. |
| **`institution_id`** | Identificador (Texto/Entero) | ID de la institución a la que pertenece (puede estar vacío). |
| **`institution_name`** | Texto (`String`) | Nombre de la institución. |
| **`created`** | Fecha/Hora (`Timestamp`) | Fecha de creación del registro. |
| **`modified`** | Fecha/Hora (`Timestamp`) | Fecha de la última modificación del registro. |
| **`addresses_roadtype_id`** | Identificador (Texto/Entero) | ID del tipo de vía (p. ej., calle, avenida). |
| **`addresses_roadtype_name`** | Texto (`String`) | Nombre del tipo de vía. |
| **`addresses_road_id`** | Identificador (Entero) | ID de la vía. |
| **`addresses_road_name`** | Texto (`String`) | Nombre de la vía. |
| **`addresses_start_street_number`** | Texto/Numérico (`String`) | Número inicial del edificio en la calle. |
| **`addresses_end_street_number`** | Texto/Numérico (`String`) | Número final del rango de la dirección (puede estar vacío). |
| **`addresses_neighborhood_id`** | Identificador (Entero) | ID del barrio. |
| **`addresses_neighborhood_name`** | Texto (`String`) | Nombre del barrio. |
| **`addresses_district_id`** | Identificador (Entero) | ID del distrito. |
| **`addresses_district_name`** | Texto (`String`) | Nombre del distrito. |
| **`addresses_zip_code`** | Código Postal (Entero) | Código postal de la dirección. |
| **`addresses_town`** | Texto (`String`) | Municipio. |
| **`addresses_main_address`** | Booleano (`True`/`False`) | Indica si es la dirección principal. |
| **`addresses_type`** | Texto (`String`) | Tipo de dirección (mayormente vacío). |
| **`values_id`** | Identificador (Entero) | ID de un valor asociado (p. ej., un teléfono). |
| **`values_attribute_id`** | Identificador (Entero) | ID de un atributo de valor (p. ej., código de teléfono). |
| **`values_category`** | Texto (`String`) | Categoría del valor (p. ej., "Telèfons"). |
| **`values_attribute_name`** | Texto (`String`) | Nombre del atributo (p. ej., "Tel."). |
| **`values_value`** | Texto (`String`) | Valor propiamente dicho (p. ej., el número de teléfono). |
| **`values_outstanding`** | Booleano (`True`/`False`) | Indica si el valor es destacado. |
| **`values_description`** | Texto (`String`) | Descripción adicional del valor (puede estar vacío). |
| **`secondary_filters_id`** | Identificador (Entero) | ID del filtro secundario (p. ej., tipo de enseñanza). |
| **`secondary_filters_name`** | Texto (`String`) | Nombre del filtro secundario (p. ej., "Educació secundària"). |
| **`secondary_filters_fullpath`** | Texto (`String`) | Ruta completa del filtro en la jerarquía. |
| **`secondary_filters_tree`** | Numérico (Entero) | Nivel o código del árbol de filtros. |
| **`secondary_filters_asia_id`** | Identificador (Texto/Numérico) | ID de clasificación ASIA del filtro. |
| **`geo_epgs_25831_x`** | Decimal (`Float`) | Coordenada X en el sistema de referencia EPSG:25831. |
| **`geo_epgs_25831_y`**** | Decimal (`Float`) | Coordenada Y en el sistema de referencia EPSG:25831. |
| **`geo_epgs_4326_lat`** | Decimal (`Float`) | Latitud en el sistema de referencia EPSG:4326. |
| **`geo_epgs_4326_lon`** | Decimal (`Float`) | Longitud en el sistema de referencia EPSG:4326. |
| **`estimated_dates`** | Texto (`String`) | Campo de fechas estimadas (mayormente vacío). |
| **`start_date`** | Fecha/Hora (`Timestamp`) | Fecha de inicio. |
| **`end_date`** | Fecha/Hora (`Timestamp`) | Fecha de finalización. |
| **`timetable`** | Texto (`String`) | Horario (mayormente vacío). |