Sistema de Gestión Académica "NEXUS" 🎓
Este proyecto es una aplicación de consola nativa para Windows desarrollada en C++. Funciona como una interfaz robusta para una base de datos MySQL, permitiendo la gestión integral de alumnos, seguimiento de calificaciones y actualizaciones automáticas de estado.

🚀 Características Detalladas
Buscador Individual: Recupera la ficha técnica completa de un alumno (Nombre, contacto, promedio y estado) mediante su ID único desde la base de datos.

Cuadro de Honor (Ranking): Genera un reporte dinámico con los 5 mejores promedios de la institución utilizando filtros de ordenamiento SQL.

Filtro de Rendimiento Binario:

Aprobados: Estudiantes con nota mayor o igual a 5.

Reprobados: Listado automático de estudiantes con nota menor a 5.

Gestión de Datos (CRUD):

Modificación de Calificaciones: Al actualizar una nota, el sistema recalcula el estado instantáneamente en la base de datos.

Actualización de Contacto: Permite modificar el número de celular del alumno de forma directa.

🛠️ Requisitos del Sistema (Solo Windows)
Para que este proyecto funcione en tu entorno local, necesitas tener instalado:

Compilador: MinGW-w64 (g++) configurado correctamente en el PATH del sistema.

Servidor de Base de Datos: MySQL Server 8.0 instalado y activo.

Librería de Enlace: API de C para MySQL (incluida en la instalación de MySQL Server).

📦 1. Configuración de Credenciales (Seguridad Local)
Por motivos de seguridad y cumpliendo con las buenas prácticas de ingeniería, las credenciales de acceso a la base de datos están ignoradas por el repositorio (vía .gitignore).

Debes crear manualmente el archivo de cabecera en la raíz del proyecto para permitir la conexión:

Crea un archivo llamado db_config.h.

Pega el siguiente bloque de código ajustando tus datos personales:

C++
#ifndef DB_CONFIG_H
#define DB_CONFIG_H

#define DB_HOST "127.0.0.1"
#define DB_USER "root"          // Tu usuario de MySQL
#define DB_PASS "tu_password"   // Tu contraseña personal de MySQL
#define DB_NAME "sistema"

#endif
⚙️ 2. Instalación y Preparación del Entorno
Paso A: Preparación de la Base de Datos
Antes de ejecutar el programa, la estructura de datos debe existir en tu servidor local:

Abre MySQL Workbench.

Carga el archivo NEXUS.sql incluido en este repositorio.

Ejecuta el script completo para crear la base de datos sistema, la tabla alumnos y cargar los datos iniciales.

Paso B: El Driver de Comunicación (DLL)
C++ necesita un "puente" físico para hablar con MySQL en Windows.

Dirígete a la carpeta de instalación de tu MySQL (usualmente C:\Program Files\MySQL\MySQL Server 8.0\lib).

Localiza el archivo llamado libmysql.dll.

Cópialo y pégalo en la carpeta donde tienes tu código fuente (main.cpp). Sin este archivo, el ejecutable dará un error de sistema al intentar abrirse.

🖥️ 3. Proceso de Compilación y Ejecución
La compilación en Windows requiere enlazar las librerías externas de MySQL. Usa la terminal de VS Code o el CMD con el siguiente comando:

Comando de Compilación (Vinculación Dinámica):
PowerShell
g++ main.cpp -o main.exe -I"C:/Program Files/MySQL/MySQL Server 8.0/include" -L"C:/Program Files/MySQL/MySQL Server 8.0/lib" -lmysql
-I: Indica dónde están los manuales de funciones (include).

-L: Indica dónde están los componentes físicos (lib).

-lmysql: Activa específicamente el conector de MySQL.

Comando de Ejecución:
Una vez que veas el archivo main.exe en tu carpeta, lánzalo con:

PowerShell
.\main.exe
📂 Estructura del Repositorio
main.cpp: Código fuente principal con la lógica de control.

NEXUS.sql: Script de base de datos para despliegue rápido.

.gitignore: Filtro de seguridad para evitar subida de binarios y contraseñas.

libmysql.dll: Conector necesario para la ejecución.

README.md: Documentación completa del proyecto.
