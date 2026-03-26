# La-Reserva
Sistema para gestionar préstamos, devoluciones y ventas de objetos.
 
El programa permite registrar usuarios, administrar inventario de ítems, controlar préstamos y generar ventas automáticas cuando un préstamo supera el tiempo permitido.


# 1. Integrantes

- Disney Restrepo Enciso – disney.restrepo@udea.edu.co
- Wbuanderley Ramírez Martínez – Wbuanderley.ramirez@udea.edu.co
- Kevin David Pazos Agudelo – david.pazos@udea.edu.co

---

# 2. Vínculos académicos y descripción

## Disney Restrepo Enciso
Programa académico: Ingeniería Industrial.

Descripción:
Tengo 18 años, me considero una persona con buen liderazgo, soy amante de los perros, hago ejercicio en el gimnasio y en mi casa, me gusta leer novelas o libros que hacen una crítica a la sociedad, aunque soy una persona un poco tímida sé cómo actuar y hablar cuando estoy con grupos de personas, también soy una persona muy creativa en cuanto a actividades culturales, trabajos y regalos.

## Wbuanderley Ramírez Martínez
Programa académico: Ingeniería Industrial

Descripción:
Tengo 19 años, me gusta viajar, conocer cosas nuevas y compartir con mi familia.


## Kevin David Pazos Agudelo
Programa académico: Ingeniería Industrial

Descripción:
Tengo 21 años, me gusta el fútbol, trabajar, y al igual, compartir tiempo con mi familia.


---

# 3. Nombre del proyecto y detalles

## La Reserva

El proyecto “La Reserva” es un sistema creado para facilitar el préstamo de objetos entre usuarios y mantener un control organizado del inventario. Permite registrar a los usuarios, almacenar artículos y gestionar tanto los préstamos como las devoluciones. Además, se encarga de supervisar los plazos de préstamo establecidos. Si no se respeta la fecha de devolución, el sistema genera automáticamente una venta del objeto.


---

# 4. Licencia del software

Este proyecto utiliza la licencia **Creative Commons Zero v1.0 Universal (CC0)**.
Esta licencia permite que cualquier persona pueda usar, modificar, distribuir y reutilizar el software sin restricciones, incluso para fines comerciales. 
Al utilizar esta licencia, los autores del proyecto renunciamos a los derechos de autor en la medida permitida por la ley, dedicando el software al dominio público para que pueda ser utilizado libremente por cualquier usuario.

---

# 5. Reporte de visión

## Visión del software

Desarrollar un sistema sencillo y funcional que permita gestionar préstamos de objetos de manera organizada, facilitando el control de usuarios, inventario y tiempos de devolución.

## Objetivos

- Registrar usuarios con validaciones adecuadas.
- Administrar un inventario de ítems disponibles para préstamo.
- Controlar préstamos y devoluciones.
- Generar ventas automáticas cuando un préstamo exceda el tiempo permitido.

## Beneficios

- Organización de los préstamos.
- Control del inventario.
- Automatización de procesos.
- Registro claro de usuarios y transacciones.

# 6. Especificación de requisitos

## Requisitos funcionales

- El sistema debe permitir registrar usuarios con datos como nombre, apellido, documento, correo electrónico y tiempo de préstamo, validando que la información sea correcta.
- El sistema debe permitir registrar ítems a prestar, incluyendo nombre, categoría, precio, ID único y estado del objeto.
- El sistema debe permitir realizar préstamos únicamente a usuarios que ya estén registrados.
- El sistema debe validar que el usuario exista antes de permitir realizar un préstamo.
- El sistema debe permitir registrar devoluciones solo si existen préstamos activos.
- El sistema debe generar un certificado de devolución cuando un ítem sea devuelto correctamente.
- El sistema debe generar una factura de venta cuando un préstamo supere los 30 días.
- El sistema debe calcular el valor total de la venta incluyendo un recargo del 23%.
- El sistema debe permitir consultar el estado general de los préstamos.
- El sistema debe almacenar la información en archivos planos.
- El sistema debe permitir el acceso a un módulo administrador mediante usuario y contraseña.
- El sistema debe generar reportes como total de préstamos, devoluciones, ventas y estadísticas de usuarios.

## Requisitos no funcionales

- El sistema debe ser fácil de usar mediante un menú en consola claro.
- El sistema debe validar correctamente los datos ingresados por el usuario.
- El sistema debe ser rápido en la ejecución de las operaciones.
- El sistema debe ser confiable en el manejo de la información.
- El sistema debe ser seguro en el acceso al módulo administrador.
- El sistema debe ser compatible con Python.
- El sistema debe permitir la lectura y escritura de archivos correctamente.
- El sistema debe tener una estructura organizada que facilite su mantenimiento.
- El sistema debe permitir futuras mejoras sin afectar su funcionamiento.
- El sistema debe permitir exportar datos en formato CSV.

---

## 7. Plan de proyecto

### Actividades

Para el desarrollo del proyecto se definieron las siguientes actividades basadas en los requerimientos del trabajo:

- Organización del equipo y definición de roles
- Desarrollo de los puntos 1 al 7 (Entrega 1)
- Desarrollo completo del sistema en Python
- Implementación de funcionalidades (usuarios, préstamos, devoluciones, ventas)
- Pruebas del sistema
- Corrección de errores
- Documentación final (manual de usuario y código)
- Preparación de entrega final

---

### Cronograma (Diagrama de Gantt)

| Actividad / Entregable                     | S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 | S10 | S11 | S12 | S13 | S14 | S15 |
|--------------------------------------------|----|----|----|----|----|----|----|----|----|-----|-----|-----|-----|-----|-----|
| Organización del equipo                    | *  |    |    |    |    |    |    |    |    |     |     |     |     |     |     |
| Integrantes                                |    | *  |    |    |    |    |    |    |    |     |     |     |     |     |     |
| Vínculos académicos                        |    | *  |    |    |    |    |    |    |    |     |     |     |     |     |     |
| Nombre del proyecto                        |    | *  |    |    |    |    |    |    |    |     |     |     |     |     |     |
| Licencia                                   |    |    | *  |    |    |    |    |    |    |     |     |     |     |     |     |
| Visión                                     |    |    | *  |    |    |    |    |    |    |     |     |     |     |     |     |
| Requisitos                                 |    |    |    | *  |    |    |    |    |    |     |     |     |     |     |     |
| Plan de proyecto                           |    |    |    | *  |    |    |    |    |    |     |     |     |     |     |     |
| 🔵 ENTREGA 1                              |    |    |    |    |    |    |    | *  |    |     |     |     |     |     |     |
| Desarrollo del sistema en Python           |    |    |    |    | *  | *  | *  |    | *  |  *  |     |     |     |     |     |
| Funcionalidades (usuarios, préstamos, etc) |    |    |    |    |    | *  | *  |    | *  |  *  |     |     |     |     |     |
| Pruebas del sistema                        |    |    |    |    |    |    |    |    |    |  *  |  *  |     |     |     |     |
| Corrección de errores                      |    |    |    |    |    |    |    |    |    |     |  *  |  *  |     |     |     |
| Documentación (manual y código)            |    |    |    |    |    |    |    |    |    |     |     |  *  |  *  |     |     |
| Preparación entrega final                  |    |    |    |    |    |    |    |    |    |     |     |     |  *  |  *  |     |
| 🔴 ENTREGA FINAL (2)                       |    |    |    |    |    |    |    |    |    |     |     |     |     |     |  *  |

---

## Presupuesto

El proyecto se desarrolla como práctica académica, por lo que el pago se representa en tiempo de trabajo.

- Total de horas del proyecto: 50 horas
- Número de integrantes: 3

Distribución del tiempo:

- Disney Restrepo Enciso: 17 horas
- Wbuanderley Ramírez Martínez: 17 horas
- Kevin David Pazos Agudelo: 16 horas

