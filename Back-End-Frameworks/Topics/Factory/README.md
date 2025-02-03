# Factory Design Pattern

The _Factory_ design pattern is a creational pattern. A "factory" is a superclass whose subclasses can influence which parameters are used to create an object. The factory superclass does two things:

- creates objects using a **hidden** superclass method
- refers to the created object through a **common** interface

The goal is to reduce code and minimize technical debt. Mainly, it should reduce the creation of new objects using the `new` keyword, for example:

```js
const bear = new Bear();
const parrot = new Parrot();
const goldfish = new Goldfish();
// etc.
```

---

## Use Case

The factory design pattern addresses problems that arise when object creation becomes complex or depends on dynamic conditions. This pattern separates the logic of creating objects from their usage, allowing the system to be more flexible and easier to maintain.

Three components in the Factory pattern:

1. **Product**: The object being created, which has a common interface, hidden from the client.
2. **Factory**: The class that contains the method for creating objects, typically hidden from the client.
3. **Client**: The class that uses the factory to create objects. This is the part that utilizes the factory.

---

## Example

### Cat Superclass ("Product" Component)

```js
// Superclass for a common interface
class Cat {
  constructor(name, age, color) {
    this.name = name;
    this.age = age;
    this.color = color;
  }
  introduce() {
    console.log(
      `My cat's name is ${this.name}, he is ${this.age} years old, and his fur color is ${this.color}.`
    );
  }
}
```

### Factory Class ("Factory" Component)

```js
class CatFactory {
  createCat(name, age, color) {
    // Factories should always contain at least a 'create()' method.
    return new Cat(name, age, color);
  }
}
```

The factory can also be implemented as a function, yielding the same result.

```js
function CatFactory(name, age, color) {
  return new Cat(name, age, color);
}
```

### Using the Factory ("Client" Component)

```js
const factory = new CatFactory();
const myCat = factory.createCat("Tom", 3, "gray");
const myOtherCat = factory.createCat("Max", 2, "white");
myCat.introduce(); // My cat's name is Tom, he is 3 years old, and his fur color is gray.
myOtherCat.introduce(); // My cat's name is Max, he is 2 years old, and his fur color is white.
```

---

## More Complex Example

In the previous example, we dealt only with cats. Now, let’s modify things to accommodate both cats and dogs.

### Product

```js
// Superclass for a common interface
class Animal {
  constructor(name, age, color, type) {
    this.name = name;
    this.age = age;
    this.color = color;
    this.type = type; // Adding the type of animal
  }
  introduce() {
    console.log(
      `My pet's name is ${this.name}, he is ${this.age} years old, and he is ${this.color} in color.`
    );
  }
  logActivity() {
    console.log(
      `Animal type: ${this.type}, activity: ${this.currentActivity()}`
    );
  }
  currentActivity() {
    return "Normal activity";
  }
}
```

### Subclasses

In comparison to the previous example, we now add subclasses to the _Animal_ class. This allows us to add unique properties as needed.

```js
class Cat extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Cat"); // Setting the type immediately since this class corresponds to that animal
  }
  currentActivity() {
    return "Playing with a toy mouse";
  }
}

class Dog extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Dog");
  }
  currentActivity() {
    return "Running around outside";
  }
}
```

### Factory

Here, I also add the _'type'_, which distinguishes between the two animals being created.

```js
class AnimalFactory {
  createAnimal(type, name, age, color) {
    if (type === "Cat") {
      return new Cat(name, age, color);
    } else if (type === "Dog") {
      return new Dog(name, age, color);
    } else {
      throw new Error("Invalid animal type"); // Our factory currently does not support other animals.
    }
  }
}
```

### Client

```js
const factory = new AnimalFactory();
const myCat = factory.createAnimal("Cat", "Tom", 3, "gray");
const myDog = factory.createAnimal("Dog", "Rex", 5, "brown");

myCat.introduce();
myDog.introduce();

myCat.logActivity(); // Animal type: Cat, activity: Playing with a toy mouse
myDog.logActivity(); // Animal type: Dog, activity: Running around outside
```

---

## Exercise

**Description**: The code must save company employees in a database. The database describes employees with three properties: name, job, and management level.

**Tasks**: Create a Product, a Factory for producing the product, and create objects through the factory into a "database" (the database here is an empty array `[]`).

**Expected Output**: The result of `console.log(database)` should be:

```json
[
  { "name": "John", "job": "Team lead", "level": "Senior" },
  { "name": "Mary", "job": "Developer", "level": "Junior" },
  { "name": "Juku", "job": "Tester", "level": "Intern" }
]
```

---

**Sources**:

- [Oodesign - factory pattern](https://www.oodesign.com/factory-pattern)
- [Refactoring Guru - factory method](https://refactoring.guru/design-patterns/factory-method)

**Author: Taavi Ansper**

## Factory Design Pattern Using a Functional Approach

The `Factory` design pattern can also be effectively utilized using a functional approach. The simplest way is to create a function that returns a new object. For example:

```js
function createCat(name, age, color) {
  return {
    name,
    age,
    color,
    introduce() {
      console.log(
        `My cat's name is ${this.name}, he is ${this.age} years old, and his fur color is ${this.color}.`
      );
    },
  };
}

const myCat = createCat("Tom", 3, "gray");
myCat.introduce(); // My cat's name is Tom, he is 3 years old, and his fur color is gray.
```


# Factory Tasarım Deseni

_Factory_ (Fabrika) tasarım deseni bir **oluşturucu (creational)** desendir. "Fabrika" burada bir üst sınıftır ve alt sınıflar, hangi parametrelerin bir nesne oluşturmak için kullanılacağını belirleyebilir. Fabrika üst sınıfı iki şey yapar:

- **Gizli** bir üst sınıf metodu kullanarak nesneler oluşturur.
- Oluşturulan nesneye **ortak** bir arayüz üzerinden referans verir.

Amaç, kodu azaltmak ve teknik borcu en aza indirmektir. Özellikle `new` anahtar kelimesinin gereksiz kullanımını azaltmaya yöneliktir. Örneğin:

```js
const bear = new Bear();
const parrot = new Parrot();
const goldfish = new Goldfish();
// vb.
```

---

## Kullanım Durumu

Factory tasarım deseni, nesne oluşturma işlemi karmaşık hale geldiğinde veya dinamik koşullara bağlı olduğunda ortaya çıkan sorunları çözer. Bu desen, nesne oluşturma mantığını kullanımından ayırarak sistemin daha esnek ve bakımı daha kolay hale gelmesini sağlar.

Factory deseninde üç bileşen bulunur:

1. **Ürün (Product)**: Oluşturulan nesnedir ve istemciden gizlenmiş ortak bir arayüze sahiptir.
2. **Fabrika (Factory)**: Nesne oluşturma metodunu içeren sınıftır ve genellikle istemciden gizlenir.
3. **İstemci (Client)**: Fabrikayı kullanarak nesneleri oluşturan bölümdür.

---

## Örnek

### Kedi Üst Sınıfı ("Ürün" Bileşeni)

```js
// Ortak bir arayüz için üst sınıf
class Cat {
  constructor(name, age, color) {
    this.name = name;
    this.age = age;
    this.color = color;
  }
  introduce() {
    console.log(
      `Kedimin adı ${this.name}, ${this.age} yaşında ve tüy rengi ${this.color}.`
    );
  }
}
```

### Fabrika Sınıfı ("Fabrika" Bileşeni)

```js
class CatFactory {
  createCat(name, age, color) {
    return new Cat(name, age, color);
  }
}
```

Fabrika ayrıca bir fonksiyon olarak da uygulanabilir:

```js
function CatFactory(name, age, color) {
  return new Cat(name, age, color);
}
```

### Fabrikanın Kullanımı ("İstemci" Bileşeni)

```js
const factory = new CatFactory();
const myCat = factory.createCat("Tom", 3, "gri");
const myOtherCat = factory.createCat("Max", 2, "beyaz");
myCat.introduce(); // Kedimin adı Tom, 3 yaşında ve tüy rengi gri.
myOtherCat.introduce(); // Kedimin adı Max, 2 yaşında ve tüy rengi beyaz.
```

---

## Daha Karmaşık Bir Örnek

Önceki örnekte sadece kediler vardı. Şimdi ise hem kedileri hem de köpekleri destekleyecek şekilde değiştirelim.

### Ürün

```js
// Ortak bir arayüz için üst sınıf
class Animal {
  constructor(name, age, color, type) {
    this.name = name;
    this.age = age;
    this.color = color;
    this.type = type;
  }
  introduce() {
    console.log(
      `Evcil hayvanımın adı ${this.name}, ${this.age} yaşında ve rengi ${this.color}.`
    );
  }
  logActivity() {
    console.log(
      `Hayvan türü: ${this.type}, aktivite: ${this.currentActivity()}`
    );
  }
  currentActivity() {
    return "Normal aktivite";
  }
}
```

### Alt Sınıflar

```js
class Cat extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Kedi");
  }
  currentActivity() {
    return "Oyuncak fare ile oynuyor";
  }
}

class Dog extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Köpek");
  }
  currentActivity() {
    return "Dışarıda koşuyor";
  }
}
```

### Fabrika

```js
class AnimalFactory {
  createAnimal(type, name, age, color) {
    if (type === "Kedi") {
      return new Cat(name, age, color);
    } else if (type === "Köpek") {
      return new Dog(name, age, color);
    } else {
      throw new Error("Geçersiz hayvan türü");
    }
  }
}
```

### İstemci

```js
const factory = new AnimalFactory();
const myCat = factory.createAnimal("Kedi", "Tom", 3, "gri");
const myDog = factory.createAnimal("Köpek", "Rex", 5, "kahverengi");

myCat.introduce();
myDog.introduce();

myCat.logActivity(); // Hayvan türü: Kedi, aktivite: Oyuncak fare ile oynuyor
myDog.logActivity(); // Hayvan türü: Köpek, aktivite: Dışarıda koşuyor
```

---

## Alıştırma

**Açıklama**: Kod, şirket çalışanlarını bir veritabanında saklamalıdır. Veritabanı çalışanları üç özellik ile tanımlar: isim, iş pozisyonu ve yönetim seviyesi.

**Görevler**: Bir **Ürün**, bir **Fabrika** ve oluşturulan nesneleri bir "veritabanına" (boş bir dizi `[]`) ekleyen bir istemci oluşturun.

**Beklenen Çıktı**:

```json
[
  { "name": "John", "job": "Takım lideri", "level": "Kıdemli" },
  { "name": "Mary", "job": "Geliştirici", "level": "Junior" },
  { "name": "Juku", "job": "Test uzmanı", "level": "Stajyer" }
]
```

---

**Kaynaklar**:

- [Oodesign - factory pattern](https://www.oodesign.com/factory-pattern)
- [Refactoring Guru - factory method](https://refactoring.guru/design-patterns/factory-method)

**Yazar: Taavi Ansper**

## Fonksiyonel Yaklaşım ile Factory Tasarım Deseni

Factory tasarım deseni, fonksiyonel bir yaklaşımla da kullanılabilir. En basit haliyle, bir fonksiyon oluşturarak yeni nesneler döndürmek mümkündür. Örneğin:

```js
function createCat(name, age, color) {
  return {
    name,
    age,
    color,
    introduce() {
      console.log(
        `Kedimin adı ${this.name}, ${this.age} yaşında ve tüy rengi ${this.color}.`
      );
    },
  };
}

const myCat = createCat("Tom", 3, "gri");
myCat.introduce();
```

