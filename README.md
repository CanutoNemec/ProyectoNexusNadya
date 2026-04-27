```markdown
# 🎓 Sistema de Gestión Académica "NEXUS"

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

Este proyecto es una herramienta de consola diseñada para **Windows** que integra **C++** con **MySQL**. Permite la administración eficiente de registros estudiantiles, procesamiento de calificaciones y reportes de rendimiento académico en tiempo real.

---

## 🚀 Características del Sistema

| Módulo | Descripción |
| :--- | :--- |
| **🔍 Buscador** | Localización instantánea de alumnos por ID único. |
| **🏆 Cuadro de Honor** | Reporte automático del Top 5 de mejores promedios. |
| **📊 Filtros** | Clasificación binaria: **Aprobados** (≥ 5) y **Reprobados** (< 5). |
| **✏️ Editor CRUD** | Actualización de notas con recálculo de estado y cambio de contactos. |

---

## 🛠️ Requisitos Previos (Entorno Windows)

Para compilar y ejecutar este sistema, tu estación de trabajo debe contar con:
* **Compilador:** MinGW-w64 (g++) debidamente agregado al PATH del sistema.
* **Gestor de BD:** MySQL Server 8.0 local.
* **Conector:** MySQL Connector/C (API de C para el enlace de datos).

---

## 📦 1. Configuración de Seguridad (Credenciales)

Por norma de seguridad (buenas prácticas), los datos de acceso no se suben al repositorio. **Sigue estos pasos:**

1. Crea el archivo `db_config.h` en la carpeta raíz.
2. Inserta el siguiente código ajustando tus credenciales de MySQL:

```cpp
#ifndef DB_CONFIG_H
#define DB_CONFIG_H

#define DB_HOST "127.0.0.1"
#define DB_USER "root"          // Tu usuario
#define DB_PASS "tu_password"   // Tu contraseña real
#define DB_NAME "sistema"

#endif
```

---

## ⚙️ 2. Instalación y Puesta en Marcha

### Paso A: Despliegue de Base de Datos
* Abre **MySQL Workbench**.
* Ejecuta el archivo `NEXUS.sql` adjunto en este repo. Esto creará la arquitectura de tablas y los registros iniciales necesarios.

### Paso B: Integración del Driver (DLL)
C++ requiere un driver dinámico para comunicarse con MySQL en Windows:
1. Localiza el archivo `libmysql.dll` en: `C:\Program Files\MySQL\MySQL Server 8.0\lib`.
2. **Cópialo y pégalo** en la carpeta donde está tu `main.cpp`.
   > ⚠️ **Nota:** Sin este archivo, el programa lanzará un error de ejecución inmediatamente.

---

## 🖥️ 3. Compilación y Ejecución

Abre una terminal en el directorio del proyecto y ejecuta los siguientes comandos de ingeniería:

### 🔨 Compilación (Vinculación de Librerías)
```powershell
g++ main.cpp -o main.exe -I"C:/Program Files/MySQL/MySQL Server 8.0/include" -L"C:/Program Files/MySQL/MySQL Server 8.0/lib" -lmysql
```

### 🏃 Ejecución
```powershell
.\main.exe
```

---

## 📂 Estructura del Repositorio
```bash
├── main.cpp        # Lógica de control y queries SQL
├── NEXUS.sql       # Script de creación de la base de datos
├── .gitignore      # Exclusión de binarios y datos sensibles
├── libmysql.dll    # Driver de conexión para Windows
└── README.md       # Documentación técnica (este archivo)
```

---

