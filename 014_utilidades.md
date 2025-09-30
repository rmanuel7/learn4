## Utilidades Esenciales por Lenguaje

### 1. Peticiones HTTP (Web Requests)

Esta utilidad es crucial para interactuar con APIs y recursos web.

| Lenguaje | Función/Método Principal | Documentación |
| :--- | :--- | :--- |
| **PowerShell** | **`Invoke-RestMethod`** | Un *cmdlet* robusto que simplifica las llamadas REST (GET, POST, etc.) y automáticamente convierte JSON en objetos de PowerShell. |
| **Bash** | **`curl`** o **`wget`** (Comandos Externos) | Bash depende de ejecutar programas externos. `curl` es el estándar para enviar y recibir datos a través de protocolos web. |
| **Python** | **`requests`** (Librería Externa) | Aunque tiene librerías nativas (`urllib`), **`requests`** es el estándar de la industria. Ofrece una API simple y legible para todas las peticiones. |
| **C\#** | **`HttpClient`** (Clase .NET) | La clase estándar en .NET. Se usa para enviar peticiones y recibir respuestas, manejando asincronía y optimización de recursos. |

---

### 2. Manejo de Archivos (Filesystem)

Esto se refiere a la manipulación de archivos y directorios (crear, leer, escribir, mover, etc.).

| Lenguaje | Función/Método Principal | Documentación |
| :--- | :--- | :--- |
| **PowerShell** | **Cmdlets de Verbo-Sustantivo** | Utiliza comandos claros como **`Get-Content`** (leer), **`Set-Content`** (escribir), **`Move-Item`**, **`New-Item`**, etc. |
| **Bash** | **Comandos Nativos del SO** | Depende de utilidades de Unix/Linux: **`cat`** (leer), **`echo`** con `>` o `>>` (escribir), **`mkdir`** (crear dir), **`mv`** (mover), etc. |
| **Python** | **Módulo `os` / Funciones `open()`** | La función **`open()`** se usa para leer y escribir archivos. El módulo **`os`** y **`pathlib`** manejan directorios y rutas de manera multiplataforma. |
| **C\#** | **Clase `System.IO.File`** | La clase **`File`** proporciona métodos estáticos como `File.ReadAllText()`, `File.WriteAllText()`, y la clase **`Directory`** para carpetas. |

---

### 3. Variables de Entorno

Las variables de entorno se usan para configurar el comportamiento del *script* o programa fuera del código (útil para secretos, *paths*, etc.).

| Lenguaje | Acceso para Lectura | Acceso para Escritura/Modificación |
| :--- | :--- | :--- |
| **PowerShell** | **`$env:NombreVar`** | **`$env:NombreVar = "valor"`** (Solo persiste en la sesión actual o *script*). |
| **Bash** | **`$NombreVar`** (Con `export` para el *shell* actual) | **`export NombreVar="valor"`** (Crea la variable si no existe, o la modifica). |
| **Python** | **`os.environ['NombreVar']`** | **`os.environ['NombreVar'] = "valor"`** (Solo afecta al proceso actual). |
| **C\#** | **`Environment.GetEnvironmentVariable("NombreVar")`** | **`Environment.SetEnvironmentVariable("NombreVar", "valor")`** (Solo afecta al proceso actual). |

---

### Conclusiones sobre Utilidades

* **Scripting vs. POO:** **PowerShell** y **Bash** usan comandos específicos para cada tarea, aprovechando el *shell* (Bash con utilidades del SO y PowerShell con *cmdlets*). **Python** y **C#** usan **módulos/clases** (ej. `os.environ` y `System.IO.File`) que encapsulan la funcionalidad.
* **HTTP:** **`curl`** en Bash es una herramienta externa, mientras que los demás integran el soporte HTTP directamente en el lenguaje o su ecosistema (PowerShell, Python `requests`, C# `HttpClient`).
* **Variables de Entorno:** Todos los lenguajes permiten leer y escribir variables de entorno, pero la modificación **solo es efectiva para el proceso actual** y sus procesos hijos, no para la terminal que lo lanzó.
