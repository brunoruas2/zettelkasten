# Unique Identifier
202510170652

# Tag
#SOLID 

# Body
> Módulos de alto nível não devem depender de módulo de baixo nível. Ambos devem depender de abstrações. E abstrações não devem depender de detalhes mas detalhes devem depender de abstrações.

> Dependa sempre de uma abstração e não de uma implementação.

```csharp
// violacao
    // Classe de baixo nível
    public class EmailService
    {
        public void EnviarEmail(string mensagem) { // void }
    }

    // Classe de alto nível
    public class PedidoService
    {
        private EmailService _emailService;

        public PedidoService()
        {
			// classe de alto nivel dependendo da de baixo nivel
            _emailService = new EmailService();
        }

        public void ProcessarPedido()
        {
            _emailService.EnviarEmail("Pedido processado com sucesso!");
        }
    }
```

Ajuste da violação

```csharp
    public interface IEmailService
    {
        void EnviarEmail(string mensagem);
    }

    public class EmailService : IEmailService
    {
        public void EnviarEmail(string mensagem)
        {
            Console.WriteLine($"Enviando email: {mensagem}");
        }
    }

    public class PedidoService
    {
		// aqui estamos dependendo apenas da abstracao
        private readonly IEmailService _emailService;

        // Injecao de dependencia via construtor implementando o DIP
        public PedidoService(IEmailService emailService)
        {
            _emailService = emailService;
        }

        public void ProcessarPedido()
        {
            Console.WriteLine("Processando pedido...");
            _emailService.EnviarEmail("Pedido processado com sucesso!");
        }
    }
```

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]