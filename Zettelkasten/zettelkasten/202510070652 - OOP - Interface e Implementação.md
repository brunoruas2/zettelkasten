# Unique Identifier
202510070652

# Tag
#OOP 

# Body
[[202510030654 - OOP]][[202510170631 - SOLID - Interface Segregation Principle (ISP)]][[202510170652 - SOLID - Dependency Inversion Principle (DIP)]]

Uma interface define contratos (parecido com uma classe abstrata) mas sem definir nenhuma implementação. A principal diferença é que a classe abstrata **pode** implementar algo se ela quiser, enquanto uma interface não tem nada de implementação além do nome do método, o retorno e os params das funções.

```csharp
public interface IRepo
{
	void GetItem();
}

public class Repo : IRepo
{
	public void GetItem()  { // implementacao  }
}

public class RepoFake : IRepo
{
	public void GetItem() { // faz nada }
}
```

Podemos usar a classe de repositório direto em uma classe instanciando um objeto dele dentro do código mas isso é ruim porque aumenta o acoplamento. Se eu mudar a classe `Repo`, existe uma grande chance de quebrar a implementação na classe abaixo. Além disso, a criação de teste de unidade fica muito difícil porque eu vou precisar lidar com o comportamento do repositório. Chamamos esse método de **composição concreta**.

```csharp
public class ImplementaRuim
{
	public void MetodoRuim()
	{
		var repo = new Repo();
		repo.GetItem();
	}
}
```

Para melhorar isso, podemos usar a [[202510181406 - DI - Injeção de Dependência]] de modo que eu injeto o repositório no construtor e uso ele sem aumentar o acoplamento. Chamamos essa técnica de **composição por interface**.

```csharp
public class ImplementaBom
{
	private readonly IRepo _repo;
	
	public ImplementaBom(IRepo repo) { _repo = repo; }
	
	public void MetodoBom() { _repo.GetItem(); }
}
```

Isso facilita muito os testes de unidade porque podemos passar qualquer classe mockada no construtor da classe de teste abstraindo totalmente a camada de repositório.

```csharp
public class TesteUniade
{
	public void Teste1()
	{
		// aqui eu posso injetar a classe RepoFake o que torna a criacao
		// de testes MUITO mais simples
		var teste = new ImplementaBom(RepoFake)
		
		// resto do teste
	}
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]