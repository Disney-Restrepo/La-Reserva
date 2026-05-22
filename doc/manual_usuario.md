# 📖 Manual de Usuario — La Reserva

**pf_Algoritmos** | Algoritmia y Programación 2026-1  
**Universidad de Antioquia** — Facultad de Ingeniería, Departamento de Ingeniería Industrial  
**Docente:** John Heider Dávila

---

## 📌 Tabla de contenido

1. [¿Qué es La Reserva?](#1--qué-es-la-reserva)
2. [Requisitos del sistema](#2--requisitos-del-sistema)
3. [Estructura del proyecto](#3--estructura-del-proyecto)
4. [Cómo ejecutar el programa](#4--cómo-ejecutar-el-programa)
5. [Menú principal](#5--menú-principal)
6. [Opción 1 — Registrar Usuario](#6--opción-1--registrar-usuario)
7. [Opción 2 — Registrar Préstamo](#7--opción-2--registrar-préstamo)
8. [Opción 3 — Registrar Devolución](#8--opción-3--registrar-devolución)
9. [Opción 4 — Consultar Ítems con más de 30 días](#9--opción-4--consultar-ítems-con-más-de-30-días)
10. [Opción 5 — Consultar Artículos Prestados](#10--opción-5--consultar-artículos-prestados)
11. [Opción 6 — Administrador](#11--opción-6--administrador)
12. [Inventario inicial de La Reserva](#12--inventario-inicial-de-la-reserva)
13. [Archivos generados por el sistema](#13--archivos-generados-por-el-sistema)
14. [Lógica difusa — Estado de los ítems](#14--lógica-difusa--estado-de-los-ítems)
15. [Preguntas frecuentes](#15--preguntas-frecuentes)

---

## 1. 🏪 ¿Qué es La Reserva?

**La Reserva** es un sistema de gestión de préstamos desarrollado en Python para consola. Fue creado para que **Michael Jackson Gamboa (MJ)** pueda controlar el préstamo de sus artículos personales a sus amigos, sin perder el registro de quién tiene qué y desde cuándo.

El sistema permite:
- Registrar usuarios (amigos de MJ) con validación de datos
- Registrar préstamos de ítems del inventario
- Registrar devoluciones y generar certificados automáticos
- Generar facturas de venta para préstamos de más de 30 días
- Consultar el estado general de todos los préstamos activos
- Acceder a un panel de administración con reportes completos

Toda la información se guarda automáticamente en archivos **CSV** dentro de la carpeta `data/`.

---

## 2. 💻 Requisitos del sistema

| Requisito | Detalle |
|-----------|---------|
| Sistema operativo | Windows 10 / 11, Linux o macOS |
| Python | Versión 3.8 o superior |
| Librerías externas | Ninguna — solo módulos estándar (`csv`, `datetime`, `os`, `re`, `sys`) |
| Terminal recomendada | **Windows Terminal** para ver el banner con colores |

---

## 3. 📁 Estructura del proyecto

```
La-Reserva/
│
├── src/
│   ├── main.py           → Programa principal (punto de entrada)
│   ├── clsUsuarios.py    → Clase de usuarios con validaciones
│   ├── clsPrestamo.py    → Clase de préstamos con cálculo de días
│   └── clsItem.py        → Clase de ítems con lógica difusa
│
├── data/                 → Generada automáticamente al ejecutar
│   ├── usuarios.csv      → Usuarios registrados
│   ├── items.csv         → Inventario de ítems
│   ├── prestamos.csv     → Historial de préstamos
│   └── admins.csv        → Credenciales de administradores
│
├── doc/
│   └── manual_usuario.md → Este manual
│
└── README.md             → Documentación general del repositorio
```

> ⚠️ La carpeta `data/` y sus archivos CSV se crean **automáticamente** la primera vez que se ejecuta el programa.

---

## 4. ▶️ Cómo ejecutar el programa

### Paso 1 — Verifica que Python esté instalado

Abre **PowerShell** y escribe:
```
python --version
```
Debe mostrar `Python 3.x.x`. Si no aparece, descarga Python desde [https://www.python.org/downloads/](https://www.python.org/downloads/) marcando la opción **"Add Python to PATH"**.

### Paso 2 — Abre la terminal en la carpeta del proyecto

1. Abre el **Explorador de archivos**
2. Navega hasta la carpeta `La-Reserva`
3. Haz clic en la barra de dirección, escribe `powershell` y presiona **Enter**

### Paso 3 — Ejecuta el programa

```powershell
python src/main.py
```

> Si `python` no funciona, prueba con `py src/main.py`

---

## 5. 🏠 Menú principal

Al iniciar verás el banner pixel-art de La Reserva y el siguiente menú:

```
--------------------------------------------------------------------------------
  Bienvenido a La Reserva
--------------------------------------------------------------------------------
          1. Registrar Usuario
          2. Registrar Prestamo
          3. Registrar Devolucion
          4. Consultar Items con mas de 30 dias
          5. Consultar Articulos Prestados
          6. Administrador
          7. Salir
--------------------------------------------------------------------------------
  Selecciona una opcion:
```

Escribe el número de la opción y presiona **Enter**.  
Para salir del programa usa la opción **7**.

---

## 6. 👤 Opción 1 — Registrar Usuario

Registra un nuevo amigo/usuario en el sistema.

### Campos y reglas de validación

| Campo | Reglas |
|-------|--------|
| **Nombre** | Mínimo 3 letras · No puede contener números |
| **Apellido** | Mínimo 3 letras · No puede contener números |
| **Documento** | Solo números · Entre 3 y 15 dígitos · No puede estar ya registrado |
| **Correo** | Debe contener `@` · Debe terminar en `.com` |
| **Días de préstamo** | Solo se aceptan: `5`, `10`, `15` o `30` |

### Ejemplo de registro exitoso

```
--------------------------------------------------------------------------------
  REGISTRAR USUARIO
--------------------------------------------------------------------------------
  Nombre    : Carlos
  Apellido  : Gomez
  Documento : 1045678901
  Correo    : carlos.gomez@gmail.com
  Dias de prestamo (5 / 10 / 15 / 30): 15

  OK - Usuario 'Carlos Gomez' registrado correctamente.
```

### Ejemplos de errores de validación

```
  Nombre    : Ca
  >> Error: Debe tener al menos 3 letras.

  Nombre    : Car3los
  >> Error: No puede contener numeros.

  Documento : abc123
  >> Error: Solo se permiten numeros.

  Correo    : correosinAT.com
  >> Error: Debe contener @ y terminar en .com

  Dias de prestamo: 20
  >> Error: Solo se permiten: 5, 10, 15 o 30 dias.
```

> El sistema repite la solicitud del campo hasta que el dato ingresado sea válido.  
> 💾 El usuario queda guardado en `data/usuarios.csv`

---

## 7. 🤝 Opción 2 — Registrar Préstamo

Registra el préstamo de un ítem del inventario a un usuario registrado.

### Paso a paso

**1.** El sistema solicita el documento del usuario:
```
  Documento del usuario: 1045678901
```

**2.** Si el usuario existe, muestra su información y el inventario disponible:
```
  Usuario: Carlos Gomez | Dias permitidos: 15

  ID         Nombre                 Categoria          Estado     Calidad       Precio
  --------------------------------------------------------------------------------------
  VID001     FIFA23                 Videojuegos        Excelente     100%    $250,000
  VID002     CallOfDuty             Videojuegos        Bueno          75%    $300,000
  VID003     MarioKart              Videojuegos        Regular        50%    $200,000
  LIB001     PythonBasico           Libros             Excelente     100%     $50,000
  HER001     TaladroBosch           Herramientas       Bueno          75%    $150,000
  ...
```

**3.** Se escribe el ID del ítem a prestar:
```
  Ingresa el ID del item a prestar: VID001

  OK - Prestamo registrado exitosamente:
       Item    : FIFA23 [VID001]
       Usuario : Carlos Gomez
       Fecha   : 2026-05-09  |  Vence en 15 dias
```

### Mensajes de error

| Situación | Mensaje |
|-----------|---------|
| Usuario no registrado | `>> Usuario NO encontrado. Por favor registrelo primero (opcion 1).` |
| ID de ítem inválido o ya prestado | `>> ID no encontrado o item no disponible.` |
| Sin ítems en inventario | `>> No hay items disponibles en este momento.` |

> 💾 El préstamo queda guardado en `data/prestamos.csv` y el ítem pasa a estado **Prestado** en `data/items.csv`

---

## 8. 📦 Opción 3 — Registrar Devolución

Registra la devolución de un ítem prestado y genera un **certificado de devolución**.

### Paso a paso

**1.** Se ingresa el documento del usuario:
```
  Documento del usuario: 1045678901
```

**2.** Se listan los préstamos activos del usuario:
```
  Prestamos activos de Carlos Gomez:
  #    ID         Item                   Desde        Dias
  ----------------------------------------------------------
  1    VID001     FIFA23                 2026-04-24     15
  2    LIB001     PythonBasico           2026-05-01      8
```

**3.** Se selecciona el ítem a devolver:
```
  Numero del item a devolver: 1

  OK - Devolucion registrada correctamente.
  Certificado generado: ..\doc\Carlos_Gomez_2026-05-09_VID001.txt
```

### Certificado generado

El archivo se guarda en `doc/` con el nombre:
```
NombreUsuario_ApellidoUsuario_FechaDevolucion_IDItem.txt
```

Ejemplo del contenido:
```
============================================================
         CERTIFICADO DE DEVOLUCION
           LA RESERVA | pf_Algoritmos
============================================================

Fecha devolucion   : 2026-05-09
Usuario            : Carlos Gomez
Documento          : 1045678901
Correo             : carlos.gomez@gmail.com

Item devuelto      : FIFA23
ID del item        : VID001
Categoria          : Videojuegos
Estado             : Excelente (100%)

Fecha prestamo     : 2026-04-24
Dias en prestamo   : 15

Se certifica que el item fue devuelto correctamente.
============================================================
```

### Mensajes de error

| Situación | Mensaje |
|-----------|---------|
| Usuario no existe | `>> Usuario no encontrado.` |
| Sin préstamos activos | `>> Este usuario no tiene prestamos activos.` |
| Selección inválida | `>> Seleccion invalida.` |

---

## 9. ⏰ Opción 4 — Consultar Ítems con más de 30 días

Detecta todos los ítems con más de 30 días prestados y genera facturas de venta automáticas.

### Visualización de ítems vencidos

```
  3 item(s) con mas de 30 dias:

  ID         Item                   Usuario                    Dias
  -----------------------------------------------------------------
  VID002     CallOfDuty             Pedro Ramirez                35
  LIB003     CienAnos               Maria Lopez                  42
  HER001     TaladroBosch           Juan Torres                  31
```

### Generación de factura de venta

```
  Desea generar facturas de venta? (s/n): s
```

El sistema cobra el precio original del ítem más el **impuesto por conchudez del 23%**:

```
============================================================
             FACTURA DE VENTA
         LA RESERVA | pf_Algoritmos
============================================================

Fecha              : 2026-05-09
Cliente            : Pedro Ramirez
Documento          : 1098765432
Correo             : pedro@gmail.com

MOTIVO DE VENTA:
El item fue prestado por mas de 30 dias sin ser devuelto.
Segun el acuerdo, el prestador debe comprarlo al precio de
adquisicion + impuesto por conchudez del 23%.

  Item                     ID              Precio
  ------------------------------------------------
  CallOfDuty               VID002      $300,000
  ------------------------------------------------
  Subtotal                             $300,000
  Impuesto conchudez (23%)              $69,000
  TOTAL                                $369,000
============================================================
```

La factura se guarda en `doc/` con el nombre:
```
NombreUsuario_ApellidoUsuario_IDItem.txt
```

> Después de generar la factura, el ítem vuelve a quedar **disponible** en el inventario.

---

## 10. 📊 Opción 5 — Consultar Artículos Prestados

Muestra todos los préstamos activos ordenados de **mayor a menor** por días prestados, con estadísticas generales.

### Visualización

```
  ARTICULOS PRESTADOS (ordenados mayor a menor por dias)
--------------------------------------------------------------------------------
   Dias  ID         Item                   Usuario                    Inicio
  --------------------------------------------------------------------------------
     42  LIB003     CienAnos               Maria Lopez                2026-03-28
     35  VID002     CallOfDuty             Pedro Ramirez              2026-04-04
     20  HER002     MartilloPro            Carlos Gomez               2026-04-19  *** ALERTA +20 dias ***
      8  LIB001     PythonBasico           Carlos Gomez               2026-05-01

  Total activos: 4  |  Promedio de dias prestado: 26.3
```

> ⚠️ Los préstamos con **20 o más días** se marcan con `*** ALERTA +20 dias ***` como recordatorio de solicitud de devolución.

---

## 11. 🔐 Opción 6 — Administrador

Acceso restringido al panel de reportes. Solo ingresan usuarios autorizados con su contraseña.

### Credenciales de acceso

| Usuario | Contraseña |
|---------|------------|
| `Disney` | `lareserva2026` |
| `Wbuanderley` | `lareserva2026` |
| `Kevin` | `lareserva2026` |
| `John` | `lareserva2026` |

### Pantalla de acceso

```
  Ingresa tus credenciales de administrador:

  Usuario    : Disney
  Contrasena : lareserva2026

  Bienvenido, Disney!
```

Si los datos son incorrectos:
```
  >> Acceso INVALIDO.
  >> El usuario o la contrasena son incorrectos.
```

### Panel de administración

```
  PANEL DE ADMINISTRACION  |  Admin: Disney
--------------------------------------------------------------------------------
          1. Total de prestamos registrados
          2. Total de items devueltos
          3. Total de ventas realizadas
          4. Total pago recaudado (ventas)
          5. Lista de usuarios
          6. Usuario con mayor y menor prestamos
          7. Volver al menu principal
```

### Descripción de reportes

| Opción | Reporte | Detalle |
|--------|---------|---------|
| **1** | Total de préstamos | Histórico total, activos y finalizados |
| **2** | Ítems devueltos | Cantidad de devoluciones voluntarias (sin venta) |
| **3** | Ventas realizadas | Cantidad de ítems vendidos por superar 30 días |
| **4** | Total pago recaudado | Suma total cobrada en ventas incluyendo impuesto 23% |
| **5** | Lista de usuarios | Tabla completa de todos los usuarios registrados |
| **6** | Mayor y menor préstamos | Usuario con más y menos préstamos históricos |
| **7** | Volver | Regresa al menú principal |

---

## 12. 🎮 Inventario inicial de La Reserva

El sistema carga automáticamente estos 20 ítems al ejecutarse por primera vez:

| ID | Nombre | Categoría | Estado | Calidad | Precio |
|----|--------|-----------|--------|---------|--------|
| VID001 | FIFA23 | Videojuegos | Excelente | 100% | $250,000 |
| VID002 | CallOfDuty | Videojuegos | Bueno | 75% | $300,000 |
| VID003 | MarioKart | Videojuegos | Regular | 50% | $200,000 |
| LIB001 | PythonBasico | Libros | Excelente | 100% | $50,000 |
| LIB002 | AlgebraLineal | Libros | Bueno | 75% | $60,000 |
| LIB003 | CienAnos | Libros | Regular | 50% | $45,000 |
| MUS001 | ThrillerMJ | Música y video | Excelente | 100% | $30,000 |
| MUS002 | ConciertoRock | Música y video | Bueno | 75% | $35,000 |
| MUS003 | PeliculaAvengers | Música y video | Excelente | 100% | $40,000 |
| HER001 | TaladroBosch | Herramientas | Bueno | 75% | $150,000 |
| HER002 | MartilloPro | Herramientas | Excelente | 100% | $30,000 |
| HER003 | LlaveInglesa | Herramientas | Regular | 50% | $25,000 |
| DIN001 | Prestamo100k | Dinero | Bueno | 75% | $100,000 |
| DIN002 | Prestamo200k | Dinero | Bueno | 75% | $200,000 |
| MIS001 | Cafetera | Misceláneo | Excelente | 100% | $120,000 |
| MIS002 | Ventilador | Misceláneo | Bueno | 75% | $90,000 |
| MIS003 | LaptopHP | Misceláneo | Excelente | 100% | $1,500,000 |
| MIS004 | MouseGamer | Misceláneo | Bueno | 75% | $80,000 |
| MIS005 | TecladoRGB | Misceláneo | Excelente | 100% | $120,000 |
| MIS006 | AudifonosSony | Misceláneo | Bueno | 75% | $200,000 |

---

## 13. 📄 Archivos generados por el sistema

| Archivo | Ubicación | Cuándo se genera |
|---------|-----------|-----------------|
| `usuarios.csv` | `data/` | Al registrar un usuario |
| `items.csv` | `data/` | Al iniciar el programa por primera vez |
| `prestamos.csv` | `data/` | Al registrar un préstamo |
| `admins.csv` | `data/` | Al iniciar el programa (se regenera siempre) |
| `Nombre_Apellido_Fecha_ID.txt` | `doc/` | Al registrar una devolución |
| `Nombre_Apellido_ID.txt` | `doc/` | Al generar una factura de venta |

---

## 14. 🧠 Lógica difusa — Estado de los ítems

El sistema usa **lógica difusa** para representar la calidad de cada ítem con un valor numérico entre 0.0 y 1.0, lo que permite una evaluación más precisa que una simple etiqueta de texto:

| Estado | Valor difuso | Interpretación |
|--------|-------------|----------------|
| Excelente | 1.00 → 100% | Ítem en perfectas condiciones, sin uso visible |
| Bueno | 0.75 → 75% | Ítem con uso mínimo, funciona perfectamente |
| Regular | 0.50 → 50% | Ítem con desgaste visible pero funcional |
| Malo | 0.25 → 25% | Ítem con daños considerables |
| Pésimo | 0.10 → 10% | Ítem casi inservible |

Este porcentaje se muestra en la columna **"Calidad"** al listar los ítems durante un préstamo.

---

## 15. ❓ Preguntas frecuentes

**¿Qué pasa si ingreso un documento que no existe al hacer un préstamo?**  
El sistema muestra `Usuario NO encontrado` y solicita registrarlo primero en la opción 1.

**¿Puedo prestar el mismo ítem a dos personas al mismo tiempo?**  
No. Un ítem solo puede estar prestado a una persona a la vez. Desaparece del inventario disponible hasta que sea devuelto o vendido.

**¿Qué pasa con los datos si cierro el programa?**  
Todo se guarda automáticamente en los archivos CSV de la carpeta `data/`. Al volver a abrir el programa, toda la información estará disponible.

**¿Qué pasa si un usuario lleva más de 30 días con un ítem?**  
La opción 4 detecta ese préstamo automáticamente y ofrece generar una factura de venta con el precio del ítem más el 23% de impuesto.

**¿Por qué el banner no muestra colores correctamente?**  
Usa **Windows Terminal** (disponible gratis en Microsoft Store). El CMD clásico no soporta colores ANSI de 24 bits.

**¿Cómo agrego más administradores?**  
Edita el archivo `main.py` en la función `cargar_admins()` y agrega una nueva línea con el usuario y contraseña deseados.

**¿Qué significa el aviso `*** ALERTA +20 dias ***`?**  
Es una notificación de recordatorio que indica que ese préstamo lleva 20 o más días activo, por lo que MJ debería solicitar la devolución pronto antes de que llegue a los 30 días y se genere una venta.

---

*Manual de usuario — Proyecto **La Reserva** | pf_Algoritmos*  
*Algoritmia y Programación 2026-1 — Universidad de Antioquia*
