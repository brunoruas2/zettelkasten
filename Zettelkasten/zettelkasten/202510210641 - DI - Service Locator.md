# Unique Identifier
202510210641

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

Service locator é outra abordagem para usarmos IoC com injeção de dependência. Essa abordagem também não é muito interessante uma vez que o service provider expõe todas as implementações no container e deixa o código menos claro quanto às dependências usadas.

Além disso é mais complexo de testar visto que vamos ter que mockar o retorno do IServiceProvider inteiro.

É tão contra indicado que isso é considerado um anti-pattern.

```csharp
public class Controller
{
	private readonly IServiceProvider _serviceProvider;

	public Controller(IServiceProvider serviceProvider)
	{
		_serviceProvider = serviceProvider;
	}

	public void Metodo()
	{
		var repo = _serviceProvider.GetRequiredService<IRepository>();
		repo.Save();
	}
}
```

O melhor a se fazer é encapsular isso em uma classe e expor ela por meio de uma interface.

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]