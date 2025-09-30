## El Casting (Conversión de Tipos) en Programación

El **casting** es la forma en que le dices al lenguaje que trate un valor de un tipo de dato como si fuera otro. Por ejemplo, convertir el texto `"123"` en el número `123`.

> [!NOTE]
> En este caso, veremos una gran diferencia entre los lenguajes de *scripting* (PowerShell, Bash, Python) y el lenguaje fuertemente tipado (C#).

### 1. PowerShell

PowerShell es flexible (tipado dinámico), pero te permite forzar la conversión de tipos usando corchetes `[]` antes de la variable o el valor. Esto se conoce como **casting explícito**.

| Tipo de Casting | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Conversión explícita** a Entero | `[int]$miNumero = "100"` | Convierte la cadena `"100"` en un entero y la asigna a la variable `$miNumero`. |
| **Conversión explícita** a Cadena | `[string]$piTexto = [string]$piNumero` | Convierte el valor de `$piNumero` (si fuera un número) a una cadena de texto. |
| **Conversión usando método** | `[convert]::ToInt32("25")` | Usa un método estático del *framework* para conversiones más complejas. |

### 2. Bash (Shell Scripting)

**Bash** solo maneja principalmente **cadenas de texto**. Para realizar operaciones matemáticas, necesitas usar comandos especiales que interpretan esas cadenas como números. El "casting" es casi siempre **implícito** o se hace a través de comandos auxiliares.

| Tipo de Conversión | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Aritmética (a número)** | `resultado=$(( 5 + $variable_texto ))` | El operador `$(( ... ))` fuerza a Bash a tratar las variables internas como números para la operación. |
| **Flotante (a decimal)** | `bc <<< "scale=2; 10/3"` | Se utiliza el comando **`bc`** (calculadora básica) para trabajar con números de punto flotante, ya que Bash no los maneja de forma nativa. |
| **Concatenación (a texto)** | `cadena_final="Texto: $resultado"` | Es la forma por defecto; todo se trata como texto. |

### 3. Python

**Python** es de tipado dinámico, pero fuertemente tipado, por lo que **el casting debe ser explícito**. Usas las funciones integradas que tienen el mismo nombre que el tipo de dato al que quieres convertir.

| Tipo de Casting | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **A Entero** | `entero = int("15")` | La función **`int()`** convierte la cadena `"15"` en el número entero `15`. |
| **A Cadena** | `texto = str(42.5)` | La función **`str()`** convierte el número `42.5` en la cadena `"42.5"`. |
| **A Flotante** | `decimal = float(10)` | La función **`float()`** convierte el entero `10` en el flotante `10.0`. |

### 4. C\#

**C#** ofrece varias formas de manejar el casting. Al ser fuertemente tipado, distingue entre conversiones **implícitas** (seguras) y **explícitas** (potencialmente riesgosas, requieren indicarlo).

| Tipo de Conversión | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Casting Implícito** | `double d = 10;` | El compilador lo hace automáticamente. Convertir un `int` (10) a un `double` es seguro porque `double` es más grande. |
| **Casting Explícito** | `int i = (int)10.5;` | Se usa la sintaxis `(Tipo)` antes del valor. Necesario al pasar de un tipo grande (`double`) a uno pequeño (`int`), lo que puede causar pérdida de datos (aquí se trunca a `10`). |
| **Conversión con la clase `Convert`** | `string s = Convert.ToString(i);` | La clase **`Convert`** proporciona métodos para conversiones comunes y maneja mejor los valores nulos y los errores. |
| **Parsing** | `int num = int.Parse("50");` | Usado específicamente para convertir **cadenas** a tipos numéricos (como `int.Parse()` o `double.Parse()`). |

---

> [!NOTE]
> PowerShell y Python usan funciones o sintaxis directas para el casting, Bash confía en comandos externos o la sintaxis aritmética, y C# nos obliga a ser muy conscientes de si la conversión es segura (implícita) o no (explícita).
