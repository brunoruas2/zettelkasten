# Unique Identifier
202510140612

# Tag
#SOLID 

# Body
> Uma classe deve estar fechada para modificação e aberta para extensão.

A ideia aqui é que as classes evoluam apenas no sentindo de aumentar a capacidade das classes por meio de extensões sem alterar o que já está implementado (o que pode quebrar várias partes do código).

Podemos usar a herança para essa expansão com interfaces ou [[202510140621 - Csharp - Extension Methods]] no caso de c# e outras linguagens.

```csharp
// violacao do principio
public class BonusService
{
    public double CalcularBonus(string tipoFuncionario, double salario)
    {
        if (tipoFuncionario == "Comum")
            return salario * 0.1;

        if (tipoFuncionario == "Gerente")
            return salario * 0.2;
            
        // essa classe precisa ser atualizada toda vez que um novo tipo de funcionario for criado

        return 0;
    }
}
```

```csharp
// correcao do OCP por heranca e interface
// Interface que define o contrato
public interface IFuncionario
{
    double CalcularBonus();
}

// Implementações específicas
public class FuncionarioComum : IFuncionario
{
    public double Salario { get; set; }
    public FuncionarioComum(double salario) => Salario = salario;

    public double CalcularBonus() => Salario * 0.1;
}

public class Gerente : IFuncionario
{
    public double Salario { get; set; }
    public Gerente(double salario) => Salario = salario;

    public double CalcularBonus() => Salario * 0.2;
}

// Serviço que usa polimorfismo
public class BonusService
{
    public double Calcular(IFuncionario funcionario)
    {
        return funcionario.CalcularBonus();
    }
}
```

# Footer / Reference
https://objectmentor.com/resources/articles/ocp.pdf

[[REF - Desenvolvedor.io - Curso Arquitetura]]