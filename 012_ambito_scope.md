# Contexto de ejecución

Estos dos conceptos son fundamentales para entender cuándo el código está disponible para ser usado y dónde es accesible una variable.

---

## Carga (Loading) de Código

La **carga** se refiere a cómo un lenguaje incluye código de otros archivos (módulos, *scripts* o librerías) en el entorno de ejecución, haciéndolo disponible para su uso.

| Lenguaje | Tipo de Carga | Mecanismo de Carga |
| :--- | :--- | :--- |
| **C#** | **Compilación Explícita** | El compilador maneja las referencias a **Assemblies** (`.dll`) que contienen los `namespaces`. La directiva `using` solo simplifica los nombres. |
| **Python** | **Tiempo de Ejecución** | La sentencia **`import`** busca el módulo/paquete, lo ejecuta si es la primera vez (creando *namespaces*), y lo enlaza al *script* actual. |
| **PowerShell** | **Tiempo de Ejecución** | El comando **`Import-Module`** carga y ejecuta el código en un **ámbito de módulo** y lo expone a la sesión. También se usa `Add-Type` para código compilado. |
| **Bash** | **Tiempo de Ejecución** | El comando **`source`** (o `.`) ejecuta el *script* en el **ámbito del *shell* actual**, haciendo que las funciones y variables sean inmediatamente accesibles. |

### Puntos Clave sobre Carga:

* **C#** se diferencia porque la "carga" de código (referencias a DLLs) ocurre principalmente en tiempo de **compilación**.
* **Python** y **PowerShell** usan mecanismos de **importación/módulo** que crean un límite o *namespace* para el código cargado.
* **Bash** es el más directo: `source` simplemente *pega* el contenido del archivo en la sesión actual, sin aislamiento.

---

## Ámbito (Scope) de Variables

El **ámbito** define la región del código donde una variable o una función puede ser accedida.

| Lenguaje | Ámbito por Defecto | Modificadores/Particularidades |
| :--- | :--- | :--- |
| **C#** | **Bloque/Método** | Las variables declaradas con `var` o un tipo solo existen dentro del bloque `{}` donde fueron creadas. Controlado por el concepto de **Clases**. |
| **Python** | **Función** (LEGB) | Las variables declaradas dentro de una función son **locales** por defecto. Se usa **`global`** o **`nonlocal`** para modificar variables fuera del ámbito actual. |
| **PowerShell** | **Local/Script** | El ámbito por defecto es **Local** (dentro de la función). Usa prefijos explícitos como `$global:`, `$script:`, `$local:` para acceder o modificar ámbitos. |
| **Bash** | **Global** | Las variables son **Globales** por defecto. Se usa la palabra clave **`local`** dentro de una función para evitar sobrescribir variables globales. |

### Puntos Clave sobre Ámbito:

1.  **C# (Bloque):** El ámbito más estricto. Una variable solo existe dentro del par de llaves `{}` donde se declara (por ejemplo, dentro de un `if` o un `for`).
2.  **Python (Función):** Las variables dentro de una función son locales. Si intentas *asignar* un valor a una variable que no existe localmente, Python asume que quieres crear una variable local nueva, a menos que uses **`global`**.
3.  **PowerShell (Explícito):** Ofrece un control granular. Es el único que usa prefijos en las variables (`$script:miVar`) para acceder o modificar explícitamente variables en ámbitos superiores.
4.  **Bash (Global):** El más laxo. Una variable dentro de una función es **global** a menos que uses la palabra clave **`local`**. Esto a menudo causa efectos secundarios no deseados si no se tiene cuidado.

---

### Resumen Rápido:

* **Carga:** C# es compilación, los demás son ejecución. Bash usa `source` sin aislamiento, mientras que Python y PowerShell usan `import/module` para mayor orden.
* **Ámbito:** C# es por bloque (estricto), Python es por función, PowerShell es por función pero con prefijos de ámbito, y Bash es global por defecto (más laxo).
