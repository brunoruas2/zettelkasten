# Unique Identifier
202510210641

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

Obviamente, isso não é indicado pois viola o [[202510170631 - SOLID - Interface Segregation Principle (ISP)]] e também da [[202510150620 - SOLID - Liskov Substitution Principle (LSP)]].

```csharp
public interface IRepository
{
	public void Save();
}
public class RepositoryA : IRepository
{
	public void Save()  { /* codigo */ }
}
public class RepositoryB : IRepository
{
	public void Save() { /* codigo */ }
}
```

No registro do container a gente vai criar uma função lambda que recebe um param e instancia um serviço que a gente indicar. Para resolver esse caso vamos fazer uso do service locator (que sabemos que é um anti-paternD.)

```csharp
builder.Services.AddTransient<RepositoryA>();
builder.Services.AddTransient<RepositoryB>();
builder.Services.AddTransient<RepositoryC>();
builder.Services.AddTransient<Func<string, IRepository>>(serviceProvider => key =>
{
    switch (key)
    {
        case "A":
            return serviceProvider.GetRequiredService<RepositoryA>();
        case "B":
            return serviceProvider.GetRequiredService<RepositoryB>();
        default:
            return null;
    }
}
);
```

Para acessar o repositório vamos usar uma function.

```csharp
public class Controller
{
    private readonly Func<string, IRepository> _serviceAccessor;

    public Controller(Func<string, IRepository> serviceAccessor)
    {
        _serviceAccessor = serviceAccessor;
    }

    public void Metodo()
    {
        var repo = _serviceAccessor("A");// retornar RepositoryA
        repo.Save();
    }
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]