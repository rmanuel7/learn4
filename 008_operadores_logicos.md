# Operadores logicos

Los **operadores booleanos y de comparación** son la base de la toma de decisiones y el control de flujo en la programación, ya que nos permiten evaluar si una condición es verdadera o falsa.


## Operadores Booleanos y de Comparación

### 1\. Operadores de Comparación

Los operadores de comparación evalúan la relación entre dos valores (por ejemplo, si uno es mayor que otro) y devuelven un valor **booleano** (`Verdadero` o `Falso`).

| Operación | PowerShell | Bash | Python | C\# |
| :--- | :--- | :--- | :--- | :--- |
| **Igual a** | `-eq` | `==` o `-eq` (en `[[...]]`) | `==` | `==` |
| **No es igual a** | `-ne` | `!=` o `-ne` (en `[[...]]`) | `!=` | `!=` |
| **Mayor que** | `-gt` | `>` o `-gt` (en `[[...]]`) | `>` | `>` |
| **Menor que** | `-lt` | `<` o `-lt` (en `[[...]]`) | `<` | `<` |
| **Mayor o igual que** | `-ge` | `>=` o `-ge` (en `[[...]]`) | `>=` | `>=` |
| **Menor o igual que** | `-le` | `<=` o `-le` (en `[[...]]`) | `<=` | `<=` |

#### Notas Clave sobre Comparación:

  * **PowerShell** utiliza operadores basados en guiones (`-eq`, `-lt`) para distinguir la comparación de la asignación.
  * **Bash** es confuso: dentro de `((...))` usa operadores matemáticos (`>`, `<`). Dentro de `[[...]]` o `[... ]` para cadenas usa `==` y para números usa operadores basados en guiones (`-gt`, `-lt`). Para simplificar, he listado los usados en la moderna sintaxis `[[...]]`.
  * **Python** y **C\#** usan los símbolos matemáticos estándar (`==`, `>`, `<=`), que son muy intuitivos.

-----

### 2\. Operadores Booleanos (Lógicos)

Los operadores lógicos combinan múltiples expresiones booleanas.

| Operación | Significado | PowerShell | Bash | Python | C\# |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Y (AND)** | Ambas condiciones son **Verdaderas**. | `-and` | `&&` | `and` | `&&` |
| **O (OR)** | Al menos una condición es **Verdadera**. | `-or` | `\|\|` | `or` | `\|\|` |
| **NO (NOT)** | Invierte el valor (de V a F, o F a V). | `!` o `-not` | `!` | `not` | `!` |

-----

## Ejemplos de Implementación

### PowerShell

PowerShell usa operadores de guion para la lógica, lo que los hace muy legibles en código:

```powershell
$esAdmin = $true
$tienePermiso = $false

# Condición: Ser Admin Y NO tener Permiso (ej. para advertir)
if ($esAdmin -and -not $tienePermiso) {
    Write-Host "¡Advertencia! Eres Admin pero no tienes permiso específico."
}
```

### Bash (Shell Scripting)

Bash usa la sintaxis C-style (`&&`, `||`) para la lógica dentro de una condición, que generalmente se encierra en corchetes dobles `[[...]]`.

```bash
ARCHIVO="config.ini"

# Condición: Si el nombre es 'config.ini' O el archivo existe
if [[ $ARCHIVO == "config.ini" || -f $ARCHIVO ]]; then
    echo "Condición cumplida."
fi
```

### Python

Python utiliza palabras clave claras y legibles (`and`, `or`, `not`) en sus estructuras condicionales.

```python
edad = 25
pais = "México"

# Condición: Ser mayor de 18 Y ser de México
if edad >= 18 and pais == "México":
    print("El usuario es mayor de edad en México.")
```

### C\#

C\# utiliza los símbolos dobles (`&&`, `||`) para operadores lógicos, lo que a menudo indica una evaluación de **cortocircuito** (si la primera parte es suficiente para determinar el resultado, no se evalúa la segunda).

```csharp
bool estaLogeado = true;
int intentos = 0;

// Condición: Estar logeado Y tener menos de 3 intentos
if (estaLogeado && intentos < 3)
{
    Console.WriteLine("Acceso permitido.");
}
```

-----

> [!NOTE]
> **Python** es el más expresivo con sus palabras clave, mientras que **C\#** y **Bash** usan la sintaxis C-style. **PowerShell** se distingue por el uso consistente de operadores basados en guion, tanto para la comparación como para la lógica.
