# Operaciones con cadenas

Las **funciones para trabajar con cadenas de texto** son el pan de cada día en casi cualquier proyecto.

---

## Funciones Comunes de Cadenas

| Operación | PowerShell | Bash | Python | C# |
| :--- | :--- | :--- | :--- | :--- |
| **Longitud** | `($cadena).Length` | `${#cadena}` | `len(cadena)` | `cadena.Length` |
| **Subcadena** | `$cadena.Substring(inicio, [largo])` | `${cadena:inicio:largo}` | `cadena[inicio:fin]` | `cadena.Substring(inicio, [largo])` |
| **Reemplazar** | `$cadena -replace "viejo", "nuevo"` | `${cadena/viejo/nuevo}` | `cadena.replace("viejo", "nuevo")` | `cadena.Replace("viejo", "nuevo")` |
| **Mayúsculas** | `$cadena.ToUpper()` | `echo $cadena \| tr '[:lower:]' '[:upper:]'` | `cadena.upper()` | `cadena.ToUpper()` |
| **Dividir (Split)** | `$cadena -split ","` | `IFS=',' read -ra arr <<< "$cadena"` | `cadena.split(',')` | `cadena.Split(',')` |

---

## Funciones de Cadena en Detalle

### 1. PowerShell

PowerShell, al estar construido sobre el **.NET Framework**, tiene acceso a la rica biblioteca de métodos de los objetos *string* de .NET. Esto lo hace muy potente y orientado a objetos.

| Tarea | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Comprobar si contiene** | `if ($cadena -like "*clave*") { ... }` | Utiliza operadores de comparación potentes, como `-like` para patrones simples. |
| **Recortar espacios** | `$cadena.Trim()` | Elimina espacios en blanco al principio y al final. También tienes `TrimStart()` y `TrimEnd()`. |
| **Formato** | `"Nombre: {0}, Edad: {1}" -f $nombre, $edad` | El operador `-f` es excelente para dar formato a cadenas de manera similar a C#. |

### 2. Bash (Shell Scripting)

Bash es más primitivo y se basa principalmente en la **expansión de parámetros** (sintaxis con `${}`) para operaciones básicas. Para tareas más complejas, a menudo requiere el uso de comandos externos como **`cut`**, **`sed`**, o **`awk`**.

| Tarea | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Eliminar sufijo** | `echo ${archivo%.txt}` | Elimina la coincidencia más corta del patrón desde el final de la cadena. |
| **Reemplazar la primera coincidencia** | `echo ${cadena/viejo/nuevo}` | Sintaxis de expansión de parámetros simple para reemplazar solo la primera aparición. |
| **Reemplazar todas las coincidencias** | `echo ${cadena//viejo/nuevo}` | Usar doble barra (`//`) reemplaza todas las apariciones. |
| **Dividir usando un comando** | `echo $cadena \| cut -d',' -f1` | El comando `cut` es común para dividir líneas basadas en un delimitador (`-d`). |

### 3. Python

**Python** trata las cadenas como **secuencias inmutables** y ofrece una gran cantidad de **métodos** de *string* integrados, además de ser muy hábil con las operaciones de **slicing** (rebanado) usando corchetes.

| Tarea | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Comprobar inicio/fin** | `cadena.startswith("HTTP")` | Métodos muy claros y legibles para verificar si una cadena comienza o termina con una subcadena. |
| **Buscar índice** | `cadena.find("error")` | Devuelve el índice de la primera aparición o `-1` si no se encuentra. |
| **Formato avanzado** | `'El valor es {:,.2f}'.format(1234.56)` | El método `format()` o las **f-strings** permiten un control de formato numérico y de texto muy detallado. |
| **Unir** | `", ".join(lista_de_palabras)` | El método `join` es la forma idiomática de concatenar una lista de cadenas con un separador específico. |

### 4. C\#

Al igual que PowerShell, **C#** (el lenguaje *base* de .NET) tiene un conjunto muy completo de métodos de clase para la manipulación de cadenas. Las cadenas también son **inmutables**, por lo que cada operación de modificación devuelve una nueva cadena.

| Tarea | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Comprobar si contiene** | `cadena.Contains("error")` | El método `Contains` devuelve un booleano (`true`/`false`). |
| **Convertir a Arreglo de Caracteres**| `char[] arr = cadena.ToCharArray();` | Convierte la cadena en un *array* (arreglo) de caracteres para manipulación a nivel de carácter. |
| **Recortar espacios** | `cadena.Trim()` | Recorta espacios en blanco, con variantes `TrimStart()` y `TrimEnd()`. |
| **Insertar** | `cadena.Insert(3, "X")` | Inserta una subcadena en una posición específica (índice). |

---

> [!NOTE]
> Python y C# tienen un enfoque muy orientado a **métodos de objeto** con nombres descriptivos. PowerShell combina métodos de objeto con operadores específicos (`-replace`, `-f`), y Bash utiliza su propia sintaxis de **expansión de parámetros** con comandos externos para lograr los mismos objetivos.
