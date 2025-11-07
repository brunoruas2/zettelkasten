# Unique Identifier
202511070629

# Tag
#DesignPattern 

# Body
[[202510230627 - Design Patterns]]

O objetivo é garantir que uma determinada classe possua apenas **uma instância** que será o global point of access da aplicação.

Direto do livro:
> Global variables makes an object accessible, but doesn't keep you from instantiating multiple objects. \[...\] A better solution is to make the class itself responsible for keeping track of its sole instance.

Estrutura do pattern
![[singleton.svg]]

# Footer / Reference
