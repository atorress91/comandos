# 🛠️ Manual de Referencia: Entity Framework Core

## Instalación y Configuración

| Comando                                                      | Descripción                                    |
| ------------------------------------------------------------ | ---------------------------------------------- |
| `dotnet add package Microsoft.EntityFrameworkCore`           | Instala el paquete base de EF Core.            |
| `dotnet add package Microsoft.EntityFrameworkCore.SqlServer` | Instala el proveedor para SQL Server.          |
| `dotnet add package Microsoft.EntityFrameworkCore.Tools`     | Instala las herramientas de EF Core.           |
| `dotnet add package Microsoft.EntityFrameworkCore.Design`    | Instala el paquete de diseño para migraciones. |

## Migraciones

| Comando                                    | Descripción                                          |
| ------------------------------------------ | ---------------------------------------------------- |
| `dotnet ef migrations add NombreMigracion` | Crea una nueva migración con los cambios pendientes. |
| `dotnet ef migrations list`                | Lista todas las migraciones aplicadas y pendientes.  |
| `dotnet ef migrations script`              | Genera un script SQL con todas las migraciones.      |
| `dotnet ef migrations script Desde Hasta`  | Genera un script SQL entre migraciones específicas.  |
| `dotnet ef migrations remove`              | Elimina la última migración si no ha sido aplicada.  |
| `dotnet ef migrations --help`              | Muestra ayuda para comandos de migraciones.          |

## Operaciones de Base de Datos

| Comando                                     | Descripción                                                     |
| ------------------------------------------- | --------------------------------------------------------------- |
| `dotnet ef database update`                 | Aplica todas las migraciones pendientes a la base de datos.     |
| `dotnet ef database update NombreMigracion` | Aplica migraciones hasta una específica.                        |
| `dotnet ef database drop`                   | Elimina la base de datos.                                       |
| `dotnet ef database drop --force`           | Elimina la base de datos sin confirmación.                      |
| `dotnet ef dbcontext list`                  | Lista todos los DbContext en el proyecto.                       |
| `dotnet ef dbcontext info`                  | Muestra información del DbContext.                              |
| `dotnet ef dbcontext scaffold`              | Genera entidades y DbContext desde una base de datos existente. |

## Generación de Código

| Comando                                                                                   | Descripción                                         |
| ----------------------------------------------------------------------------------------- | --------------------------------------------------- |
| `dotnet ef dbcontext scaffold "ConnectionString" Microsoft.EntityFrameworkCore.SqlServer` | Genera modelos y DbContext desde una base de datos. |
| `dotnet ef dbcontext scaffold --table Tabla1,Tabla2`                                      | Genera solo tablas específicas.                     |
| `dotnet ef dbcontext scaffold --force`                                                    | Sobrescribe archivos existentes.                    |

## Consultas y Operaciones LINQ

| Método                                               | Descripción                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| `context.Entidades.ToList()`                         | Obtiene todos los registros.                               |
| `context.Entidades.Where(e => e.Propiedad == valor)` | Filtra registros con condición.                            |
| `context.Entidades.FirstOrDefault()`                 | Obtiene el primer registro o null.                         |
| `context.Entidades.Find(id)`                         | Busca por clave primaria.                                  |
| `context.Entidades.Include(e => e.Relacion)`         | Incluye entidades relacionadas (eager loading).            |
| `context.Entidades.OrderBy(e => e.Propiedad)`        | Ordena los resultados.                                     |
| `context.Entidades.Skip(n).Take(m)`                  | Paginación: salta n y toma m registros.                    |
| `context.Entidades.Count()`                          | Cuenta el número de registros.                             |
| `context.Entidades.Any(e => e.Condicion)`            | Verifica si existe algún registro que cumpla la condición. |
| `context.Entidades.Add(entidad)`                     | Agrega una nueva entidad.                                  |
| `context.Entidades.Update(entidad)`                  | Actualiza una entidad existente.                           |
| `context.Entidades.Remove(entidad)`                  | Elimina una entidad.                                       |
| `context.SaveChanges()`                              | Guarda todos los cambios en la base de datos.              |
| `context.SaveChangesAsync()`                         | Guarda cambios de forma asíncrona.                         |

## Configuración de DbContext

| Método                                                                          | Descripción                                               |
| ------------------------------------------------------------------------------- | --------------------------------------------------------- |
| `protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)` | Configura la conexión a la base de datos.                 |
| `protected override void OnModelCreating(ModelBuilder modelBuilder)`            | Configura el modelo de datos (relaciones, índices, etc.). |
| `modelBuilder.Entity<Entidad>().HasKey(e => e.Id)`                              | Define clave primaria.                                    |
| `modelBuilder.Entity<Entidad>().Property(e => e.Propiedad).IsRequired()`        | Hace una propiedad requerida.                             |
| `modelBuilder.Entity<Entidad>().HasOne(e => e.Relacion).WithMany()`             | Configura relación uno a muchos.                          |
| `modelBuilder.Entity<Entidad>().HasIndex(e => e.Propiedad)`                     | Crea un índice en una propiedad.                          |

## Manejo de Relaciones

| Tipo            | Descripción                                  |
| --------------- | -------------------------------------------- |
| Uno a Uno       | `HasOne().WithOne()`                         |
| Uno a Muchos    | `HasOne().WithMany()`                        |
| Muchos a Muchos | `HasMany().WithMany()`                       |
| Carga Eager     | `.Include()` en la consulta.                 |
| Carga Lazy      | Propiedad virtual con navegación automática. |
| Carga Explícita | `.Load()` después de la consulta.            |

## Migraciones Avanzadas

| Comando                                                      | Descripción                                                    |
| ------------------------------------------------------------ | -------------------------------------------------------------- |
| `dotnet ef migrations add --output-dir Migrations/Custom`    | Especifica directorio para migraciones.                        |
| `dotnet ef migrations add --namespace MiProyecto.Migrations` | Especifica namespace para migraciones.                         |
| `dotnet ef migrations script --idempotent`                   | Genera script idempotente (se puede ejecutar múltiples veces). |
| `dotnet ef migrations bundle`                                | Crea un ejecutable autocontenido para aplicar migraciones.     |

## Depuración y Diagnóstico

| Comando                                   | Descripción                                           |
| ----------------------------------------- | ----------------------------------------------------- |
| `dotnet ef --verbose`                     | Muestra salida detallada.                             |
| `context.Database.EnsureCreated()`        | Crea la base de datos si no existe (sin migraciones). |
| `context.Database.Migrate()`              | Aplica migraciones pendientes en código.              |
| `context.Database.GetPendingMigrations()` | Lista migraciones pendientes.                         |
| `context.Database.GetAppliedMigrations()` | Lista migraciones aplicadas.                          |

## Mejores Prácticas

- Usa migraciones para cambios en el esquema.
- Implementa repositorios para encapsular lógica de acceso a datos.
- Usa async/await para operaciones de base de datos.
- Configura índices en propiedades frecuentemente consultadas.
- Maneja transacciones para operaciones complejas.
- Usa logging para diagnosticar problemas de rendimiento.</content>
  <parameter name="filePath">c:\Users\andre\Desktop\comandos\entity-framework.md
