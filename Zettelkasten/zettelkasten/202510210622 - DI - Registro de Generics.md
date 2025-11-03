# Unique Identifier
202510210622

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

Caso seja mais interessante a criação de classes genéricas (que usam polimorfismo paramétrico) ainda assim podemos fazer uso da injeção de dependência por meio de um container.

```csharp
public interface IRepositoryGeneric<T> where T : class
{
    public void Save();
}
public class RepositoryGeneric<T> : IRepositoryGeneric<T> where T : class
{
    public void Save() 
    { /* codigo */ }
}
```

No Program.cs vamos colocar desse modo.

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddRazorPages();
builder.Services.AddScoped(
	typeof(IRepositoryGeneric<>), typeof(RepositoryGeneric<>)
);

var app = builder.Build();
```

O resto segue igual.

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
[[202510070613 - OOP - Polimorfismo]]