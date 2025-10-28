# Unique Identifier
202510280654

# Tag
#DesignPattern 

# Body
[[202510240635 - Patterns - Abstract Factory]]

```python
from abc import ABC, abstractmethod

# ----- Abstract Products -----
class Chair(ABC):
    @abstractmethod
    def sit_on(self):
        pass

class Sofa(ABC):
    @abstractmethod
    def lie_on(self):
        pass


# ----- Concrete Products -----
class VictorianChair(Chair):
    def sit_on(self):
        return "Você se senta em uma cadeira vitoriana elegante."

class ModernChair(Chair):
    def sit_on(self):
        return "Você se senta em uma cadeira moderna minimalista."

class VictorianSofa(Sofa):
    def lie_on(self):
        return "Você deita em um sofá vitoriano luxuoso."

class ModernSofa(Sofa):
    def lie_on(self):
        return "Você deita em um sofá moderno e confortável."


# ----- Abstract Factory -----
class FurnitureFactory(ABC):
    @abstractmethod
    def create_chair(self) -> Chair:
        pass

    @abstractmethod
    def create_sofa(self) -> Sofa:
        pass


# ----- Concrete Factories -----
class VictorianFurnitureFactory(FurnitureFactory):
    def create_chair(self) -> Chair:
        return VictorianChair()

    def create_sofa(self) -> Sofa:
        return VictorianSofa()

class ModernFurnitureFactory(FurnitureFactory):
    def create_chair(self) -> Chair:
        return ModernChair()

    def create_sofa(self) -> Sofa:
        return ModernSofa()


# ----- Client Code -----
def client_code(factory: FurnitureFactory):
    chair = factory.create_chair()
    sofa = factory.create_sofa()

    print(chair.sit_on())
    print(sofa.lie_on())


# ----- Testando -----
if __name__ == "__main__":
    print("Móveis vitorianos:")
    client_code(VictorianFurnitureFactory())

    print("\nMóveis modernos:")
    client_code(ModernFurnitureFactory())
```

# Footer / Reference
GPT