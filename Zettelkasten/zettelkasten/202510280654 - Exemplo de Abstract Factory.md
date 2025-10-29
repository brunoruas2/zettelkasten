# Unique Identifier
202510280654

# Tag
#DesignPattern 

# Body
[[202510240635 - Patterns - Abstract Factory]]

Para dar mais senso de aprendizado ao pattern de abstract factory, vou usar um exemplo de criação de equipamentos para personagens em um jogo (WoW).

Cada personagem possui uma classe: Humano, Orc ou Mago. Cada classe possui diferente armor e weapons.

Já conseguimos ver que temos uma relação de variação de equipamentos e classes baseada na classe. Cenário ideal para uso desse pattern.

Primeiro vamos criar os objetos finais (armor e weapons) e depois ir construindo nossa factory para, no final, criarmos nossa factory abstrata.

```typescript
// interface das weapon
export interface Weapon {
  usefulFunction(): string;
}

// weapons
import { Weapon } from "./weapon.interface";

// humano
export class Sword implements Weapon {
  public usefulFunction(): string {
    return "The result of the Sword";
  }
}

// orc
export class Axe implements Weapon {
  public usefulFunction(): string {
    return "The result of the Axe";
  }
}

// mago
export class MageFireball implements Weapon {
  public usefulFunction(): string {
    return "The result of the MageFireball";
  }
}
```

Agora vamos fazer a mesma lógica para armor.

```typescript
// interface de armor
import { Weapon } from "../weapons/weapon.interface";

export interface Armor {
  usefulFunction(): string;
  usefulFunctionWithWeapon(collaborator: Weapon): string; // armor e weapon juntos
}

// armors
import { Armor } from "./armor-interface";

// humano
export class BodyArmor implements Armor {
  public usefulFunction(): string {
    return "The result of the BodyArmor";
  }

  public usefulFunctionWithWeapon(collaborator: Weapon): string {
    const result = collaborator.usefulFunction();
    return `The result of the BodyAmor collaborating with the (${result})`;
  }
}

// orc
export class OrcArmor implements Armor {
  public usefulFunction(): string {
    return "The result of the OrcArmor";
  }

  public usefulFunctionWithWeapon(collaborator: Weapon): string {
    const result = collaborator.usefulFunction();
    return `The result of the OrcAmor collaborating with the (${result})`;
  }
}

// mago
export class Cloak implements Armor {
  public usefulFunction(): string {
    return "The result of the Cloak";
  }

  public usefulFunctionWithWeapon(collaborator: Weapon): string {
    const result = collaborator.usefulFunction();
    return `The result of the Cloak collaborating with the (${result})`;
  }
}
```

Agora que temos os "produtos" vamos criar as factories. São as factories que vão definir **quais** produtos serão criados.

```typescript
// interface
import { Armor } from "./armor/armor-interface";
import { Weapon } from "./weapons/weapon.interface";

export interface AbstractFactory {
  createWeapon(): Weapon;
  createArmor(): Armor;
}

// factories
import { AbstractFactory } from "./abstract-factory";
import { Armor } from "./armor/armor-interface";
import { BodyArmor } from "./armor/body-armor.model";
import { Sword } from "./weapons/sword.model";
import { Weapon } from "./weapons/weapon.interface";

// humano
export class WarriorFactory implements AbstractFactory {
  public createWeapon(): Weapon {
    return new Sword();
  }

  public createArmor(): Armor {
    return new BodyArmor();
  }
}

// orc
export class OrcFactory implements AbstractFactory {
  public createWeapon(): Weapon {
    return new Axe();
  }

  public createArmor(): Armor {
    return new OrcArmor();
  }
}

// mago
export class MageFactory implements AbstractFactory {
  public createWeapon(): Weapon {
    return new MageFireball();
  }

  public createArmor(): Armor {
    return new Cloak();
  }
}
```

Agora temos tudo necessário para aplicar nosso pattern.

```typescript
import { AbstractFactory } from "./abstract-factory";
import { MageFactory } from "./mage-factory";
import { OrcFactory } from "./orc-factory";
import { WarriorFactory } from "./warrior-factory";

function clientCode(factory: AbstractFactory) {
  const sword = factory.createWeapon();
  const armor = factory.createArmor();

  console.log(armor.usefulFunction());
  console.log(armor.usefulFunctionWithWeapon(sword));
}

console.log("Client: WarriorFactory");
clientCode(new WarriorFactory());

console.log("----------------");

console.log("Client: OrcFactory");
clientCode(new OrcFactory());

console.log("----------------");

console.log("Client: MageFactory");
clientCode(new MageFactory());
```

# Footer / Reference
https://dev.to/carlillo/understanding-design-patterns-abstract-factory-23e7