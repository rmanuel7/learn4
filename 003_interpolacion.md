# Interpolación de cadenas

La **interpolación de cadenas** es la capacidad de incrustar expresiones (como el valor de una variable) directamente dentro de una cadena de texto, sin tener que usar operadores de concatenación (`+`) repetidamente.

-----

## Interpolación de Cadenas

| Lenguaje | Símbolo de Interpolación | Sintaxis de Ejemplo | Documentación |
| :--- | :--- | :--- | :--- |
| **PowerShell** | `$` (por defecto) | `"El valor es: $miVariable"` | Los valores de las variables se expanden automáticamente dentro de comillas dobles (`"`). |
| **Bash** | `$` (por defecto) | `"La ruta es: $RUTA_ACTUAL"` | Las variables se expanden automáticamente dentro de comillas dobles (`"`). |
| **Python** | `f` | `f"Hola, {nombre}"` | Se requiere el prefijo `f` (f-string) antes de la cadena y llaves `{}` para la expresión. |
| **C\#** | `$` | `$"La edad es {edad}"` | Se requiere el prefijo `$` antes de la cadena y llaves `{}` para la expresión. |

-----

## Interpolación en Detalle

### 1\. PowerShell

En **PowerShell**, la interpolación es el comportamiento predeterminado cuando se usan **comillas dobles** (`"`). Cualquier variable que comience con `$` será automáticamente reemplazada por su valor. Si usas comillas simples (`'`), la interpolación no ocurre (se trata como una cadena literal).

```powershell
$nombre = "Asistente"
$lenguaje = "PowerShell"

# Ejemplo de Interpolación (comillas dobles)
Write-Host "Hola $nombre, estás programando en $lenguaje."

# Salida: Hola Asistente, estás programando en PowerShell.

# Ejemplo SIN Interpolación (comillas simples)
Write-Host 'Hola $nombre, estás programando en $lenguaje.'

# Salida: Hola $nombre, estás programando en $lenguaje.
```

### 2\. Bash (Shell Scripting)

Similar a PowerShell, **Bash** realiza la interpolación (o **expansión de variables**) por defecto dentro de las **comillas dobles** (`"`).

```bash
NOMBRE="Coder"
ARCHIVOS_CONTADOS=10

# Ejemplo de Interpolación (comillas dobles)
echo "Hola $NOMBRE, encontré $ARCHIVOS_CONTADOS archivos."

# Salida: Hola Coder, encontré 10 archivos.

# Ejemplo usando sintaxis de expresión más compleja
echo "Resultado: $((ARCHIVOS_CONTADOS * 2))"

# Salida: Resultado: 20
```

### 3\. Python

**Python** ofrece las **f-strings** (cadenas con formato, introducidas en Python 3.6) como la forma moderna y preferida de interpolar. Debes prefijar la cadena con una `f` o una `F` y encerrar la variable o expresión entre llaves `{}`.

```python
nombre = "Asistente"
version = 3.10

# Ejemplo de F-string (Interpolación)
print(f"La versión actual es: {version}, hola {nombre}.")

# Salida: La versión actual es: 3.10, hola Asistente.

# Se pueden incluir expresiones dentro de las llaves
print(f"El doble de 5 es: {5 * 2}")

# Salida: El doble de 5 es: 10
```

### 4\. C\#

**C\#** también utiliza el prefijo de dólar (`$`) para indicar una **cadena interpolada** y usa llaves `{}` para incrustar las expresiones, de manera similar a Python. Esta sintaxis es mucho más limpia que la concatenación tradicional.

```csharp
string producto = "Laptop";
decimal precio = 999.99m; // La 'm' indica que es un decimal

// Ejemplo de Interpolación (usando $)
string mensaje = $"El {producto} tiene un precio de {precio:C}.";

// Salida: El Laptop tiene un precio de $999.99. (Dependiendo de la configuración regional)

// Expresiones más complejas y métodos
int resultado = 4 + 1;
Console.WriteLine($"El resultado de la suma es {resultado}.");

// Salida: El resultado de la suma es 5.
```

-----

> [!NOTE]
> Los lenguajes de *scripting* (PowerShell, Bash) confían en el símbolo `$` sin sintaxis de llave adicional (siempre y cuando se usen comillas dobles), mientras que los lenguajes más estructurados (Python, C\#) requieren un prefijo (`f` o `$`) y el uso de llaves `{}` para marcar las expresiones a interpolar, lo cual ofrece más control y claridad.
