# Unique Identifier
202510060607

# Tag
#OOP #Programação 

# Body
[[202510030654 - OOP]]

Em OOP, chamamos de **Estado** as propriedades da classe. **Comportamento** por sua vez são as partes que processam informação como funções ou procedimentos.

```csharp
public class Classe
{
	public int estado1 {get;set;}
	
	public int Comportamento1(int valor)
	{
		estado1 = valor; // comportamento modificando o estado original
		return estado1
	}
}
```


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]