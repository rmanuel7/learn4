# Punto de entrada y manejo de argumentos
 
El punto de entraada es crucial y diferencia a los lenguajes de *scripting* (PowerShell, Bash, Python) de un lenguaje compilado y estructurado como C\#.

-----

## Formas de Ejecución en Shell y Argumentos

| Lenguaje | Comando de Ejecución Típico | Argumentos dentro del Script | Concepto de "Método `main`" |
| :--- | :--- | :--- | :--- |
| **PowerShell** | `powershell -File .\script.ps1 arg1 arg2` | Se acceden mediante el bloque `param()` o la variable `$args`. | **Implícito.** El script se ejecuta secuencialmente de arriba abajo. |
| **Bash** | `bash --init-file ./script.sh arg1 arg2` | Se acceden posicionalmente: `$1`, `$2`, `$@`. | **Implícito.** El script se ejecuta secuencialmente de arriba abajo. |
| **Python** | `python script.py arg1 arg2` | Se acceden a través del módulo `sys.argv`. | **Explícito y Recomendado** con la estructura `if __name__ == "__main__":`. |
| **C\#** | `dotnet run` o `.\programa.exe arg1 arg2` | Se accede mediante el parámetro `string[] args` del método `Main`. | **Explícito y Requerido.** El programa inicia en el método `Main` de una clase. |

-----

## 1\. PowerShell

### Ejecución y Argumentos

En PowerShell, un *script* se ejecuta simplemente llamando al archivo (a menudo con `./` o `.\` para rutas relativas). El manejo de argumentos tiene dos formas principales:

1.  **Variable Automática `$args`**: Una *array* que contiene todos los argumentos pasados.
2.  **Bloque `param()`**: La forma recomendada para declarar argumentos nombrados y forzar tipos de datos.

<!-- end list -->

```powershell
# mi_script.ps1

# Paso 1: Definición de parámetros (Mejor Práctica)
param(
    [string]$Nombre = "Mundo"
)

# Paso 2: El script se ejecuta desde aquí
Write-Host "Hola, $Nombre. Este es PowerShell."
Write-Host "Total de argumentos pasados: $($args.Count)"

# Ejecución en Shell:
# PS C:\> .\mi_script.ps1 -Nombre "PowerUser"
# Salida: Hola, PowerUser. Este es PowerShell.
# Salida: Total de argumentos pasados: 0
```

### Método `main`

El concepto de un punto de entrada explícito como `main` **no existe** formalmente. El *script* de PowerShell simplemente comienza a ejecutar la primera línea de código no definida (fuera de funciones) y continúa secuencialmente.

-----

## 2\. Bash (Shell Scripting)

### Ejecución y Argumentos

Los *scripts* de Bash se ejecutan usando `./` (si tienen permisos de ejecución) o llamando al intérprete (`bash mi_script.sh`). El manejo de argumentos es puramente **posicional**:

  * **`$0`**: El nombre del *script* en sí.
  * **`$1`, `$2`, `$3`...**: Los argumentos pasados en orden.
  * **`$#`**: El número total de argumentos.
  * **`$@`**: Todos los argumentos como una lista separada.

<!-- end list -->

```bash
# mi_script.sh

# Paso 1: Se accede a los argumentos posicionalmente
echo "El script es: $0"
echo "Primer argumento: $1"
echo "Total de argumentos: $#"

# Paso 2: El script se ejecuta desde aquí
if [ "$1" == "iniciar" ]; then
    echo "Iniciando proceso..."
fi

# Ejecución en Shell:
# $ ./mi_script.sh iniciar log.txt
# Salida: El script es: ./mi_script.sh
# Salida: Primer argumento: iniciar
# Salida: Total de argumentos: 2
# Salida: Iniciando proceso...
```

### Método `main`

Al igual que PowerShell, **Bash no tiene** un método `main`. El *script* se ejecuta de principio a fin, línea por línea.

-----

## 3\. Python

### Ejecución y Argumentos

Python se ejecuta llamando al intérprete (`python mi_script.py`). Los argumentos se acceden a través de la lista **`sys.argv`** (donde el primer elemento, `sys.argv[0]`, es el nombre del *script*).

```python
# mi_script.py
import sys

# Paso 1: Definición del punto de entrada (el "main" de facto)
def main():
    print(f"Nombre del script: {sys.argv[0]}")
    # Accedemos al primer argumento después del nombre del script (índice 1)
    if len(sys.argv) > 1:
        print(f"Primer argumento: {sys.argv[1]}")
    else:
        print("No se pasaron argumentos adicionales.")

# Paso 2: La estructura "main"
if __name__ == "__main__":
    main()

# Ejecución en Shell:
# $ python mi_script.py hola
# Salida: Nombre del script: mi_script.py
# Salida: Primer argumento: hola
```

### Método `main`

Python fomenta el uso del bloque **`if __name__ == "__main__":`**. Esta estructura es el **`main` de facto**. Asegura que el código dentro de él solo se ejecute cuando el archivo se ejecuta directamente, y no cuando es importado como un módulo por otro *script*.

-----

## 4\. C\#

### Ejecución y Argumentos

C\# (como parte de un proyecto) se compila en un archivo ejecutable (`.exe` o *assembly*). La ejecución inicia llamando a este ejecutable (`.\mi_programa.exe`).

### Método `main`

El método **`Main`** es el **punto de entrada obligatorio** y explícito para cualquier aplicación de consola de C\#. El código debe estar dentro de una clase, y la ejecución comienza allí. Los argumentos se reciben directamente como un *array* de cadenas.

```csharp
// Program.cs

using System;

// El programa requiere una clase contenedora
class Program
{
    // Método Main: el punto de entrada obligatorio
    static void Main(string[] args)
    {
        // Paso 1: El código comienza aquí
        Console.WriteLine("El programa ha iniciado.");

        // Paso 2: Acceso a los argumentos a través del parámetro 'args'
        if (args.Length > 0)
        {
            Console.WriteLine($"Primer argumento: {args[0]}");
        }
        else
        {
            Console.WriteLine("No se pasaron argumentos.");
        }
    }
}

// Ejecución en Shell (después de compilar):
// C:\> .\mi_programa.exe proceso1
// Salida: El programa ha iniciado.
// Salida: Primer argumento: proceso1
```

-----

> [!NOTE]
> **C\#** es el más estricto, requiriendo un método `Main` explícito. **Python** lo emula con una convención (`if __name__ == "__main__":`). **PowerShell** y **Bash** son más libres, ejecutando el *script* secuencialmente desde el principio.
