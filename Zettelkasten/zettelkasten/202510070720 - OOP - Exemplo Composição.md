# Unique Identifier
202510070720

# Tag
#OOP 

# Body
[[202510030654 - OOP]][[202510070712 - OOP - Herança e Composição]]

Aqui tem um exemplo mais específico do porquê composição é melhor que herança. Para isso vamos fazer uso de composição com interface.

```csharp
public class ClasseQualquer {/* estados e comportamentos */}

// interface sem escopo definido de classe
public interface IInterfaceGenerica<T>
{
    void MetodoGenerico1(T obj);
    void MetodoGenerico2(T obj);
}

// interface com escopo definido de uso para ClasseQualquer
public interface IInterfaceDefinida
{
    void MetodoGenerico1(ClasseQualquer obj);
    // vamos supor que nao queremos o metodoGenerico2 quando trabalhamos com ClasseQualquer
}

// implementacao da interface com os 2 metodos
public class ImplementaInterfaceGenerica<T> : IInterfaceGenerica<T>
{
    public void MetodoGenerico1(T obj) { /*logica*/ }
    public void MetodoGenerico2(T obj) { /*logica*/ }
}

// classe que implementa a interface definida usando heranca
public class UsoDaHeranca : ImplementaInterfaceGenerica<ClasseQualquer>, IInterfaceDefinida
{
    public void ExecutaMetodo()
    {
        var obj = new ClasseQualquer();
        MetodoGenerico1(obj);
        MetodoGenerico2(obj); // temos acesso a esse metodo
    }
}

// classe que implementa a interface usando composicao
public class UsoDaComposicao : IInterfaceDefinida
{
    private readonly IInterfaceGenerica<ClasseQualquer> _interfaceDefinida;

    public UsoDaComposicao(IInterfaceGenerica<ClasseQualquer> interfaceDefinida) 
    { 
	    _interfaceDefinida = interfaceDefinida; 
	}

    // aqui nos temos que implementar o acesso aos metodos que vamos usar
    public void MetodoGenerico1(ClasseQualquer obj)
    {
        _interfaceDefinida.MetodoGenerico1(obj);
    }
}

// teste de unidade
public class TesteDeUnidade
{
    public void Teste()
    {
        var objTeste = new ClasseQualquer();
        // podemos usar qualquer classe que implemente o contrato
        // isso facilita muito os testes
        var interfaceGenerica = new ImplementaInterfaceGenerica<ClasseQualquer>();

        // teste usando heranca
        var testHeranca = new UsoDaHeranca();
        testHeranca.MetodoGenerico1(objTeste);
        testHeranca.MetodoGenerico2(objTeste);

        // teste usando composicao
        var testComp = new UsoDaComposicao(interfaceGenerica);
        testComp.MetodoGenerico1(objTeste);
        // testComp.MetodoGenerico2(objTeste); <- erro pois nao tem esse metodo
    }
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]