# Unique Identifier
202510090651

# Tag
#SOLID

# Body
[[202510090642 - SOLID]]

> Uma classe só deve ter 1 motivo para ser modificada, ou seja, deve ter apenas 1 responsabilidade.

Aqui vale um disclaimer: Existem classes de serviço que vão atuar em várias frentes mas **nunca** com a implementação dentro delas. Por exemplo, um service de cliente pode ter uma parte que salva o cliente no banco usando o repositório, envia um email usando um service de email confirmando o salvamento e etc, mas a implementação não está no service em si.

Exemplo de violação
```csharp
public class classeErroSrp
{
    public string Nome { get; set; }
    public string Email { get; set; }

	// a propria classe esta interagindo com o banco
    public string AdicionaNaBase()
    {
        if (!Email.Contains("@")) return "Email inválido";
        using (var conn = new SqlConnection())
        {
            var cmd = new SqlCommand();

            conn.ConnectionString = "connString";
            cmd.Connection = conn;
            cmd.CommandType = CommandType.Text;
            cmd.CommandText = "INSERT INTO ... VALUES (@nome, @email)";

            cmd.Parameters.AddWithValue("nome", Nome);
            cmd.Parameters.AddWithValue("email", Email);

            conn.Open();
            cmd.ExecuteNonQuery();
        }

        return "Adicionado na base!";
    }
    
    // a propria classe envia email
    public string EnviaEmail() { // logica qualquer de envio de email }
}
```

Correção do princípio
```csharp
public class ClasseDominio
{
    public string Nome { get; set; }
    public string Email { get; set; }
}

public class ServicoEmail(ClasseDominio cliente)
{
    public void EnviaEmail() { // logica qualquer de envio de email }
}

public class Repositorio(ClasseDominio cliente)
{
    public string AdicionaNaBase()
    {
        if (!cliente.Email.Contains("@")) return "Email inválido";

        using (var conn = new SqlConnection()) { // logica do save }

        return "Adicionado na base!";
    }
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]