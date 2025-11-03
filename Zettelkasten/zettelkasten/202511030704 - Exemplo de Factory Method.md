# Unique Identifier
202511030704

# Tag
#DesignPattern 

# Body
[[202510240635 - Patterns - Abstract Factory]]

```typescript
// interface de produto
export interface Product {
   operation(): string;
}

// classes concretas que vao ser criadas
export class Burger implements Product {
  public operation(): string {
    return "Burger: Results";
  }
}

export class Pizza implements Product {
    public operation(): string {
        return 'Pizza: Operation';
    }
}

// classe de criacao abstrata
export abstract class Creator {

    public abstract factoryMethod(): Product;

    public someOperation(): string {
        const product = this.factoryMethod();
        return `Creator: The same creator's code has just worked with ${product.operation()}`;
    }
}

// clases concretas
export class PizzaCreator extends Creator {
    public factoryMethod(): Product { // aqui ele ta dando override
        return new Pizza();
    }
}

export class BurgerCreator extends Creator {
  public factoryMethod(): Product {
    return new Burger();
  }
}
```

No final, temos esse código na classe de cliente

```typescript
import { BurgerCreator } from "./burger-creator";
import { Creator } from "./creator";
import { KebabCreator } from "./kebab-creator";
import { PizzaCreator } from "./pizza-creator";

function client(creator: Creator) {
    console.log('Client: I\'m not aware of the creator\'s class, but it still works.');
    console.log(creator.someOperation());
}

// instancio os criadores de objetos
const pizzaCreator = new PizzaCreator();
const burgerCreator = new BurgerCreator();

console.log('App: Launched with the PizzaCreator');
client(pizzaCreator);

console.log('----------');

console.log('App: Launched with the BurgerCreator');
client(burgerCreator);
```
# Footer / Reference
Design Patterns: Elements of Reusable Object-Oriented