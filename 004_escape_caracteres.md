# Escape de caracteres

El **escape de caracteres** es una técnica esencial para decirle al intérprete o compilador que un carácter que normalmente tiene un significado especial (como las comillas o el signo de dólar) debe tratarse como un carácter literal dentro de una cadena.

---

## Escape de Caracteres

| Lenguaje | Carácter de Escape Principal | Ejemplo de Escape (Comilla Doble) | Explicación |
| :--- | :--- | :--- | :--- |
| **PowerShell** | Backtick (\`) | `"Esto es una \"cita\"."` o ```"Esto es una `"cita`"."``` | Usa la **comilla invertida** (``` ` ```) o la sintaxis de duplicación de comillas dentro de comillas simples. |
| **Bash** | Barra invertida (\\) | `"La variable es \$nombre."` | La **barra invertida** `\` anula el significado especial del siguiente carácter. |
| **Python** | Barra invertida (\\) | `"Dijo: \"Hola\""` | La **barra invertida** `\` es el estándar de muchos lenguajes, útil para comillas y saltos de línea. |
| **C\#** | Barra invertida (\\) | `"El archivo está en C:\\ruta\\archivo.txt"` | La **barra invertida** `\` se usa para secuencias de escape estándar como `\n` (nueva línea) o `\t` (tabulación). |

---

## Escape de Caracteres en Detalle

### 1. PowerShell

PowerShell usa la **comilla invertida** o **backtick** (``` ` ```) como su carácter de escape estándar. Además, cuando trabajas con cadenas de comillas dobles, puedes escapar el signo de dólar (`$`) para evitar la interpolación.

| Objetivo | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Escapar Comilla Doble** | ```"Dijo: `"Hola`""``` | El **``` ` ```** anula el significado especial de la comilla doble. |
| **Escapar el Signo \$** | ```"El costo es de `$100"``` | Evita que PowerShell intente interpretar `$100` como una variable. |
| **Nueva Línea** | ```"Línea 1`nLínea 2"``` | Uso estándar para el salto de línea. |
| **Alternativa con Comillas Simples** | `'El costo es de $100'` | Las comillas simples tratan la cadena literalmente y no requieren escapar el `$` (pero tampoco interpolan). |

### 2. Bash (Shell Scripting)

En **Bash**, el carácter de escape principal es la **barra invertida** (`\`). Dentro de las comillas dobles, la barra invertida anula el significado especial de los caracteres como `$`, `"` o `\`.

| Objetivo | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Escapar Comilla Doble** | `echo "Dijo: \"Listo\""` | La `\` permite que la comilla doble se imprima como un carácter literal. |
| **Escapar el Signo \$** | `echo "El precio es \$20"` | Previene la **expansión de variables**, imprimiendo el `$` directamente. |
| **Nueva Línea** | `echo "Línea 1\nLínea 2"` | Aunque esto es común, para que Bash interprete `\n`, a menudo debes usar la bandera `-e` con `echo` (`echo -e`). |
| **Alternativa con Comillas Simples** | `echo 'Esto tiene un $'` | Las comillas simples previenen *casi toda* expansión o interpretación especial, tratando todo literalmente. |

### 3. Python

**Python** utiliza la **barra invertida** (`\`) como su carácter de escape, siguiendo el estándar de muchos lenguajes de programación.

| Objetivo | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Escapar Comilla Doble** | `print("Dijo: \"Vámonos\"")` | Útil cuando la cadena ya está definida con comillas dobles. |
| **Escapar Comilla Simple** | `print('Dijo: \'Genial\'')` | Útil cuando la cadena ya está definida con comillas simples. |
| **Barra Invertida Literal** | `print("Ruta: C:\\users\\doc")` | Se requiere doble barra invertida para imprimir una sola barra invertida (la primera escapa a la segunda). |
| **Cadenas "Raw" (Crudas)** | `print(r"Ruta: C:\users\doc")` | Al anteponer una `r` (cadena *raw* o cruda), Python ignora la mayoría de las secuencias de escape, muy útil para rutas de archivo o expresiones regulares. |

### 4. C\#

Al igual que Python y Bash, **C#** usa la **barra invertida** (`\`) para secuencias de escape estándar.

| Objetivo | Sintaxis | Documentación |
| :--- | :--- | :--- |
| **Escapar Comilla Doble** | `string mensaje = "El valor es: \"10\"";` | Permite incrustar comillas dobles dentro de una cadena de comillas dobles. |
| **Barra Invertida Literal** | `string ruta = "C:\\Archivos\\Documento.pdf";` | Se necesita doble barra invertida `\\` para representar una barra invertida literal en la cadena. |
| **Nueva Línea/Tabulación** | `Console.WriteLine("Columna1\tColumna2\nNueva Fila");` | Secuencias de escape tradicionales (`\t` para tabulación, `\n` para nueva línea). |
| **Cadenas Verbatim (`@`)** | `string ruta = @"C:\Archivos\Documento.pdf";` | El prefijo **`@`** (cadena *verbatim*) trata el contenido de la cadena literalmente, anulando la necesidad de doble barra invertida, ideal para rutas de archivo. |

---

> [!NOTE]
> Aunque todos cumplen la misma función, el carácter de escape varía (`\` vs. ``` ` ```) y cada lenguaje tiene su propia sintaxis alternativa (comillas simples en scripting, `r` en Python, `@` en C#) para simplificar la vida del programador en ciertos contextos.
