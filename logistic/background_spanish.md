# Projecto: modelamiento de empresa de logistica "Chicatita"

## Proposito
En este proyecto buscamos mostrar como lograr diferentes formas de modelar datos para un sistema de logistica con un enfoque de sistema de analisis de datos para la empresa para sus componentes:

- Mercado de datos o data mart.
- Almacen de datos o data warehouse. (principalmente)
- Almacen de datos operativos o Operational data store (ODS)

Hay diferentes tipos de modelos de datos para cada uno de los componentes; por lo que podria ser interesante como aplicarlos al caso de logistica y dar algunas observaciones y comentarios con relación a la arquitectura de datos y canalización de datos para cada uno.

## Contexto

### Servicios y contexto

Una empresa camaneja llamada "chicatita" que se encarga de enviar paquetes entre personas y empresas. Actualmente se opera en 3 paises en las siguientes area:

| Pais | Region | Formato |
|------|--------|---------|
| Perú | Arequipa, Lima, Cusco, Trujillo | B2C, C2C y B2B |
| Colombia | Cali, Bogota y Cartagena de indias | C2C, B2C y B2B |
| Chile | Santiago de chile, Valparaíso y La serena  | B2C y C2C |
| Argentina | Buenos Aires provincia, Ciudad de buenos Aires, Cordoba  | C2C y B2C |

Actualmente da un grupo de servicios para sus usuarios de la siguiente forma.

| Servicio | Descripcion | Formato | Duración | ¿Hay Recojo? | ¿Hay devolución? | Tipo de vehiculo |
|----------|-------------|---------|----------|--------------|------------------|------------------|
| Envio    | Envio de paquetes ligeros dentro de una región | C2C y B2C | Entre 90 minutos a 48 horas | Si | Si | Auto, van, moto, bicicleta |
| Mudanza  | Envio de paquetes pesados dentro de un región | B2B y C2C | Entre 2 horas a 96 horas | Si | No | Van, Camión |
| Transferencia | Envio de paquetes pesados entre regiones | B2B y B2C | Entre 5 horas a 168 horas | Si | No | Van, Camión |

En el caso del servicio "Envio", hay subservicios dentro del mismo que se puede utilizar:

| Subservicio | Descripcion | Hay recojo | Hay almacenamiento temporal | Tipo de vehiculo |
|-------------|-------------|------------|-----------------------------|------------------|
| Express | Entregar pedidos en menos de 90 minutos posterior a la creación. | Si | No | Moto y bicicleta |
| Regular | Entregado dentro de entre 90 minutos a 18 horas posterior a la creación. | Si | No | Auto, bicicleta, auto, van|
| Next | Entregado dentro de las siguientes 24 horas posterior a la creación. | Si | Si | Auto, van, moto, bicicleta |
| Next 2 | Entregado dentro de las siguientes 48 horas posterior a la creación. | Si | Si | Auto, van, moto, bicicleta |

### Proceso

Hay varias formas para enviar una solicitud para utilizar nuestros servicios:

- Integración via Webhook
- Landing page.
- Telefono.

Cuando recibimos la solicitud, esta puede pasar por un flujo de estados:

<imagen>

1.  _**Creado**_: Se registro la solicitud.
2.  _**Validando**_: Se debe validar la solicitud. Solo aplica para landing page y telefono.
3.  _**Validado**_: La solicitud es valida para operar.
4.  _**Llendo a almacen**_: La solicitud se lleva hacia el almacen.
5.  _**Saliendo de almacen**_: La solicitud sale del almacen.
6.  _**Entregando**_: La solicitud se esta llendo a entregar al usuario. 
7.  _**Entregado**_: La solicitud se entrego al usuario.
8.  _**Recogiendo**_: La solicitud se esta llendo a recoger al propietario.
9.  _**Recogido**_: La solicitud se recogio del usuario y esta en poder del conductor.
10. _**Devolviendo**_: Regresando la solicitud al propietario. Solo Aplica para logistica inversa.
11. _**Devuelto**_: Se entrego la solicitud al propietario. Solo Aplica para logistica inversa.
12. _**Retornando**_: Se regresa la solicitud a almacen.
13. _**Retorno**_: La solicitud esta en el almacen y no esta con el conductor.
14. _**Perdido**_: Se perdio la solicitud dentro del almacen.
15. _**Cancelado**_: Se cancelo la solicitud.
16. _**Robado**_: Se lo quitaron al conductor en su operación.

No todos los servicios utilizan todos los estados dentro de una solicitud:

| Estado | Aplica en Envio | Aplica en Mudanza | Aplica en Transferencia |
|--------|-----------------|-------------------|-------------------------|
| _**Creado**_ | x | x | x |
| _**Validando**_ | x | x | x |
| _**Validado**_ | x | x | x |
| _**Llendo a almacen**_ | x |  |  |
| _**Saliendo de almacen**_ | x |  |  |
| _**Entregando**_ | x | x | x |
| _**Entregado**_ | x | x | x |
| _**Recogiendo**_ | x | x | x |
| _**Recogido**_ | x | x | x |
| _**Devolviendo**_ | x |  |  |
| _**Devuelto**_ | x |  |  |
| _**Retornando**_ | x |  |  |
| _**Retorno**_ | x |  |  |
| _**Perdido**_ | x |  |  |
| _**Cancelado**_ | x | x | x |
| _**Robado**_ | x | x | x |

Las solicitudes de envio puede tener logistica inversa: trata que el usuario envia algo al propietario a cambio.

## Estructura del proyecto

## Version
