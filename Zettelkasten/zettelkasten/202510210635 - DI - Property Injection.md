# Unique Identifier
202510210635

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

Existe a possibilidade de usar DI diretamente na passagem de params em uma function. Mas isso não é indicado porque é ruim de testar. Estou salvando aqui porque pode haver alguma situação onde eu não vou conseguir fazer DI via construtor.

```csharp
// Repository.cs
public interface IRepository
{
	public void Save();
}
public class Repository : IRepository
{
	public void Save() 
	{ /* codigo */ }
}

// Program.cs
builder.Services.AddRazorPages();
builder.Services.AddScoped<IRepository, Repository>();

// Controller.cs
public class Controller
{
	// aqui estamos recebendo direto do services da app
	public void Metodo([FromServices] IRepository repository)
	{
		repository.Save();
	}
}
```


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]