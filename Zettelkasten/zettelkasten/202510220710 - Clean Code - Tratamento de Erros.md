# Unique Identifier
202510220710

# Tag
#CleanCode 

# Body
[[202510220620 - Clean Code]]

Existem regras gerais que se aplicam a qualquer linguagem:
- Tratar e prever possíveis exceções
	- Idealmente sem usar um monte de `try catch` por meio de um handler global
- Retorne exceptions e não códigos de erro (ex http 404)
- Informe o máximo possível do contexto na exception (além do código de erro) a call stack ajuda muito
- Se possível, crie uma classe herdada da exception base class para capturar cenários específicos
- Não retorne `null` para evitar `catch` mudo

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]