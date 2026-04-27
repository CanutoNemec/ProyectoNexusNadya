# Sistema de Gestión Académica "NEXUS"

Este proyecto es una aplicación de consola desarrollada en **C++** que actúa como interfaz para una base de datos **MySQL**. Permite gestionar la información de alumnos, visualizar rankings de rendimiento y actualizar datos en tiempo real.

## 🚀 Características
- **Buscador Individual**: Consulta la ficha completa de un alumno por su ID.
- **Cuadro de Honor**: Visualiza el Top 5 de los mejores promedios.
- **Filtro de Reprobados**: Lista automáticamente a los alumnos con nota menor a 5.
- **Actualización Dinámica**: 
  - Modificación de notas con cálculo de estado automático (Aprobado/Reprobado).
  - Actualización de números de contacto.

## 🛠️ Requisitos Técnicos
- **Compilador**: MinGW-w64 (g++)
- **Base de Datos**: MySQL Server 8.0
- **Conector**: MySQL Connector/C (libmysql)

## 📦 Configuración Local
Por motivos de seguridad, las credenciales de la base de datos no están incluidas en este repositorio. Para ejecutar el proyecto, debes crear un archivo llamado `db_config.h` en la raíz del proyecto con el siguiente formato:

```cpp
#ifndef DB_CONFIG_H
#define DB_CONFIG_H

#define DB_HOST "127.0.0.1"
#define DB_USER "tu_usuario"
#define DB_PASS "tu_password"
#define DB_NAME "sistema"

#endif
