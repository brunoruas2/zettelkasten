# Unique Identifier
202510020643

# Tag
#Dotnet #Csharp 

# Body
Estrutura básica dos folders:
```text

bin/
obj/ <- pasta usada para debug do app
Arquivo.csproj
Program.cs
```

Arquivo csproj
```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType> <!-- tipo de saida do projeto -->
    <TargetFramework>net9.0</TargetFramework> <!-- qual version do framework -->
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

Escopo do programa é usado para definir como um projeto é definido. Basicamente, temos:
- Usings <- Imports de funções
- Namespaces <- Separação lógica (na compilação vira 1 dll só)
- Classe
- Main(string [] args) <- Método de entrada do runtime

# Footer / Reference
[[REF - Balta.io]]