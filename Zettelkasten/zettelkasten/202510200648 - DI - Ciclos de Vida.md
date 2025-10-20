# Unique Identifier
202510200648

# Tag
#InjecaoDeDependencia 

# Body
[[202510181406 - DI - Injeção de Dependência]]

No .NET temos a capacidade de gerenciar o ciclo de vida dos objetos injetados via container de DI. Na documentação oficial temos 3 tipos de ciclo de vida:

- Transient - Um novo objeto é criado toda vez que o container é solicitado.
- Scoped - Um objeto é criado e reusado sempre que necessário enquanto a chamada (connection) estiver ativa.
- Singleton - Uma única instância para toda a aplicação.

Como regra de bolso, usamos Scoped para aplicações web. Se não soubermos muito sobre o contexto de uso, o mais seguro (e caro) é usar Transient. Singleton só deve ser usado se tivermos certeza que aquela classe é referente ao aplicativo todo e nunca baseada por session de usuário.

TODO - implementar um ASP.NET app simples que retornar um guid para cada ciclo de vida para testar em um retorno na tela comparando os guids para provar os clicos de vida (aula de ciclo de vida 04:22)

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection#service-lifetimes