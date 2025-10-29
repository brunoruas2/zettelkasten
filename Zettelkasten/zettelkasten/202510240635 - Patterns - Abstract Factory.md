# Unique Identifier
202510240635

# Tag
#DesignPattern 

# Body
[[202510230627 - Design Patterns]]

O objetivo desse pattern é criar uma interface de criação de famílias de objetos relacionados/dependentes sem implementar as classes concretas. A ideia principal é garantir que os objetos finais (chamados de produtos) sejam todos de um mesmo grupo (que vai ser definido pela factory).

É indicado quando:
- Um sistema de ser independente de como seus produtos são criados, compostos e representados
- O sistema deve ser configurado com segregação de **famílias de produtos** <- Esse é o ponto chave do pattern
- Os produtos de cada família devem ser usados juntos (deve ter uma trava para misturar classes de diferentes famílias)
- Os produtos devem ser expostos aos clientes por meio de uma class library revelando apenas as interfaces dos mesmos em implementação

Principais características:
- O client só depende de abstrações (tanto de produtos quanto de fábricas)
- AbstractFactory é a interface que o client usa para definir qual fábrica concreta será criada
- Decidindo qual ConcreteFactory será usada, automaticamente decidimos quais produtos tipos de produtos podem ser criados

Estrutura do pattern usando [[202510251523 - UML - Padrão de Notação]]
![[abstract_factory.svg]]
Aqui tem um exemplo em python -> [[202510280654 - Exemplo de Abstract Factory]]
# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
https://www.dofactory.com/net/design-patterns
https://refactoring.guru/design-patterns
Design Patterns: Elements of Reusable Object-Oriented