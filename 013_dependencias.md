# Manejo de paquetes

El manejo de **paquetes, repositorios e instalación** es la piedra angular del desarrollo moderno, ya que nos permite reutilizar el trabajo de otros de manera eficiente.

## Paquetes, Repositorios e Instalación

| Concepto | PowerShell | Bash (Linux) | Python | C\# (Ecosistema .NET) |
| :--- | :--- | :--- | :--- | :--- |
| **Gestor de Paquetes** | **PowerShellGet** / **`Install-Module`** | **`apt`**, **`yum`**, **`dnf`**, etc. | **`pip`** (Python Installer) | **`NuGet`** (Se integra con **`dotnet`** CLI) |
| **Repositorio Central** | **PSGallery** (PowerShell Gallery) | **Servidores de Distribución** (Debian, Red Hat, etc.) | **PyPI** (Python Package Index) | **NuGet Gallery** |
| **Instalación de Librerías** | `Install-Module Nombre` | `sudo apt install nombre` | `pip install nombre_paquete` | `dotnet add package NuGet_ID` |
| **Uso en el Código** | `Import-Module Nombre` | `source` (para scripts) | `import nombre_paquete` | `using NombreEspacio` |

-----

## 1\. PowerShell

### Gestor y Repositorio

  * **Gestor:** El principal es **`PowerShellGet`**, que proporciona *cmdlets* para descubrir, instalar y publicar módulos.
  * **Repositorio:** **PSGallery** (PowerShell Gallery) es el repositorio central, donde se encuentran módulos de la comunidad y de Microsoft.

### Instalación y Uso

El flujo de trabajo es muy directo, similar a la gestión de *scripts* y módulos:

1.  **Instalar un Módulo (Paquete):**
    ```powershell
    Install-Module Az # Instala el módulo de Azure
    ```
2.  **Usar la Funcionalidad:**
    ```powershell
    Import-Module Az
    Connect-AzAccount # Comando disponible tras la importación
    ```

-----

## 2\. Bash (Linux)

### Gestor y Repositorio

Bash en sí mismo no tiene un gestor de paquetes. Depende del **Sistema Operativo (SO) subyacente** para instalar herramientas (que luego se usan dentro del *script* Bash).

  * **Gestores (Ejemplos):** **`apt`** (Debian/Ubuntu), **`yum`** o **`dnf`** (Red Hat/CentOS). Estos gestores manejan librerías binarias o *scripts* del SO.
  * **Repositorios:** Los servidores de paquetes que mantiene la distribución de Linux (ej. repositorios de Ubuntu).

### Instalación y Uso

El objetivo en Bash no es instalar una *librería de código*, sino una **herramienta binaria** o un **script** que Bash pueda ejecutar.

1.  **Instalar una Herramienta (Ejemplo: `jq` para JSON):**
    ```bash
    sudo apt install jq
    ```
2.  **Usar la Herramienta:**
    ```bash
    cat datos.json | jq '.campo' # Se invoca la herramienta externa
    ```

-----

## 3\. Python

### Gestor y Repositorio

Python tiene el ecosistema de paquetes más definido y extendido en la comunidad de *scripting* y desarrollo general.

  * **Gestor:** **`pip`** (Python Installer Package), la herramienta estándar para instalar y gestionar paquetes de terceros.
  * **Repositorio:** **PyPI** (Python Package Index), el catálogo central que contiene miles de librerías, desde manejo de datos (`pandas`) hasta desarrollo web (`Django`).

### Instalación y Uso

El uso de **entornos virtuales** es la mejor práctica para aislar las dependencias del proyecto.

1.  **Instalar un Paquete (Librería):**
    ```bash
    pip install requests # Instala la librería para peticiones HTTP
    ```
2.  **Usar la Funcionalidad:**
    ```python
    import requests # El nombre del paquete se convierte en el namespace
    response = requests.get('http://api.com')
    ```

-----

## 4\. C\# (Ecosistema .NET)

### Gestor y Repositorio

C\# se basa en el ecosistema **.NET**, que utiliza un sistema de paquetes altamente formalizado para gestionar dependencias.

  * **Gestor:** **`NuGet`**. Se utiliza a través de herramientas como el **`dotnet` CLI** o la interfaz gráfica en Visual Studio.
  * **Repositorio:** La **NuGet Gallery** es el repositorio principal, que alberga paquetes que son esencialmente *assemblies* compilados (`.dll`).

### Instalación y Uso

Los paquetes se añaden como referencias al archivo de proyecto (`.csproj`), lo que permite que el compilador sepa dónde buscar las clases necesarias.

1.  **Instalar un Paquete:**
    ```bash
    dotnet add package Newtonsoft.Json # Añade el paquete al proyecto
    ```
2.  **Usar la Funcionalidad:**
    ```csharp
    using Newtonsoft.Json; // Se usa la directiva 'using' para el namespace
    var obj = JsonConvert.DeserializeObject(jsonString);
    ```

-----

> [!NOTE]
> C\# y Python tienen ecosistemas formales con gestores y repositorios dedicados (NuGet/PyPI), mientras que PowerShell usa `PowerShellGet` para sus módulos. Bash, al ser un *shell*, subcontrata la instalación a los gestores del sistema operativo (`apt`, `yum`).
