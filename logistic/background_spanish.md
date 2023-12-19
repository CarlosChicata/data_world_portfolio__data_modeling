# Projecto: modelamiento de empresa de logistica "Chicatita"

## Proposito
En este proyecto buscamos mostrar como lograr diferentes formas de modelar datos para un sistema de logistica con un enfoque de sistema de analisis de datos para la empresa para sus componentes:

- Mercado de datos o data mart.
- Almacen de datos o data warehouse. (principalmente)
- Almacen de datos operativos o Operational data store (ODS)

Hay diferentes tipos de modelos de datos para cada uno de los componentes; por lo que podria ser interesante como aplicarlos al caso de logistica y dar algunas observaciones y comentarios con relación a la arquitectura de datos y canalización de datos para cada uno.

## Contexto

### Historia ficticia

Una empresa camaneja llamada "chicatita" que se encarga de enviar paquetes entre personas y empresas. Actualmente se opera en 3 paises en las siguientes area:

| Pais | Region | Formato |
|------|--------|---------|
| Perú | Arequipa, Lima, Cusco, Trujillo | B2C, C2C y B2B |
| Colombia | Cali, Bogota y Cartagena de indias | C2C, B2C y B2B |
| Chile | Santiago de chile, Valparaíso y La serena  | B2C y C2C |
| Argentina | Buenos Aires provincia, Ciudad de buenos Aires, Cordoba  | C2C y B2C |

Actualmente da un grupo de servicios para sus usuarios de la siguiente forma.

| Servicio | Descripcion | Formato | Duración | ¿Hay Recojo? | ¿Hay devolución? |
|----------|-------------|---------|----------|--------------|------------------|
| Envio    | Envio de paquetes ligeros dentro de una región | C2C y B2C | Entre 90 minutos a 48 horas | Si | Si |
| Mudanza  | Envio de paquetes pesados dentro de un región | B2B y C2C | Entre 2 horas a 96 horas | Si | No |
| Transferencia | Envio de paquetes pesados entre regiones | B2B y B2C | Entre 5 horas a 168 horas | Si | No |

En el caso del servicio "Envio", hay subservicios dentro del mismo que se puede utilizar:

| Subservicio | Descripcion | Hay recojo | Hay almacenamiento temporal | 
|-------------|-------------|------------|-----------------------------|
| Express | Entregar pedidos en menos de 90 minutos posterior a la creación. | Si | No |
| Regular | Entregado dentro de entre 90 minutos a 18 horas posterior a la creación. | Si | No |
| Next | Entregado dentro de las siguientes 24 horas posterior a la creación. | Si | Si |
| Next 2 | Entregado dentro de las siguientes 48 horas posterior a la creación. | Si | Si |


## Estructura del proyecto

## Version
