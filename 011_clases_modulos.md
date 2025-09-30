# Organización y reutilización del código

Cómo se maneja la **organización y reutilización del código** a gran escala, utilizando **clases**, **módulos** y **espacios de nombres (namespaces)**. Esto es lo que realmente separa la programación *orientada a objetos* (C\#, Python) de los *scripts* secuenciales (Bash, PowerShell).

## Organización y Estructuras de Código

| Concepto | PowerShell | Bash | Python | C\# |
| :--- | :--- | :--- | :--- | :--- |
| **Clases / POO** | Soporte completo desde PowerShell 5.0. | **No Soporta.** Se limita a funciones y variables. | Soporte nativo, fundamental para el lenguaje. | **Fundamental y Requerido.** Un pilar de .NET. |
| **Módulos / Librerías** | Módulos (`.psm1`, `.dll`). Carga con `Import-Module`. | *Scripts* o funciones que se cargan con `source`. | Módulos (`.py`) y Paquetes (directorios). Carga con `import`. | *Assemblies* (`.dll`). Carga implícita o con `using`. |
| **Espacios de Nombres** | **Implícito** (usa el nombre del módulo). | **No Aplica.** | **Implícito** (usa el nombre del módulo/paquete). | **Explícito** (`namespace`) y crucial para evitar colisiones. |
| **Carga/Inclusión** | `Import-Module`, `Add-Type`. | `source` o `.` | `import`, `from ... import ...` | `using` (para namespaces). |

-----

## 1\. PowerShell

### Clases y POO

Desde PowerShell 5.0, puedes definir **Clases** usando la palabra clave `class`. Esto permite la **Programación Orientada a Objetos (POO)** formalmente, aunque el lenguaje se usa más a menudo para tareas de scripting secuenciales.

```powershell
# Definición de una Clase
class Usuario {
    [string]$Nombre
    Usuario([string]$n) { $this.Nombre = $n }
    [string] Saludar() { return "Hola $($this.Nombre)" }
}

# Uso
$u = [Usuario]::new("Alex")
$u.Saludar()
```

### Módulos y Carga

PowerShell organiza el código reutilizable en **Módulos** (`.psm1`).

  * **Carga:** Se usa el comando **`Import-Module`** para cargar funciones, variables y clases definidas en ese módulo en la sesión actual.
  * **Reutilización:** También puede usar **`Add-Type`** para cargar código compilado de C\# (DLLs) directamente.

-----

## 2\. Bash (Shell Scripting)

### Clases y POO

**Bash no tiene soporte nativo para Clases ni para la POO formal.** El código se organiza en **funciones** secuenciales.

### Módulos y Carga

El concepto más cercano a un módulo es un *script* que contiene solo definiciones de funciones y variables.

  * **Carga:** Se usa el comando **`source`** o su alias **`.`** (punto) para ejecutar el *script* en el *shell* actual. Esto hace que las funciones y variables definidas en ese archivo estén disponibles globalmente.
  * **Ejemplo:** `source ./mis_funciones.sh`

### Namespaces

**No aplica.** Los nombres de las funciones y variables cargadas son globales en el *shell* actual, lo que puede causar conflictos si se cargan varios *scripts* con nombres idénticos.

-----

## 3\. Python

### Clases y POO

**Python es fuertemente orientado a objetos.** Las **Clases** se definen con la palabra clave `class` y son fundamentales para estructurar la mayoría de las aplicaciones.

```python
# Definición de una Clase
class Usuario:
    def __init__(self, nombre):
        self.nombre = nombre
    
    def saludar(self):
        return f"Hola {self.nombre}"

# Uso
u = Usuario("Alex")
print(u.saludar())
```

### Módulos y Carga

Python organiza el código en **Módulos** (archivos `.py`) y **Paquetes** (colecciones de módulos en directorios).

  * **Carga:** Se usa la palabra clave **`import`**.
      * **`import math`**: Carga el módulo `math`. Accedes a funciones como `math.sqrt()`.
      * **`from math import sqrt`**: Carga solo la función `sqrt` para usarla directamente.

### Namespaces

Los módulos de Python actúan como sus propios **espacios de nombres implícitos**. Cuando haces `import math`, el nombre `sqrt` de ese módulo se accede como `math.sqrt`, evitando colisiones con otras funciones `sqrt` definidas en otro lugar.

-----

## 4\. C\#

### Clases y POO

**C\# es un lenguaje puramente orientado a objetos.** Toda la lógica debe estar contenida dentro de **Clases** o **Structs**.

```csharp
// Definición de una Clase
public class Usuario
{
    public string Nombre { get; set; }
    public Usuario(string n) { Nombre = n; }
    public string Saludar() { return $"Hola {Nombre}"; }
}
```

### Namespaces y Carga

C\# utiliza **Namespaces** como su mecanismo primario de organización para agrupar clases y evitar colisiones de nombres.

  * **Definición:** Las clases se envuelven en un bloque **`namespace`** (por ejemplo, `namespace MiApp.Datos { ... }`).
  * **Carga:** Para usar clases de otro *namespace* (o un *assembly* cargado), se usa la directiva **`using`**. Esto permite usar los nombres de las clases directamente sin tener que calificarlas (ej. `Console.WriteLine` en lugar de `System.Console.WriteLine`).

### Módulos y Carga

El código compilado se distribuye en **Assemblies** (archivos `.dll`). El sistema de proyectos de .NET se encarga de cargar los *assemblies* referenciados automáticamente, y el programador solo necesita gestionar la organización de los *namespaces* con la directiva `using`.

