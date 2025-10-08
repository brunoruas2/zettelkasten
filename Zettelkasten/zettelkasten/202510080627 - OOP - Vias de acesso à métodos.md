# Unique Identifier
202510080627

# Tag
#OOP

# Body
[[202510030654 - OOP]]
[[202510070712 - OOP - Herança e Composição]]
[[202510070720 - OOP - Exemplo Composição]]

Existem 4 conceitos que se relacionam ao acesso à métodos de classes.

1. Herança 
2. Composição
	1. Interface <- Melhor abordagem
	2. Objeto Concreto
3. Implementação direta 

Esses conceitos se complementam e formam a base do polimorfismo e da reutilização de código.

```csharp
public interface IClassePai { void MetodoPai(); }

public class ClassePai : IClassePai
{
    public void MetodoPai() { }
}

// Implementacao direta
public class Implementacao
{
    public void Implementa()
    {
        var classePai = new ClassePai();
        classePai.MetodoPai();
    }
}

// Heranca
public class Heranca : ClassePai
{
    public void HerancaMetodo() { MetodoPai(); }
}

// Composicao via objeto concreto
public class Composicao
{
    public ClassePai? ClassePai { get; set; }
    public void UsandoComposicao()
    {
        var classeComposicao = new Composicao();
        classeComposicao.ClassePai?.MetodoPai();
    }
}

// Composicao via interface
public class Interface
{
    private readonly IClassePai _classePai;
    public Interface(IClassePai classePai) { _classePai = classePai; }
    public void MetodoInterface() { _classePai.MetodoPai(); }
}
