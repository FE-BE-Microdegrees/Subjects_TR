# Mocha Testing Framework

Mocha is a popular JavaScript testing framework that allows you to write and run tests in both server-side (Node.js) and client-side (browser) environments. Mocha is flexible and extensible, supporting various testing styles, including BDD (Behavior-Driven Development) and TDD (Test-Driven Development).

![Mocha](Mocha.webp)

Image source: Dall-E by OpenAI

- [Mocha Testing Framework](#mocha-testing-framework)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Mocha?](#what-is-mocha)
  - [Advantages of Mocha](#advantages-of-mocha)
  - [Installing and Setting Up Mocha](#installing-and-setting-up-mocha)
    - [1. Installing Mocha](#1-installing-mocha)
      - [Global Installation](#global-installation)
      - [Project-Level Installation](#project-level-installation)
    - [2. Creating a Test File](#2-creating-a-test-file)
  - [Writing Tests with Mocha](#writing-tests-with-mocha)
    - [Example: Simple Test](#example-simple-test)
      - [`sum.js` - Function to Test](#sumjs---function-to-test)
      - [`test/test.js` - Mocha Test](#testtestjs---mocha-test)
    - [Running Tests](#running-tests)
  - [Asynchronous Tests](#asynchronous-tests)
    - [Example: Asynchronous Test with Callbacks](#example-asynchronous-test-with-callbacks)
      - [`asyncFunction.js` - Asynchronous Function](#asyncfunctionjs---asynchronous-function)
      - [`test/asyncTest.js` - Mocha Test](#testasynctestjs---mocha-test)
    - [Example: Asynchronous Test with Promises](#example-asynchronous-test-with-promises)
      - [`asyncPromise.js` - Asynchronous Function](#asyncpromisejs---asynchronous-function)
      - [`test/asyncPromiseTest.js` - Mocha Test](#testasyncpromisetestjs---mocha-test)
  - [Using Chai Assertion Library](#using-chai-assertion-library)
    - [Installing Chai](#installing-chai)
    - [Example: Using Chai](#example-using-chai)
      - [`test/chaiTest.js` - Mocha Test with Chai](#testchaitestjs---mocha-test-with-chai)
  - [Additional Mocha Features](#additional-mocha-features)
    - [Hooks](#hooks)
      - [Example: Using Hooks](#example-using-hooks)

## Learning Outcomes

By the end of this material, learners should be able to:

- explain what Mocha is and why it is used;
- install and set up the Mocha testing framework;
- write and run basic tests using Mocha;
- use assertion libraries like Chai alongside Mocha.

## What is Mocha?

Mocha is a JavaScript testing framework designed for writing and running asynchronous tests. It provides a simple and flexible way to organize and manage tests and integrates well with other tools and frameworks.

## Advantages of Mocha

- **Flexibility:** Supports various testing styles and methodologies.
- **Asynchronicity:** Easy to write and run asynchronous tests.
- **Extensibility:** Integrates well with other tools and frameworks, such as Chai and Sinon.
- **Good documentation and community:** A large user base and plenty of resources.

## Installing and Setting Up Mocha

### 1. Installing Mocha

You can install Mocha either globally or at the project level using npm.

#### Global Installation

```bash
npm install --global mocha
```

#### Project-Level Installation

```bash
npm install --save-dev mocha
```

### 2. Creating a Test File

Create a directory named `test` in the root of your project and create a test file inside it, for example, `test.js`.

```bash
mkdir test
cd test
touch test.js
```

## Writing Tests with Mocha

Mocha uses BDD style functions to write tests, including `describe`, `it`, and `before`, `after`, `beforeEach`, `afterEach`.

### Example: Simple Test

#### `sum.js` - Function to Test

```javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

#### `test/test.js` - Mocha Test

```javascript
const assert = require("assert");
const sum = require("../sum");

describe("Sum Function", function () {
  it("should return 3 when the inputs are 1 and 2", function () {
    assert.strictEqual(sum(1, 2), 3);
  });

  it("should return -1 when the inputs are -2 and 1", function () {
    assert.strictEqual(sum(-2, 1), -1);
  });
});
```

### Running Tests

Run the tests using Mocha from the command line.

```bash
npx mocha
```

## Asynchronous Tests

Mocha supports writing asynchronous tests using callbacks or promises.

### Example: Asynchronous Test with Callbacks

#### `asyncFunction.js` - Asynchronous Function

```javascript
function asyncFunction(callback) {
  setTimeout(() => {
    callback(null, "Hello World");
  }, 1000);
}

module.exports = asyncFunction;
```

#### `test/asyncTest.js` - Mocha Test

```javascript
const assert = require("assert");
const asyncFunction = require("../asyncFunction");

describe("AsyncFunction", function () {
  it('should return "Hello World" after 1 second', function (done) {
    asyncFunction(function (err, result) {
      assert.strictEqual(result, "Hello World");
      done();
    });
  });
});
```

### Example: Asynchronous Test with Promises

#### `asyncPromise.js` - Asynchronous Function

```javascript
function asyncPromise() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Hello World");
    }, 1000);
  });
}

module.exports = asyncPromise;
```

#### `test/asyncPromiseTest.js` - Mocha Test

```javascript
const assert = require("assert");
const asyncPromise = require("../asyncPromise");

describe("AsyncPromise", function () {
  it('should return "Hello World" after 1 second', function () {
    return asyncPromise().then((result) => {
      assert.strictEqual(result, "Hello World");
    });
  });
});
```

## Using Chai Assertion Library

Chai is a popular assertion library that can be used with Mocha. Chai supports various assertion styles, including TDD and BDD.

### Installing Chai

Install Chai at the project level.

```bash
npm install --save-dev chai
```

### Example: Using Chai

#### `test/chaiTest.js` - Mocha Test with Chai

```javascript
const chai = require("chai");
const expect = chai.expect;
const sum = require("../sum");

describe("Sum Function", function () {
  it("should return 3 when the inputs are 1 and 2", function () {
    expect(sum(1, 2)).to.equal(3);
  });

  it("should return -1 when the inputs are -2 and 1", function () {
    expect(sum(-2, 1)).to.equal(-1);
  });
});
```

## Additional Mocha Features

### Hooks

Mocha provides hooks (`before`, `after`, `beforeEach`, `afterEach`) that allow you to execute code before and after tests run.

#### Example: Using Hooks

```javascript
describe("Hooks Example", function () {
  before(function () {
    // Executed before all tests
  });

  after(function () {
    // Executed after all tests
  });

  beforeEach(function () {
    // Executed before each test
  });

  afterEach(function () {
    // Executed after each test
  });

  it("test case 1", function () {
    // Test code
  });

  it("test case 2", function () {
    // Test code
  });
});
```


# Mocha Test Çerçevesi

Mocha, hem sunucu tarafı (Node.js) hem de istemci tarafı (tarayıcı) ortamlarında test yazmanıza ve çalıştırmanıza olanak tanıyan popüler bir JavaScript test çerçevesidir. Mocha, BDD (Davranışa Dayalı Geliştirme) ve TDD (Test-Tabanlı Geliştirme) dahil olmak üzere çeşitli test stillerini destekleyen esnek ve genişletilebilir bir yapıya sahiptir.

![Mocha](Mocha.webp)

Görsel kaynağı: Dall-E tarafından OpenAI

- [Mocha Test Çerçevesi](#mocha-test-çerçevesi)
  - [Öğrenme Hedefleri](#öğrenme-hedefleri)
  - [Mocha Nedir?](#mocha-nedir)
  - [Mocha'nın Avantajları](#mochanın-avantajları)
  - [Mocha'yı Yükleme ve Ayarlama](#mochayı-yükleme-ve-ayarlama)
    - [1. Mocha'yı Yükleme](#1-mochayı-yükleme)
      - [Global Yükleme](#global-yükleme)
      - [Proje Seviyesi Yükleme](#proje-seviyesi-yükleme)
    - [2. Bir Test Dosyası Oluşturma](#2-bir-test-dosyası-oluşturma)
  - [Mocha ile Test Yazma](#mocha-ile-test-yazma)
    - [Örnek: Basit Test](#örnek-basit-test)
      - [`sum.js` - Test Edilecek Fonksiyon](#sumjs---test-edilecek-fonksiyon)
      - [`test/test.js` - Mocha Testi](#testtestjs---mocha-testi)
    - [Testleri Çalıştırma](#testleri-çalıştırma)
  - [Asenkron Testler](#asenkron-testler)
    - [Örnek: Geri Çağırma ile Asenkron Test](#örnek-geriye-çağırma-ile-asenkron-test)
      - [`asyncFunction.js` - Asenkron Fonksiyon](#asyncfunctionjs---asenkron-fonksiyon)
      - [`test/asyncTest.js` - Mocha Testi](#testasynctestjs---mocha-testi)
    - [Örnek: Promiseler ile Asenkron Test](#örnek-promiseler-ile-asenkron-test)
      - [`asyncPromise.js` - Asenkron Fonksiyon](#asyncpromisejs---asenkron-fonksiyon)
      - [`test/asyncPromiseTest.js` - Mocha Testi](#testasyncpromisetestjs---mocha-testi)
  - [Chai İddia Kütüphanesini Kullanma](#chai-iddia-kütüphanesini-kullanma)
    - [Chai'yi Yükleme](#chaıyı-yükleme)
    - [Örnek: Chai Kullanımı](#örnek-chai-kullanımı)
      - [`test/chaiTest.js` - Mocha Testi Chai ile](#testchaitestjs---mocha-testi-chai-ile)
  - [Ekstra Mocha Özellikleri](#ekstra-mocha-özellikleri)
    - [Hook'lar](#hooklar)
      - [Örnek: Hook Kullanımı](#örnek-hook-kullanımı)

## Öğrenme Hedefleri

Bu materyalin sonunda öğrenciler şunları yapabilmelidir:

- Mocha'nın ne olduğunu ve neden kullanıldığını açıklamak;
- Mocha test çerçevesini yükleyip ayarlamak;
- Mocha ile temel testler yazıp çalıştırmak;
- Chai gibi iddia kütüphanelerini Mocha ile birlikte kullanmak.

## Mocha Nedir?

Mocha, asenkron testler yazmak ve çalıştırmak için tasarlanmış bir JavaScript test çerçevesidir. Testleri organize etmek ve yönetmek için basit ve esnek bir yol sunar ve diğer araçlar ve çerçevelerle iyi bir şekilde entegre olur.

## Mocha'nın Avantajları

- **Esneklik:** Farklı test stilleri ve metodolojilerini destekler.
- **Asenkronluk:** Asenkron testler yazmak ve çalıştırmak kolaydır.
- **Genişletilebilirlik:** Chai ve Sinon gibi diğer araçlarla iyi bir şekilde entegre olur.
- **İyi dökümantasyon ve topluluk:** Büyük bir kullanıcı kitlesi ve çok sayıda kaynak bulunur.

## Mocha'yı Yükleme ve Ayarlama

### 1. Mocha'yı Yükleme

Mocha'yı global olarak ya da proje seviyesinde npm kullanarak yükleyebilirsiniz.

#### Global Yükleme

```bash
npm install --global mocha
```

### Proje Seviyesi Yükleme
```bash
npm install --save-dev mocha
```
### 2. Bir Test Dosyası Oluşturma
Projenizin kök dizininde test adında bir dizin oluşturun ve içerisine bir test dosyası oluşturun, örneğin `test.js`.

```bash
mkdir test
cd test
touch test.js
```

## Mocha ile Test Yazma
Mocha, `describe`, `it`, `before`, `afte`r, `beforeEach`, `afterEach` gibi BDD stilindeki fonksiyonları kullanarak test yazmanızı sağlar.

## Örnek: Basit Test

`sum.js` - Test Edilecek Fonksiyon
```javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```
`test/test.js` - Mocha Testi
```javascript
const assert = require("assert");
const sum = require("../sum");

describe("Sum Fonksiyonu", function () {
  it("girdi olarak 1 ve 2 verildiğinde 3 döndürmelidir", function () {
    assert.strictEqual(sum(1, 2), 3);
  });

  it("girdi olarak -2 ve 1 verildiğinde -1 döndürmelidir", function () {
    assert.strictEqual(sum(-2, 1), -1);
  });
});
```

## Testleri Çalıştırma
Testleri Mocha ile komut satırından çalıştırabilirsiniz.
```bash
npx mocha
```

## Asenkron Testler

Mocha, geri çağırmalar veya promiseler kullanarak asenkron testler yazılmasını destekler.

### Örnek: Geri Çağırma ile Asenkron Test

#### `asyncFunction.js` - Asenkron Fonksiyon

```javascript
function asyncFunction(callback) {
  setTimeout(() => {
    callback(null, "Merhaba Dünya");
  }, 1000);
}

module.exports = asyncFunction;
```
### `test/asyncTest.js` - Mocha Testi
```javascript
const assert = require("assert");
const asyncFunction = require("../asyncFunction");

describe("AsyncFunction", function () {
  it('1 saniye sonra "Merhaba Dünya" döndürmelidir', function (done) {
    asyncFunction(function (err, result) {
      assert.strictEqual(result, "Merhaba Dünya");
      done();
    });
  });
});
```

### Örnek: Promiseler ile Asenkron Test

## `asyncPromise.js` - Asenkron Fonksiyon
```javascript
function asyncPromise() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Merhaba Dünya");
    }, 1000);
  });
}

module.exports = asyncPromise;
```

## `test/asyncPromiseTest.js` - Mocha Testi
```javascript
const assert = require("assert");
const asyncPromise = require("../asyncPromise");

describe("AsyncPromise", function () {
  it('1 saniye sonra "Merhaba Dünya" döndürmelidir', function () {
    return asyncPromise().then((result) => {
      assert.strictEqual(result, "Merhaba Dünya");
    });
  });
});
```
### Chai İddia Kütüphanesini Kullanma
Chai, Mocha ile birlikte kullanılabilen popüler bir iddia kütüphanesidir. Chai, TDD ve BDD dahil olmak üzere çeşitli iddia stillerini destekler.

## Chai'yi Yükleme
Chai'yi proje seviyesinde yükleyin.
```bash
npm install --save-dev chai
```

### Örnek: Chai Kullanımı
## `test/chaiTest.js` - Mocha Testi Chai ile

```javascript
const chai = require("chai");
const expect = chai.expect;
const sum = require("../sum");

describe("Sum Fonksiyonu", function () {
  it("girdi olarak 1 ve 2 verildiğinde 3 döndürmelidir", function () {
    expect(sum(1, 2)).to.equal(3);
  });

  it("girdi olarak -2 ve 1 verildiğinde -1 döndürmelidir", function () {
    expect(sum(-2, 1)).to.equal(-1);
  });
});
```

### Ekstra Mocha Özellikleri

## Hook'lar
Mocha, testlerden önce ve sonra kod çalıştırmanızı sağlayan before, `after`, `beforeEach`, `afterEach` gibi hook'lar sunar.

# Örnek: Hook Kullanımı
```javasript
describe("Hooklar Örneği", function () {
  before(function () {
    // Tüm testlerden önce çalıştırılır
  });

  after(function () {
    // Tüm testlerden sonra çalıştırılır
  });

  beforeEach(function () {
    // Her testten önce çalıştırılır
  });

  afterEach(function () {
    // Her testten sonra çalıştırılır
  });

  it("test durumu 1", function () {
    // Test kodu
  });

  it("test durumu 2", function () {
    // Test kodu
  });
});
```









