#Manual de Usuario — La Reserva

##Universidad de Antioquia

###Algoritmia y Programación 

####Desarrolladores:

####Wbuanderley Ramírez Martínez · Disney Restrepo Enciso

---

###Tabla de Contenido

1. ¿Qué es La Reserva?

2. ¿Qué necesitas para usarlo?

3. ¿Cómo abrir el programa?

4. El menú principal

5. Registrar un usuario

6. Registrar un préstamo

7. Registrar una devolución

8. Consultar ítems con más de 30 días

9. Consultar artículos prestados

10. Panel de Administrador

11. Archivos que genera el sistema

12. Recomendaciones de uso

13. Créditos

---

#1. ¿Qué es La Reserva?

La Reserva es un sistema de gestión de préstamos entre amigos desarrollado en Python. Te permite registrar personas, prestar artículos, controlar devoluciones, generar facturas automáticas y consultar reportes, todo desde una consola fácil de usar.

Si alguna vez olvidaste a quién le prestaste algo, esto es para ti.

#2. ¿Qué necesitas para usarlo?

Antes de empezar, asegúrate de tener lo siguiente:

Python 3.10 o superior instalado en tu computador, o una cuenta activa en Google Colab (gratis, solo necesitas un correo Gmail).

La librería fpdf instalada. El mismo programa la instala automáticamente cuando lo ejecutas en Colab con este comando que ya viene incluido en el notebook:

  pip install fpdf

El archivo .ipynb descargado o en tu Google Drive.

####*Si vas a ejecutarlo en Colab, no tienes que instalar absolutamente nada en tu computador.

#3. ¿Cómo abrir el programa?

###Opción Recomendada — Google Colab

Ve a https://colab.research.google.com

Haz clic en "Subir" y sube el archivo LARESERVADEFINITIVOP.ipynb.

Una vez abierto, haz clic en "Entorno de ejecución" → "Ejecutar todo" (o usa Ctrl + F9).

El programa instalará las dependencias y arrancará solo. Verás el banner de La Reserva en la pantalla.

###Opción alternativa — Local (en tu computador)

Abre una terminal o símbolo del sistema.

Instala la dependencia si no la tienes:

bash   pip install fpdf

Ejecuta el notebook con Jupyter:

bash   jupyter notebook (archivo del código).ipynb

Ejecuta todas las celdas en orden desde la primera.

#4. El menú principal

Cuando el programa arranca, verás el siguiente menú:

          1. Registrar Usuario

          2. Registrar Prestamo

          3. Registrar Devolucion

          4. Consultar Items con mas de 30 dias

          5. Consultar Articulos Prestados

          6. Administrador

          7. Salir

Para elegir una opción, escribe el número correspondiente y presiona Enter.

Si escribes un número que no está en el menú, el sistema te avisará que la opción no es válida y te pedirá que intentes de nuevo.

#5. Registrar un usuario

Elige la opción 1 en el menú principal. El sistema te pedirá que ingreses los siguientes datos: nombre, apellido, número de documento, correo electronico y días a prestar.

Si ingresas un dato incorrecto, el programa te lo dirá y te pedirá que lo corrijas antes de continuar. No pierdes lo que ya escribiste.

####Ejemplo de registro exitoso:

  Nombre    : Laura

  Apellido  : Martinez

  Documento : 1023456789

  Correo    : laura@gmail.com

  Dias de prestamo (5 / 10 / 15 / 30): 15

  OK - Usuario 'Laura Martinez' registrado correctamente.

#6. Registrar un préstamo

Elige la opción 2 en el menú principal.

Pasos:

Escribe el número de documento de la persona que va a recibir el préstamo. Si no está registrada, el sistema te avisará que primero debes registrarla (opción 1).

El sistema te mostrará una lista de todos los ítems disponibles con su ID, nombre, categoría, estado y precio.

Escribe el ID del ítem que deseas prestar (por ejemplo: VID001, LIB002).

El sistema confirmará el préstamo y generará automáticamente un certificado PDF con todos los detalles.

*El certificado se guarda automáticamente en la carpeta /doc con un nombre como:

Certificado_Prestamo_Laura_Martinez_VID001_2026-06-05.pdf

*Un ítem ya prestado no aparece en la lista hasta que sea devuelto.

#7. Registrar una devolución

Elige la opción 3 en el menú principal.

Pasos:

Escribe el documento de la persona que va a devolver el ítem.

El sistema te mostrará una tabla con todos sus préstamos activos, incluyendo cuántos días lleva prestado cada ítem y si ya está vencido o a tiempo. Elige el ítem a devolver escribiendo su ID o su número en la lista.

El sistema registra la devolución y genera un certificado PDF de devolución.

*El certificado se guarda en /doc con un nombre como:

Certificado_Devolucion_Laura_Martinez_VID001_2026-06-05.pdf

*Si la persona no tiene préstamos activos, el sistema te avisará y no te dejará continuar.

#8. Consultar ítems con más de 30 días

Elige la opción 4 en el menú principal.

El sistema busca automáticamente todos los ítems que llevan más de 30 días prestados sin ser devueltos y los muestra en pantalla.

Si hay ítems vencidos, el sistema te preguntará:

  Desea generar facturas de venta? (s/n):

Si escribes s y presionas Enter, el sistema genera una factura de venta en formato .txt por cada usuario que tenga ítems vencidos.

La factura incluye:

Nombre y documento del cliente

Detalle de cada ítem no devuelto

Subtotal del valor de los ítems

Impuesto del 23% (impuesto por conchudez)

Total a pagar

*La factura se guarda en /doc con el nombre:

Laura_Martinez_VID001.txt

#9. Consultar artículos prestados

Elige la opción 5 en el menú principal.

Verás una tabla con todos los préstamos activos, ordenados de mayor a menor cantidad de días prestados. Cada fila muestra:

1. Días transcurridos

2. ID y nombre del ítem

3. Nombre del usuario

4. Fecha de inicio del préstamo

5. Una alerta *** ALERTA +20 dias *** si el ítem lleva 20 días o más

Al final de la lista verás un resumen con el total de préstamos activos y el promedio de días que llevan prestados.

#10. Panel de Administrador

Elige la opción 6 en el menú principal.

El sistema te pedirá usuario y contraseña. Las credenciales válidas son:

Usuarios: Disney, Wbuanderley, John. 

Contraseña: lareserva2026

Si escribes mal el usuario o la contraseña, el sistema te denegará el acceso.

Una vez dentro, verás el panel de administración con estas opciones:

          1. Total de prestamos registrados

          2. Total de items devueltos

          3. Total de ventas realizadas

          4. Total pago recaudado (ventas)

          5. Lista de usuarios

          6. Usuario con mayor y menor prestamos

          7. Generar reporte PDF

          8. Volver al menu principal

¿Qué hace cada opción?

1. Muestra cuántos préstamos hay en total (histórico), cuántos están activos y cuántos ya terminaron.

2. Muestra cuántos ítems fueron devueltos voluntariamente (sin necesidad de venta).

3. Muestra cuántos ítems fueron "vendidos" por superar los 30 días.

4. Calcula el dinero total recaudado por todas las ventas (precio del ítem + 23% de impuesto).

5. Lista completa de todos los usuarios registrados con su información.

6. Dice qué usuario tiene más préstamos registrados y cuál tiene menos.

7. Genera (o actualiza) el reporte PDF completo del sistema. Puedes usarlo cuantas veces quieras; cada vez que lo abres refleja el estado actual de La Reserva.

8. Regresa al menú principal.

#11. Archivos que genera el sistema

El programa crea y administra automáticamente estos archivos.

Los archivos se encuentran en las carpetas del Colab.

En Colab, las carpetas /data/ y /doc/ se crean dentro de /content/ automáticamente.

#12. Recomendaciones de uso

El inventario de 20 ítems ya viene cargado la primera vez que ejecutas el programa.

Si ejecutas el programa en Colab, descarga los archivos de /doc/ antes de cerrar la sesión, porque Colab borra los archivos temporales cuando la sesión termina. Esto incluye el reporte PDF del administrador.

Genera el reporte PDF cada vez que hagas cambios importantes (nuevos préstamos, devoluciones, ventas) para tener siempre una copia actualizada descargada.

No modifiques manualmente los archivos .csv de la carpeta /data/, ya que podrías dañar la información del sistema.

Si el programa muestra un error al generar el PDF, revisa que la librería fpdf esté instalada correctamente.

#13. Créditos

La Reserva

Proyecto académico — Algoritmia y Programación 2026-1

Universidad de Antioquia · Facultad de Ingeniería · Ingeniería Industrial

Equipo de desarrollo:

Wbuanderley Ramírez Martínez

Disney Restrepo Enciso

Docente: John Heider Dávila
