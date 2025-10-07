# Unique Identifier
202510070613

# Tag
#OOP 

# Body
[[202510030654 - OOP]]

Se refere a capacidade de transformação de uma classe. Temos 2 tipos: Paramétrico e de Inclusão. O token chave para o polimorfismo é o `override` pois é ele que "transforma" a classe filha em relação à classe pai.

Token `abstract` obriga o polimorfismo enquanto o token `virtual` permite mas sem obrigar. O token `sealed` é usada para impedir o polimorfismo.

```csharp
// Polimorfismo de Inclusão
public class SuperClasse {
    public string str = "string original";

    // permitindo a sobrescrita por meio do token 'virtual'
    public virtual void Mostra() {
        Console.WriteLine("Mostra original");
    }
}
public class SubClasse : SuperClasse {
    // criando uma variável 'str' na classe filha
    public new string str = "String nova";

    // override do método original
    public override void Mostra() {
        Console.WriteLine("-------");
        base.mostra(); // função original
        Console.WriteLine("-------");
        Console.WriteLine("Mostra Estendida");
        Console.WriteLine("-------")
    }
}

// Polimorfismo paramétrico
public class Conjuntos <T> {
	// criacao de uma funcao como membro estatico
	// que retorna um booleano para os vetores "s" e "w"
	// do tipo de dado definido por "<T>"
	public static bool Disjuntos(T[] s, T[] w)
	{
	// loop em todos os elementos do vetor "s"
	for (int i = 0; i < s.Length; i++)
	{
		// loop em todos so elementos do vetor "w"
		for (int j = 0; j < w.Length; j++)
		{
			// Teste: O elemento s[i] é igual ao w[j]?
			// se sim, eles possuem algum elemento em comum
			// logo, nao sao conjuntos disjuntos!
			if (s[i].Equals(w[j]))
				return false;
		}
	}
	// se nenhum dos elementos dos dois conjuntos
	// for igual ao do outro, entao sao conjuntos
	// disjuntos!
	return true;
}
```


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
https://brunoruas2.github.io/CC_site/docs/puc/segundo-periodo/programacao-modular#polimorfismo-de-inclus%C3%A3o