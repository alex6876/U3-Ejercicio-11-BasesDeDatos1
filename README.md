# Modelo Relacional de Bases de Datos 11



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de venta de entradas y gestión de conciertos, enfocado en el control de recintos, sectores, conciertos, clientes, compras y tickets.

---

## Estructura de Tablas y Atributos



### 1. Recinto



* **PK (Clave Primaria):** `id_cofigo_recinto`


* **Atributos:**
* `nombre`


* `dirección`


* `ciudad`


* `capacidad_maxima`





### 2. sector



* **PK (Clave Primaria):** `id_sector`


* **Atributos:**
* `nombre`


* `capacidad_maxima`


* `precio_base`




* **FK (Claves Foráneas):**
* `id_codigo_recinto` (asociado a la tabla Recinto)





### 3. Concierto



* **PK (Clave Primaria):** `id_concierto`


* **Atributos:**
* `titulo_gira`


* `fecha`


* `hora`




* **FK (Claves Foráneas):**
* `id_codigo_recinto` (asociado a la tabla Recinto)





### 4. Cliente



* **PK (Clave Primaria):** `id_dni`


* **Atributos:**
* `nombre`


* `apellido`


* `correo_electronico`


* `contraseña`





### 5. Compra



* **PK (Clave Primaria):** `id_compra`


* **Atributos:**
* `fecha`


* `hora`


* `monto_total`




* **FK (Claves Foráneas):**
* `id_dni` (asociado a la tabla Cliente)





### 6. Ticket



* **PK (Clave Primaria):** `id_ticket`


* **FK (Claves Foráneas):**
* `id_compra` (asociado a la tabla Compra)


* `id_sector` (asociado a la tabla sector)


* `id_concierto` (asociado a la tabla Concierto)


* `id_dni` (asociado a la tabla Cliente)





---

## Relaciones Principales



* **Recinto y Sector:** Un recinto cuenta con múltiples sectores diferenciados vinculados mediante `id_codigo_recinto`.


* **Recinto y Concierto:** Los conciertos se llevan a cabo en un recinto específico utilizando `id_codigo_recinto`.


* **Cliente y Compra:** Un cliente realiza una o varias operaciones de compra identificadas por su `id_dni`.


* **Compra, Sector, Concierto y Cliente (Ticket):** La tabla `Ticket` registra los detalles de cada entrada adquirida, asociándola con la compra realizada, el sector correspondiente, el concierto y el cliente respectivo mediante sus claves foráneas.
