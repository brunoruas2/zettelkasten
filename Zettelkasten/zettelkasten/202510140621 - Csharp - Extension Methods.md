# Unique Identifier
202510140621

# Tag
#Csharp 

# Body
Em C# podemos usar técnicas para expandir a capacidade de uma classe inserindo métodos de maneira indireta por meio de uma **sintaxe açucarada** e não composição nem herança.

```csharp
// antes do c# 14
namespace CustomExtensionMethods;

public static class MyExtensions
{
    public static int WordCount(this string str) =>
        str.Split([' ', '.', '?'], StringSplitOptions.RemoveEmptyEntries).Length;

// depois do c# 14 temos um token para isso
    extension(string str)
    {
        public int WordCount() =>
            str.Split([' ', '.','?'],StringSplitOptions.RemoveEmptyEntries).Length;
    }
}

// em ambos os casos o uso e igual
string s = "Hello Extension Methods";
int i = s.WordCount(); // veja que parece que string agora possui esse metodo
```


# Footer / Reference
https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods
[[REF - Desenvolvedor.io - Curso Arquitetura]]