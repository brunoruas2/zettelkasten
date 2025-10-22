# Unique Identifier
202510220658

# Tag
#CleanCode 

# Body
[[202510220620 - Clean Code]]

Boas práticas:
1. Nome de classes devem ser substantivos
2. Métodos no infinitivo (`AdicionarCliente`, por exemplo)
3. Não seja genérico (`public void Calcula()` por exemplo)
4. Menos é mais (valores ideais)
	1. 20 linhas por método 
	2. 100 chars por linha
	3. 500 linhas por classe
5. Extraia trechos em métodos privados (isso deixa ele menor e ainda controlado)
6. Métodos devem fazer apenas 1 coisa
	1. Se fizer mais de 1 coisa -> quebre em outros métodos
7. Evitar muitos parâmetros (melhor passar um dict caso precise de muitos ou uma classe de transferência)
8. Não deixe seus métodos mentir (fazendo algo que não está no título)
9. Leia seu método como um livro (se tiver confuso, está ruim)
10. Boa indentação (pois isso denota hierarquia)

> A primeira regra é que métodos devem ser pequenos. A segunda regra é que devem ser menores ainda. Uncle Bob.

> Deixe a área de acampamento mais limpa do que você encontrou. Regra dos Escoteiros.

# Footer / Reference
[[REF - Desenvolvedor.io - Curso Arquitetura]]