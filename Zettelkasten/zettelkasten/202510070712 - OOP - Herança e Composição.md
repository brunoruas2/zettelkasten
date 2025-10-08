# Unique Identifier
202510070712

# Tag
#OOP 

# Body
[[202510030654 - OOP]]

Basicamente, uma herança só é uma boa ideia se realmente tivermos uma relação de subconjunto entre classes. Só faz sentido herdar se realmente a classe filha for do tipo da classe pai.

Mas, na vida real, a maioria das vezes, nós não temos relações com tanta certeza. Para isso podemos usar uma classe dentro da outra sem colocar uma relação de herança (o que permite mais flexibilidade). Chamamos isso de composição (depois vamos juntar com o conceito de [[202510070652 - OOP - Interface e Implementação]]).

```csharp
public class ClassePai
{
	public string paramStringPai {get;set;}
}
// heranca simples
public class ClasseFilha : ClassePai
{
	public string paramString {get;set;}
}
// composicao
public class ClasseImplementacao
{
	public ClassePai classePai {get;set;} // trouxe a classe pai inteira
	public string paramString {get;set;}
}
```

Aqui tem um exemplo de como composição é melhor: [[202510070720 - OOP - Exemplo Composição]]

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]