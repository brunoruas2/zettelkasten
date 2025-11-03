# Unique Identifier
202510290617

# Tag
#DesignPattern 

# Body
[[202510230627 - Design Patterns]]

Parece uma versão mais simples do [[202510240635 - Patterns - Abstract Factory]] só que em 1 camada só. A ideia aqui é criar uma classe/interface que é responsável por criar os objetos para a classe cliente (assim não precisamos lidar com o construtor).

A ideia aqui é centralizar o trabalho de criar classes deixando todas as [[202510181406 - DI - Injeção de Dependência]] padronizadas (como logger, por exemplo) e, ao mesmo tempo, reduzir a complexidade de expansão do sistema porque o overhead de criação está centralizado em uma classe.

É indicado quando:
- Não se sabe a priori os tipos de objetos que o client precisa usar.

![[factory_method.svg]]

Partes principais:
- Product - Interface comum aos objetos
- ProductA/B - Implementação da interface
- Creator - Classe abstrata
- ConcreteCreatorA/B - Classe que cria o objeto específico via override do FactoryMethod()

Vale observar que esse pattern é um caso específico do pattern Template-Method.
#TODO - fazer o link quando tiver o zettel desse pattern.

Exemplo em código -> [[202511030704 - Exemplo de Factory Method]]
# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
https://www.dofactory.com/net/design-patterns
https://refactoring.guru/design-patterns
Design Patterns: Elements of Reusable Object-Oriented