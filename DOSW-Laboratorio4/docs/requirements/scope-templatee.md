# 📄 Requerimientos del Sistema

## 1. Sistema

* Nombre del sistema: Bankify
* Objetivo: El sistema tiene como objetivo: la gestion a niveles basicos de cuentas bancarias en el tema que permita registrar, administrar y consultar cuentas de manera segura y validada, garantizando el cumplimiento de las reglas del negocio y facilitando la generación de reportes tributarios tanto para los clientes como para la DIAN.

## 2. Problema a resolver
Bankify no cuenta con un sistema centralizado que permita gestionar cuentas bancarias de forma validada y segura. No existe un mecanismo para registrar cuentas, consultar saldos, realizar depósitos controlados ni generar reportes tributarios para clientes y la DIAN. Esto genera riesgos de inconsistencia en la información, errores operativos y falta de control financiero.

## 3. Diagrama de Contexto

### 3.1 Diagrama

Relacionar imagen del diagrama de contexto realizado

### 3.2 Actores

<En el siguiente cuadro, mapee los actores o roles identificados del sistema>
<El primer rol es de ejemplo>

| Actor / Rol                        |          Descripción              |
|------------------------------------|:---------------------------------:|
| Usuario final                      | Cliente del sistema de Bankify    |
| operador/asesor                    | Encargado de crear, activar/desactivar y eliminar cuentas |
|supervisor                            Gestiona la informacion del cliente |
|Gerente financiero                    genera y envia reportes tributarios a la Dian |
|                                                                                    |
|                                                                                    |
|                                                                                    |
### 3.3 Sistemas externos

<En el siguiente cuadro, mapee los sistemas externos que interactúan con el sistema de Bankify>
<El primer sistema es de ejemplo>

| Sistema                            |                                    Descripción                                        |
|------------------------------------|:-------------------------------------------------------------------------------------:|
| Reportes                           | Sistema que genera los reportes tributarios de cada cliente del sistema de Bankify    |
|                                    |                                                                                       |
|DIAN                                | Entidad que recibe los reportes tributarios de las cuentas bancarias de usuarios      |
|                                    |                                                                                       |
|sistema de autenticacion            | servicio del programa que valida la identidad de quien desea entrar en la cuenta      |
|

## 4. Alcance del sistema
   
### 4.1 Dentro del sistema

Registrar cuentas bancarias con validación de reglas de negocio.

Crear, actualizar, activar y desactivar cuentas.

Consultar saldo de cuentas activas.

Realizar depósitos a cuentas bancarias.

### 4.2 Fuera del sistema

Procesar transferencias interbancarias entre diferentes entidades financieras.

Realizar inversiones, créditos o productos financieros avanzados.

Gestionar pagos electrónicos externos (PSE, tarjetas, pasarelas de pago).

Administrar infraestructura bancaria externa.

