# AIM Web

Aplicación web administrativa del ecosistema **AIM**, una plataforma orientada a la gestión y al seguimiento de la práctica del tiro con arco.

AIM Web proporciona una interfaz web para la administración de la plataforma y forma parte de una solución .NET que incluye tanto la aplicación web como su API.

## Tabla de contenidos

- [Descripción](#descripción)
- [Arquitectura del proyecto](#arquitectura-del-proyecto)
- [Tecnologías](#tecnologías)
- [Funcionalidades](#funcionalidades)
- [Requisitos previos](#requisitos-previos)
- [Instalación y ejecución](#instalación-y-ejecución)
- [Estado del proyecto](#estado-del-proyecto)
- [Repositorios relacionados](#repositorios-relacionados)

## Descripción

**AIM Web** es el componente web administrativo del ecosistema AIM.

El proyecto está desarrollado con Blazor y .NET 10. Su objetivo es ofrecer una interfaz web desde la que gestionar y supervisar los recursos de la plataforma, complementando la experiencia de usuario de la aplicación multiplataforma.

La solución incorpora `ApiAim2.0`, la nueva API del ecosistema AIM, que sustituye al backend anterior.

De esta forma, la aplicación web y la API se desarrollan dentro de una misma solución, facilitando su mantenimiento y evolución conjunta.

## Arquitectura del proyecto

El ecosistema AIM se organiza en dos repositorios principales:

| Repositorio | Responsabilidad |
|---|---|
| [aim](https://github.com/mraldev/aim) | Aplicación multiplataforma desarrollada con Kotlin Multiplatform. |
| [AimWeb](https://github.com/mraldev/AimWeb) | Solución .NET que contiene la aplicación web administrativa, la nueva API y el proyecto de pruebas. |

### Estructura de la solución

La solución `AimWeb.slnx` contiene los siguientes proyectos:

- **`AimWeb/AimWeb.csproj`**: aplicación web administrativa desarrollada con Blazor.
- **`ApiAim2.0/ApiAim2.0.csproj`**: API desarrollada con ASP.NET Core, encargada de exponer los servicios del backend.
- **`TestAim/TestAim.csproj`**: proyecto destinado a las pruebas de la solución.

### Esquema de arquitectura

```text
                    Ecosistema AIM
                          |
             +------------+------------+
             |                         |
      Aplicación AIM              Solución AimWeb
    Kotlin Multiplatform                |
             |                +---------+---------+
             |                |                   |
       Cliente móvil       AIM Web            ApiAim2.0
                         Blazor Server       ASP.NET Core
                                                 |
                                          Persistencia de datos
                                             PostgreSQL
```

Este esquema representa la organización lógica del ecosistema. La comunicación efectiva entre los componentes y la configuración de la persistencia dependen de la implementación y de los parámetros de ejecución de cada proyecto.

## Tecnologías

### Aplicación web

- **C#:** lenguaje principal de desarrollo.
- **.NET 10:** plataforma de desarrollo y ejecución.
- **Blazor Server:** interfaz web interactiva mediante renderizado en servidor.
- **Radzen.Blazor:** biblioteca de componentes para la construcción de la interfaz.

### API y backend

- **ASP.NET Core:** desarrollo de la API HTTP.
- **Entity Framework Core:** acceso a datos mediante ORM.
- **PostgreSQL:** sistema de gestión de bases de datos.
- **C#:** lenguaje de desarrollo de la API.

## Funcionalidades

El panel administrativo se encuentra en desarrollo.

Las funcionalidades administrativas se documentarán a medida que se implementen y verifiquen.

## Requisitos previos

Para desarrollar y ejecutar el proyecto se necesita:

- Git.
- SDK de .NET 10.
- Un IDE compatible con C# y Blazor, como Visual Studio o JetBrains Rider, o un editor con soporte para .NET.

Si se va a ejecutar la API con persistencia de datos, también será necesario disponer de PostgreSQL y configurar los parámetros de conexión correspondientes.

Para comprobar los SDK instalados:

```bash
dotnet --info
```

## Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/mraldev/AimWeb.git
cd AimWeb
```

### 2. Restaurar las dependencias

Desde el directorio raíz de la solución:

```bash
dotnet restore AimWeb.slnx
```

### 3. Compilar la solución

```bash
dotnet build AimWeb.slnx
```

Este comando compila los proyectos incluidos en la solución, pero no garantiza que todos los servicios externos estén configurados o en ejecución.

### 4. Ejecutar la API

Para iniciar `ApiAim2.0` de forma independiente:

```bash
dotnet run --project ApiAim2.0/ApiAim2.0.csproj
```

Antes de utilizar la API, comprueba la configuración de la base de datos, las variables de entorno y los parámetros de ejecución requeridos.

### 5. Ejecutar la aplicación web

Para iniciar AIM Web:

```bash
dotnet run --project AimWeb/AimWeb.csproj
```

La aplicación utilizará la configuración de ejecución definida en el proyecto. Si la web necesita comunicarse con la API, será necesario que esta se encuentre disponible y que las direcciones y los parámetros de conexión estén correctamente configurados.

## Estado del proyecto

AIM Web se encuentra en desarrollo.

La solución contiene la aplicación web administrativa, la nueva API `ApiAim2.0` y un proyecto de pruebas. Las funcionalidades del panel y la integración entre los componentes evolucionarán conforme avance el desarrollo.

## Repositorios relacionados

- **Aplicación multiplataforma:** https://github.com/mraldev/aim
- **Aplicación web administrativa y nueva API:** https://github.com/mraldev/AimWeb

