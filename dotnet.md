# 🛠️ Manual de Referencia: .NET CLI

## Gestión de Soluciones y Proyectos

| Comando                                  | Descripción                                                         |
| ---------------------------------------- | ------------------------------------------------------------------- |
| `dotnet new sln -n Nombre`               | Crea un archivo de solución (.sln) para agrupar proyectos.          |
| `dotnet new webapi -o Nombre`            | Crea un proyecto Web API (Capa de Presentación).                    |
| `dotnet new classlib -o Nombre`          | Crea una biblioteca de clases (útil para capas Core, Data, Models). |
| `dotnet sln add Carpeta/Proyecto.csproj` | Agrega un proyecto existente a la solución actual.                  |
| `dotnet sln list`                        | Lista todos los proyectos que forman parte de la solución.          |

## Comandos de Mantenimiento y Ejecución

| Comando                         | Descripción                                                            |
| ------------------------------- | ---------------------------------------------------------------------- |
| `dotnet restore`                | Descarga y restaura los paquetes NuGet del proyecto.                   |
| `dotnet build`                  | Compila el proyecto y verifica errores de sintaxis.                    |
| `dotnet run --project Proyecto` | Compila y ejecuta el proyecto especificado.                            |
| `dotnet watch run`              | Ejecuta la app y aplica Hot Reload (recarga al guardar cambios).       |
| `dotnet clean`                  | Limpia los archivos de salida de compilaciones anteriores (bin y obj). |
