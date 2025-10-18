# Unique Identifier
202510060615

# Tag
#OOP #Programação 

# Body
[[202510030654 - OOP]]

Classe é uma representação de uma entidade que possui estados e comportamentos nela. 

Objeto é a instanciação (ou seja, alocação em memória) de uma classe.

Em outras palavras, classes são descrições de objetos que serão criados e usados em tempo de execução.

```csharp

// classe
public class Classe()
{
	public int param1 { get; set; } 
}

// objeto
public class Objeto()
{
	public Objeto()
	{
		// criacao do objeto
		var objetoCriado = new Classe()
		{
			param1 = 100
		};
	}
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]