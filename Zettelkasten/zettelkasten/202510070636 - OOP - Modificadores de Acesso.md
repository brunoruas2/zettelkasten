# Unique Identifier
202510070636

# Tag
#OOP 

# Body
[[202510030654 - OOP]] [[202510070631 - OOP - Encapsulamento]]

Tokens usados para o gerenciamento do encapsulamento. Conhecimento importante que deve ser decorado.

```csharp
// para classes e métodos
public // acesso irrestrito
protected // acesso limitado na classe ou nas filhas
internal // acesso apenas no assembly (projeto) atual do projeto
private // acesso apenas dentro da classe

// apenas para métodos
protected internal // acesso no assembly (projeto) e em classes filhas
private protected // acesso limitado dentro da classe e dentro do mesmo assembly
```

Lembrete: Os modificadores que estão relacionados com herança foram criados para evitar que se acesse os métodos de uma classe apenas pela instanciação da classe dentro de outra sem uma relação de herança. Exemplo:

```csharp
public class Classe1
{
    protected void Metodo1() { }
}

public class Classe2 : Classe1
{
    public void Metodo2()
    {
        // aqui eu consigo usar o metodo1 pois temos heranca
        Metodo1();

        var classe1 = new Classe1();
        // erro de compilacao pois eu criei uma classe nova
        classe1.Metodo1();
    }
}
```


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]