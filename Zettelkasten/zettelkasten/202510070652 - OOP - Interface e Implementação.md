# Unique Identifier
202510070652

# Tag
#OOP 

# Body
[[202510030654 - OOP]]

TODO - Voltar aqui quando estudarmos SOLID com interface.

Uma interface define contratos (parecido com uma classe abstrata) mas sem definir nenhuma implementação. A principal diferença é que a classe abstrata **pode** implementar algo se ela quiser, enquanto uma interface não tem nada de implementação além do nome do método, o retorno e os params das funções.

```csharp
public interface IRepo
{
	void GetItem();
}

public class Repo : IRepo
{
	public void GetItem() 
	{ // implementacao 
	}
}

public class RepoFake : IRepo
{
	public void GetItem()
	{ // faz nada so implementa vazio para teste de unidade
	}
}
```

Podemos usar a classe de repositório direto em uma classe instanciando um objeto dele dentro do código (chamamos isso de implementação) mas isso é ruim porque aumenta o acoplamento. Se eu mudar a classe `Repo`, eu quebro a implementação na classe abaixo.

```csharp

public class ImplementaRuim()
{
	public void MetodoRuim()
	{
		var repo = new Repo();
		repo.GetItem();
	}
}
```

Para melhorar isso, podemos usar a injeção de dependência de modo que eu injeto o repositório no construtor e uso ele sem aumentar o acoplamento.

```csharp
public class ImplementaBom()
{
	private readonly IRepo _repo;
	
	public ImplementaBom(IRepo repo)
	{
		_repo = repo;
	}
	
	public void MetodoBom()
	{
		_repo.GetItem();
	}
}
```

Isso facilita muito os testes de unidade porque podemos passar qualquer classe mockada no construtor da classe de teste abstraindo totalmente a camada de repositório.

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]