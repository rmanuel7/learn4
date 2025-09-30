# Arreglos (arrays)

El manejo de **arreglos (arrays)** o **listas** es una de las partes más importantes al programar, ya que nos permite almacenar y gestionar colecciones de datos.

> [!NOTE]
> La diferencia clave aquí es que **PowerShell**, **Python** y **Bash** usan estructuras flexibles (listas/arrays dinámicos), mientras que **C\#** requiere arrays de tamaño fijo o el uso de tipos de colección especializados (como `List<T>`) para la flexibilidad.

-----

## Creación de Arreglos o Listas

| Lenguaje | Nombre de la Estructura | Sintaxis de Creación | Explicación Breve |
| :--- | :--- | :--- | :--- |
| **PowerShell** | Array | `$miArray = @(10, 20, 30)` | Usa `@()` para inicializar un array. |
| **Bash** | Array Indexado | `colores=(rojo verde azul)` | Se inicializa con paréntesis `()`. |
| **Python** | Lista (List) | `mi_lista = [1, "dos", 3.0]` | Usa corchetes `[]` para inicializar una lista. |
| **C\#** | Array/Lista Genérica | `int[] arr = { 1, 2, 3 };` ó `List<string> lista = new();` | Se puede usar el tipo `Array` (fijo) o `List<T>` (dinámico). |

-----

## Operaciones Comunes de Arreglos/Listas

| Operación | PowerShell | Bash | Python | C\# (usando `List<T>`) |
| :--- | :--- | :--- | :--- | :--- |
| **Acceder al elemento** | `$miArray[0]` | `${colores[0]}` | `mi_lista[0]` | `lista[0]` |
| **Longitud/Tamaño** | `($miArray).Count` | `${#colores[@]}` | `len(mi_lista)` | `lista.Count` |
| **Añadir elemento** | `$miArray += 40` | `colores+=(amarillo)` | `mi_lista.append(4)` | `lista.Add(4)` |
| **Iterar (Ejemplo)** | `foreach ($i in $arr)` | `for i in "${arr[@]}"` | `for i in mi_lista:` | `foreach (var i in lista)` |

-----

## Arreglos/Listas en Detalle

### 1\. PowerShell

En PowerShell, el tipo más común es el **Array**. Puedes usar el operador de adición (`+=`) para añadir elementos, pero internamente PowerShell crea un array nuevo más grande, lo que puede ser ineficiente para operaciones masivas. Es más eficiente usar la sintaxis de **Array Literals** (`@()`).

```powershell
# Creación e indexación
$nombres = @("Alice", "Bob", "Charlie")
Write-Host "El primer nombre es: $($nombres[0])"

# Añadir un elemento (ineficiente, pero común)
$nombres += "David"
Write-Host "Total de nombres: $($nombres.Count)"

# Recorrer
$nombres | ForEach-Object {
    Write-Host "Nombre: $_"
}
```

### 2\. Bash (Shell Scripting)

Bash usa **Arrays Indexados** o **Arrays Asociativos** (hashes). La sintaxis para acceder a los elementos es particular, requiriendo llaves `{}` y el símbolo `@` o `*` para acceder a todos los elementos.

```bash
# Creación e indexación
archivos=(log.txt config.ini data.json)
echo "Primer archivo: ${archivos[0]}"

# Añadir un elemento
archivos+=(reporte.pdf)

# Recorrer (acceso a todos los elementos)
for archivo in "${archivos[@]}"; do
    echo "Procesando: $archivo"
done
```

### 3\. Python

Python utiliza el tipo **`list`** (lista), que es una estructura de datos muy flexible, dinámica y que puede contener elementos de diferentes tipos (heterogénea). Es la colección de datos más fundamental y usada en Python.

```python
# Creación e indexación
parametros = [10, "config", True]
print(f"Elemento central: {parametros[1]}")

# Añadir un elemento
parametros.append("nuevo_valor")
print(f"Longitud después de añadir: {len(parametros)}")

# Recorrer
for p in parametros:
    print(f"Valor: {p}")
```

### 4\. C\#

En **C\#**, tienes dos opciones principales:

1.  **Arrays de tamaño fijo:** Son eficientes para el acceso, pero no pueden cambiar de tamaño. Requieren declarar el tipo de dato y el tamaño.
2.  **`List<T>` (Listas Genéricas):** Son la opción preferida para colecciones dinámicas. Son parte de la librería de **Collections** y permiten añadir o eliminar elementos fácilmente.

<!-- end list -->

```csharp
// 1. Array de tamaño fijo (solo contiene enteros)
int[] numeros = new int[3] { 1, 2, 3 };

// 2. Lista genérica (flexible, solo contiene strings)
List<string> usuarios = new List<string> { "Ana", "Beto" };

// Acceder al elemento
Console.WriteLine($"Usuario 1: {usuarios[0]}");

// Añadir un elemento a la lista dinámica
usuarios.Add("Carla");
Console.WriteLine($"Total de usuarios: {usuarios.Count}");

// Recorrer
foreach (string usuario in usuarios)
{
    Console.WriteLine($"Usuario: {usuario}");
}
```

-----

> [!NOTE]
> Python y C\# (`List<T>`) ofrecen colecciones dinámicas a través de **métodos** de objeto (`append`, `Add`), mientras que PowerShell usa el operador de asignación (`+=`) y Bash utiliza una sintaxis de **expansión** especial (`+=(...)`).
