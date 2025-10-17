# Unique Identifier
202510170631

# Tag
#SOLID 

# Body
> Clientes (aka Classes) não devem ser forçados a depender de métodos que não usam.

> É melhor ter muitas interfaces específicas do que uma única interface grande.

```csharp
public interface ICadastro
{
    // logica apenas para cadastro de clientes
    void SendEmail(string to, string subject, string body);
    // logica apenas para cadastro de fornecedores
    void SendContract(string to, string subject, string body);
    // logica para ambos
    void Save(string nome, string email);
}

public class CadastroCliente : ICadastro
{
    public void Save(string nome, string email) { }
    public void SendEmail(string to, string subject, string body) { }
    // sou obrigado a implementar mesmo sem usar
    public void SendContract(string to, string subject, string body) { }
}
```

Como correção, poderíamos usar **hierarquia** entre interfaces (olha que maneiro).

```csharp
public interface ICadastro
{
    void Save(string nome, string email);
}

public interface ICadastroCliente : ICadastro
{
    void SendEmail(string to, string subject, string body);
}

public interface ICadastroFornecedor : ICadastro
{
    void SendContract(string to, string subject, string body);
}

public class CadastroCliente : ICadastroCliente
{
    public void Save(string nome, string email) { }
    public void SendEmail(string to, string subject, string body) { }
}
```


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]