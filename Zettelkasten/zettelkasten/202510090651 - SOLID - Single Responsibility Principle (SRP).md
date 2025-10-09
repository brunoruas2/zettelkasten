# Unique Identifier
202510090651

# Tag
#SOLID

# Body
Uma classe só deve ter 1 motivo para ser modificada, ou seja, deve ter apenas 1 responsabilidade. Até pode ter mais de 1 método mas sempre relacionados à uma única responsabilidade.

Aqui vale um disclaimer: Existem classes de serviço que vão atuar em várias frentes mas **nunca** com a implementação dentro delas. Por exemplo, um service de cliente pode ter uma parte que salva o cliente no banco usando o repositório, envia um email usando um service de email confirmando o salvamento e etc, mas a implementação não está no service em si.

Exemplo de violação
```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.Net.Mail;

public class classeErroSrp
{
    public string Nome { get; set; }
    public string Email { get; set; }

	// a propria classe esta interagindo com o banco
    public string AdicionaNaBase()
    {
        if (!Email.Contains("@"))
            return "Email inválido";

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
    public string EnviaEmail()
    {
	    // logica qualquer de envio de email
    }
}
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]