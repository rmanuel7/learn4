# Bucles

Los bucles (`for`, `while`) nos permiten ejecutar un bloque de código repetidamente, lo cual es fundamental para procesar colecciones de datos o realizar tareas iterativas.

## Bucles (Loops)

### 1. PowerShell

PowerShell utiliza `ForEach-Object` para iterar pipelines, pero la sintaxis más común para un bucle dentro de un script es el **`foreach`** (para colecciones) y el **`while`** (para condiciones).

| Tipo de Bucle | Sintaxis de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Bucle `foreach` (Colección)** | `foreach ($elemento in $lista) { Write-Host $elemento }` | La variable iteradora (`$elemento`) se define al inicio. Útil para recorrer arrays, archivos, o resultados de comandos. |
| **Bucle `while` (Condición)** | `while ($contador -lt 5) { $contador++ }` | Ejecuta el bloque de código **mientras** la condición entre paréntesis sea verdadera. |
| **Bucle `for` (Índice)** | `for ($i=0; $i -lt 5; $i++) { ... }` | Sintaxis similar a C, con inicialización, condición y paso. |

### 2. Bash (Shell Scripting)

Bash tiene un bucle **`for`** muy flexible que se utiliza tanto para iterar sobre colecciones como para la sintaxis tipo C (usando `((...))`). El bucle **`while`** se usa comúnmente para procesar líneas de un archivo.

| Tipo de Bucle | Sintaxis de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Bucle `for` (Colección)** | `for fruta in manzana pera; do echo $fruta; done` | Itera sobre una lista de elementos separados por espacios. Las palabras clave `do` y `done` encierran el cuerpo. |
| **Bucle `for` (Índice)** | `for (( i=0; i<5; i++ )); do echo $i; done` | Usa doble paréntesis `(())` para el contexto aritmético. |
| **Bucle `while` (Condición)** | `while [[ $num -lt 10 ]]; do num=$((num + 1)); done` | Ejecuta el bucle **mientras** la condición entre corchetes dobles `[[...]]` sea verdadera. |

### 3. Python

Python se basa en el **`for`** para iterar sobre cualquier elemento iterable (listas, tuplas, rangos) y el **`while`** para la ejecución basada en condiciones.

| Tipo de Bucle | Sintaxis de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Bucle `for` (Iteración)** | `for item in mi_lista: print(item)` | El bucle **`for`** de Python está diseñado para iterar directamente sobre los elementos de una colección (es un bucle *for-each*). |
| **Bucle `for` (Rango)** | `for i in range(5): print(i)` | Se usa la función **`range()`** para generar una secuencia numérica para la indexación. |
| **Bucle `while` (Condición)** | `while sigue_activo: procesar_datos()` | La indentación define el cuerpo del bucle. |

### 4. C\#

**C#** es un lenguaje estructurado con sintaxis similar a C/C++ y Java. Ofrece el `for` tradicional (basado en índice), el `foreach` (basado en elemento) y el `while` (basado en condición).

| Tipo de Bucle | Sintaxis de Ejemplo | Documentación |
| :--- | :--- | :--- |
| **Bucle `foreach` (Colección)** | `foreach (string nombre in nombres) { Console.WriteLine(nombre); }` | Itera sobre cada elemento. Es el preferido para colecciones. |
| **Bucle `for` (Índice)** | `for (int i = 0; i < 10; i++) { Console.WriteLine(i); }` | Se usa para iterar un número fijo de veces o cuando se necesita acceso al índice. |
| **Bucle `while` (Condición)** | `while (contador < limite) { contador++; }` | La condición se evalúa antes de cada iteración. |
| **Bucle `do-while`** | `do { Console.WriteLine("Una vez"); } while (false);` | Garantiza que el código dentro del bucle se ejecute al menos una vez, ya que la condición se evalúa al final. |

---

## Conclusiones sobre Bucles

1.  **Iteración de Colecciones (For-each):** **Python** y **C#** (`foreach`) tienen el enfoque más limpio y moderno, iterando directamente sobre los elementos. **PowerShell** y **Bash** también lo permiten, aunque Bash tiene una sintaxis más cruda (separada por espacios).
2.  **Iteración Basada en Índice (For):** **PowerShell**, **Bash** (con `((...))`) y **C#** tienen la sintaxis tradicional de tres partes (inicialización; condición; paso).
3.  **Ejecución Condicional (While):** Todos los lenguajes usan la estructura **`while`** para ejecutar código basado en una condición booleana. C# agrega el `do-while` para la ejecución garantizada al menos una vez.
