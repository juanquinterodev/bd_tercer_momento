# bd_tercer_momento
# Proyecto Base de Datos - Tienda de Celulares

## Descripción General

Este proyecto consiste en el desarrollo de una base de datos para la gestión de una tienda de celulares. La base de datos permite administrar clientes, marcas, celulares, ventas y detalle de ventas, facilitando el control de inventario y el registro de compras realizadas por los clientes.

El sistema fue desarrollado utilizando SQL Server y contiene estructuras DDL, inserción de datos DML, procedimientos almacenados, vistas y consultas relacionales.

---

# Motor de Base de Datos

* Motor utilizado: SQL Server
* Lenguaje: SQL
* Tipo de sistema: Base de datos relacional

---

# Cantidad de Tablas

La base de datos contiene las siguientes tablas:

1. clientes
2. marcas
3. celulares
4. ventas
5. detalle_ventas

Total: 5 tablas principales.

---

# Estructura de la Base de Datos

## Tabla: clientes

Almacena la información de los clientes registrados en el sistema.

| Campo      | Tipo de dato | Descripción                     |
| ---------- | ------------ | ------------------------------- |
| id_cliente | INT          | Identificador único del cliente |
| nombre     | VARCHAR(100) | Nombre del cliente              |
| email      | VARCHAR(100) | Correo electrónico              |
| telefono   | VARCHAR(20)  | Número telefónico               |
| direccion  | VARCHAR(150) | Dirección del cliente           |

---

## Tabla: marcas

Almacena las marcas de celulares disponibles.

| Campo    | Tipo de dato | Descripción               |
| -------- | ------------ | ------------------------- |
| id_marca | INT          | Identificador de la marca |
| nombre   | VARCHAR(50)  | Nombre de la marca        |

---

## Tabla: celulares

Contiene la información de los celulares disponibles para la venta.

| Campo          | Tipo de dato  | Descripción               |
| -------------- | ------------- | ------------------------- |
| id_celular     | INT           | Identificador del celular |
| modelo         | VARCHAR(100)  | Modelo del celular        |
| precio         | DECIMAL(10,2) | Precio del equipo         |
| stock          | INT           | Cantidad disponible       |
| id_marca       | INT           | Marca relacionada         |
| garantia_meses | INT           | Meses de garantía         |

---

## Tabla: ventas

Registra las ventas realizadas a los clientes.

| Campo      | Tipo de dato  | Descripción                   |
| ---------- | ------------- | ----------------------------- |
| id_venta   | INT           | Identificador de la venta     |
| fecha      | DATE          | Fecha de la venta             |
| total      | DECIMAL(10,2) | Valor total de la venta       |
| id_cliente | INT           | Cliente que realizó la compra |

---

## Tabla: detalle_ventas

Almacena el detalle de cada venta realizada.

| Campo      | Tipo de dato  | Descripción               |
| ---------- | ------------- | ------------------------- |
| id_detalle | INT           | Identificador del detalle |
| cantidad   | INT           | Cantidad vendida          |
| subtotal   | DECIMAL(10,2) | Valor subtotal            |
| id_venta   | INT           | Venta relacionada         |
| id_celular | INT           | Celular vendido           |

---

# Relaciones de la Base de Datos

Las relaciones implementadas en la base de datos son las siguientes:

* Un cliente puede realizar muchas ventas.
* Una venta pertenece a un solo cliente.
* Una marca puede tener muchos celulares.
* Un celular pertenece a una sola marca.
* Una venta puede contener varios celulares.
* El detalle de ventas permite relacionar las ventas con los celulares vendidos.

Estas relaciones se implementaron mediante llaves foráneas para garantizar la integridad referencial de los datos.

---

# Funcionalidades Implementadas

## Inserción de Datos

Se implementaron instrucciones INSERT INTO para registrar:

* Clientes
* Marcas
* Celulares
* Ventas
* Detalles de ventas

---

## Modificación de Estructura

Se utilizaron instrucciones ALTER TABLE para modificar la estructura de la base de datos agregando nuevos campos:

* direccion en la tabla clientes
* garantia_meses en la tabla celulares

---

## Actualización de Información

Se implementaron instrucciones UPDATE para:

* Modificar el stock de celulares
* Actualizar direcciones de clientes

---

# Procedimientos Almacenados

## Procedimiento: sp_ventas_cliente

Permite consultar las ventas realizadas por un cliente específico utilizando un parámetro de entrada y devuelve la cantidad total de ventas mediante un parámetro OUTPUT.

### Funcionalidades:

* Consulta de ventas por cliente
* Conteo de ventas realizadas
* Uso de parámetros de entrada y salida

---

## Procedimiento: sp_registrar_venta

Permite registrar una nueva venta de manera automática.

### Funcionalidades:

* Registro de venta
* Registro del detalle de venta
* Cálculo automático del subtotal
* Descuento automático del stock
* Generación automática del ID de venta
* Uso de parámetros OUTPUT

---

# Vista Implementada

## vista_ventas_clientes

La vista permite consultar información consolidada de clientes y ventas para facilitar reportes y consultas administrativas.

---


Las vistas permiten simplificar la presentación de datos dentro de las interfaces gráficas.

---

# Conclusiones


El sistema permite administrar eficientemente la información de una tienda de celulares y servir como base para futuras mejoras del proyecto.
