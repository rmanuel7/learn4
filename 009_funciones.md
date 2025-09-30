# Funciones

Las **funciones** (o **métodos**, el término preferido en lenguajes orientados a objetos como C#) son esenciales para organizar el código en bloques reutilizables.

## Definición de Funciones o Métodos

| Lenguaje | Palabra Clave | Sintaxis de Definición | Explicación Breve |
| :--- | :--- | :--- | :--- |
| **PowerShell** | `function` | `function Get-Saludo { ... }` | Usa la palabra clave `function`, seguida del nombre (a menudo con verbos y sustantivos). |
| **Bash** | `function` o nombre simple | `function saludo { ... }` | Opcionalmente usa `function`. Los paréntesis `()` son clave. |
| **Python** | `def` | `def saludar(nombre): ...` | Usa `def` (de *define*) y la indentación define el cuerpo de la función. |
| **C\#** | Tipo de Retorno | `public int Sumar(int a, int b) { ... }` | Se requiere un **tipo de retorno** (`int`) y modificadores de acceso (`public`). |

---

## Funciones y Métodos en Detalle

### 1. PowerShell

En **PowerShell**, las funciones se definen con la palabra clave `function`. A menudo siguen un esquema de nombres de **verbo-sustantivo** (por ejemplo, `Get-Item`, `Set-Variable`) para mayor claridad y coherencia.

| Aspecto | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Definición Simple** | `function Mostrar-Hora { Write-Host (Get-Date) }` | No requiere paréntesis si no hay parámetros. El cuerpo va entre llaves `{}`. |
| **Con Parámetros** | `function Saludar { param($nombre) Write-Host "Hola, $nombre" }` | Los parámetros se definen dentro de un bloque `param()`. |
| **Llamada** | `Saludar -nombre "Coder"` | Se pueden usar los nombres de los parámetros con un guion (`-`). |
| **Retorno** | `function Duplicar { param($num) return $num * 2 }` | El valor de la última expresión no capturada se devuelve por defecto, pero se recomienda usar `return`. |

### 2. Bash (Shell Scripting)

En **Bash**, una función se define simplemente con su nombre seguido de paréntesis `()`. Los parámetros no se nombran en la definición; en su lugar, se acceden posicionalmente dentro del cuerpo de la función ( `$1` para el primer argumento, `$2` para el segundo, etc.).

| Aspecto | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Definición Simple** | `saludo() { echo "Hola mundo" }` | El uso de `()` seguido de llaves `{}` define la función. |
| **Con Parámetros** | `sumar() { resultado=$(($1 + $2)); echo $resultado; }` | `$1` y `$2` son los valores del primer y segundo argumento pasados a la función. |
| **Llamada** | `sumar 5 3` | Los argumentos se pasan separados por espacios. |
| **Retorno (Código de Salida)** | `retornar_codigo() { return 1; }` | `return` solo devuelve un **código de salida** (un número entre 0 y 255). Para devolver un valor, se usa `echo` y se captura la salida. |

### 3. Python

**Python** usa la palabra clave `def` y la indentación para definir el cuerpo de la función. Es muy legible y permite definir parámetros con valores por defecto.

| Aspecto | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Definición Simple** | `def mostrar_info(): print("Info")` | `def` seguido del nombre y paréntesis. Los dos puntos (`:`) indican el inicio del cuerpo. |
| **Con Parámetros** | `def saludar(nombre, mensaje="Hola"): print(f"{mensaje}, {nombre}")` | Los parámetros se nombran dentro de los paréntesis. Puedes asignarles valores por defecto. |
| **Llamada** | `saludar("Ana", "Buenos días")` | La llamada se hace usando el nombre de la función seguido de los argumentos entre paréntesis. |
| **Retorno** | `def multiplicar(a, b): return a * b` | La palabra clave `return` se usa para devolver un valor. Si no se usa `return`, la función devuelve implícitamente `None`. |

### 4. C\#

En **C#** (dentro de una clase), lo que definimos son **métodos**. La sintaxis es más formal, ya que debes especificar el **tipo de retorno** (o `void` si no devuelve nada) y el **modificador de acceso** (`public`, `private`, etc.).

| Aspecto | Código de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Definición Simple (sin retorno)** | `public void MostrarMensaje() { Console.WriteLine("Mensaje"); }` | `void` indica que el método no devuelve un valor. |
| **Con Parámetros y Retorno** | `private string ObtenerNombreCompleto(string nom, string ape)` | Se especifica el tipo de retorno (`string`) y el tipo de cada parámetro. |
| **Llamada (dentro de la misma clase)** | `ObtenerNombreCompleto("Javier", "Perez");` | Se llama al método. En C#, la llamada se hace sobre un objeto o estáticamente. |
| **Retorno** | `public int Restar(int a, int b) { return a - b; }` | Se debe usar `return` para devolver un valor que coincida con el tipo de retorno declarado. |

---

> [!NOTE]
> La principal diferencia radica en el sistema de tipos: **C#** exige la declaración de tipos de retorno y parámetros, mientras que **Python** y **PowerShell** son más flexibles. **Bash** es el más simple, manejando parámetros posicionalmente sin nombres formales.
