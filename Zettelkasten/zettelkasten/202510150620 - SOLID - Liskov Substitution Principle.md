# Unique Identifier
202510150620

# Tag
#SOLID 

# Body
> Versão clássica 88 - Se, para cada objeto $o_1$ do tipo $S$, existir um objeto $o_2$ do tipo T de modo que para todos os programas $P$ definidos em termo de $T$ o comportamento de $P$ é inalterado quando substituímos $o_1$ por $o_2$. Então, $S$ é um subtipo de $T$.

> Versão mais facil 94 - Seja $\phi(x)$ alguma propriedade provável de objetos $x$ do tipo $T$. Então, deve ser verdade que $\phi(y)$ para todos os objetos $y$ do tipo $S$ quando $S$ for um subtipo de $T$.

> Versão para burros - Subclasses devem ser substitutos válidos para suas superclasses.

Aqui vale destacar que a maioria das traduções literais aponta que a classe pai deve ser capaz de substituir a classe filha. Mas o foco é o contrário.

Como Uncle bob mesmo explica: Se temos uma função $f$ que recebe como argumento a classe $B$ e passamos no lugar uma classe $D$ que é derivada de $B$. A função $f$ não deve mudar seu comportamento.


# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]
https://objectmentor.com/resources/articles/lsp.pdf
https://www.cs.tufts.edu/~nr/cs257/archive/barbara-liskov/data-abstraction-and-hierarchy.pdf
https://dl.acm.org/doi/pdf/10.1145/197320.197383 (artigo: A Behavioral Notion of Subtyping - 1994)
Agile Principles, Patterns, and Practices in C# cap 10