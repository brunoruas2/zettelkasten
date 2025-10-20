# Unique Identifier
202510200611

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

Exemplo em ASP.NET Core com .NET 9

```csharp
// no arquivo Program.cs
var builder = WebApplication.CreateBuilder(args);

// Aqui estamos injetando as dependencias no container
builder.Services.AddRazorPages();
builder.Services.AddScoped<IRepository, Repository>();

var app = builder.Build();

// [...]
app.Run();
```

Toda vez que um contrato `IRepository` for colocado no construtor de uma classe para fazermos o DIP. O container de DI irá automaticamente alocar um objeto `Repository` conforme indicamos no builder.

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]