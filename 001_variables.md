## Resumen de la Definición de Variables

| Lenguaje | Símbolo/Palabra Clave | Sintaxis de Ejemplo | Explicación Breve |
| :--- | :--- | :--- | :--- |
| **PowerShell** | `$` | `$miVariable = "Hola"` | Comienza con `$` y no requiere declaración de tipo. |
| **Bash** | `$` | `mi_variable="Mundo"` | No usa `$` para la asignación, solo para el uso/acceso. No requiere declaración de tipo. |
| **Python** | (Ninguno) | `mi_variable = 10` | No utiliza un símbolo especial y no requiere declaración de tipo (tipado dinámico). |
| **C#** | `var`, `string`, `int`, etc. | `int miVariable = 5;` | Requiere una palabra clave de tipo (`int`, `string`, `bool`, etc.) o `var` para inferencia. Termina con `;`. |

---

## Variables en Detalle

### 1. PowerShell

En **PowerShell**, todas las variables comienzan con el símbolo de dólar (`$`). No necesitas declarar explícitamente el tipo de dato, ya que PowerShell lo infiere automáticamente, aunque puedes forzarlo si lo deseas.

| Acción | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Asignar** un valor (una cadena de texto) | `$nombre = "Asistente"` | El símbolo `$` indica que es una variable. El tipo se infiere (en este caso, *string*). |
| **Asignar** un número | `$edad = 30` | El tipo se infiere como un número (*integer*). |
| **Usar** la variable | `Write-Host "Mi nombre es $nombre"` | Para acceder al valor, simplemente se usa el nombre de la variable. |

### 2. Bash (Shell Scripting)

En **Bash**, el proceso de asignación es muy sencillo: solo el nombre de la variable, un signo de igual y el valor. **Es crucial no tener espacios** a ambos lados del signo de igual (`=`). Además, solo necesitas usar el símbolo de dólar (`$`) **cuando quieres obtener o usar** el valor de la variable.

| Acción | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Asignar** un valor | `archivo="mi_log.txt"` | **No** se usa el `$` en la asignación. |
| **Usar** la variable | `echo "El archivo es: $archivo"` | El `$` se usa para *expandir* la variable y obtener su valor. |

### 3. Python

**Python** es un lenguaje de tipado dinámico, lo que significa que no se requiere ninguna palabra clave o símbolo para definir variables. Simplemente asignas un valor a un nombre.

| Acción | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Asignar** un valor | `contador = 0` | La variable `contador` ahora contiene el valor entero `0`. |
| **Asignar** una cadena | `mensaje = "Hola"` | No se requiere ningún símbolo especial. El tipo es *string*. |
| **Usar** la variable | `print(mensaje)` | La función `print()` muestra el valor de la variable. |

### 4. C\#

**C#** es un lenguaje de tipado estático, por lo que, tradicionalmente, debes especificar el **tipo de dato** de la variable al declararla. Toda sentencia debe terminar con un punto y coma (`;`). También puedes usar la palabra clave `var` para dejar que el compilador infiera el tipo (lo que se conoce como tipado implícito).

| Acción | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Asignar** un entero (Tipado explícito) | `int numeroIntentos = 3;` | Se especifica el tipo **`int`** (entero). |
| **Asignar** una cadena (Tipado explícito) | `string nombreUsuario = "coder";` | Se especifica el tipo **`string`** (cadena de texto). |
| **Asignar** usando inferencia (Tipado implícito) | `var esActivo = true;` | La palabra clave **`var`** permite al compilador determinar que el tipo es *bool* (booleano). |
