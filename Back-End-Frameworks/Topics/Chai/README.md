# Chai Assertion Library

Chai is a popular assertion library for JavaScript used with testing frameworks like Mocha and Jest. Chai offers various assertion styles, including TDD (Test-Driven Development) and BDD (Behavior-Driven Development) styles, making it easy and readable to write tests.

![Chai](Chai.webp)

Image source: Dall-E by OpenAI

- [Chai Assertion Library](#chai-assertion-library)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Chai?](#what-is-chai)
    - [Chai Advantages](#chai-advantages)
  - [Installing and Setting Up Chai](#installing-and-setting-up-chai)
    - [1. Installing Chai](#1-installing-chai)
    - [2. Installing a Testing Framework](#2-installing-a-testing-framework)
    - [3. Creating a Test File](#3-creating-a-test-file)
  - [Writing Tests with Chai](#writing-tests-with-chai)
    - [Example: Simple TDD Style Test](#example-simple-tdd-style-test)
      - [`sum.js` - The Function We Are Testing](#sumjs---the-function-we-are-testing)
      - [`test/sum.test.js` - Mocha Test with Chai](#testsumtestjs---mocha-test-with-chai)
    - [Example: Simple BDD Style Test](#example-simple-bdd-style-test)
      - [`test/sum.test.js` - Mocha Test with Chai](#testsumtestjs---mocha-test-with-chai-1)
    - [Running Tests](#running-tests)
  - [Chai Assertion Styles](#chai-assertion-styles)
    - [1. Assert Style](#1-assert-style)
    - [2. Expect Style](#2-expect-style)
    - [3. Should Style](#3-should-style)
  - [Extending Chai](#extending-chai)
    - [Example: Chai-as-Promised](#example-chai-as-promised)
      - [Installation](#installation)
      - [Usage](#usage)
  - [Additional Examples and Best Practices](#additional-examples-and-best-practices)
    - [Checking Object Equality](#checking-object-equality)
    - [Checking for Errors](#checking-for-errors)
    - [Testing Asynchronous Functions](#testing-asynchronous-functions)

## Learning Outcomes

By the end of this material, learners should be able to:

- explain what Chai is and why it is used;
- install and set up Chai at the project level with Mocha or another testing framework;
- use various Chai assertions for writing tests in TDD and BDD styles;
- extend Chai functionality with plugins.

## What is Chai?

Chai is an assertion library that provides various methods to verify test results. It works well with Mocha and other JavaScript testing frameworks, offering flexible and readable assertions.

### Chai Advantages

- **Flexibility:** Supports multiple assertion styles.
- **Readability:** Assertions are clear and intuitive.
- **Extensibility:** Can be extended with plugins.

## Installing and Setting Up Chai

### 1. Installing Chai

Install Chai at the project level using npm or yarn.

```bash
npm install --save-dev chai@4.4.1
```

Or, if you are using yarn:

```bash
yarn add --dev chai@4.4.1
```

> Note: For this course, we are using version 4.4.1, as it is the last version that supports `require`-based imports. Newer versions use ES6 imports.

### 2. Installing a Testing Framework

In this example, we will use Mocha, but you can also use Jest or any other testing framework.

```bash
npm install --save-dev mocha
```

Add a script in the `package.json` file to run tests with Mocha.

```json
{
  "scripts": {
    "test": "mocha"
  }
}
```

### 3. Creating a Test File

Create a directory named `test` in the root of the project and a test file inside it, for example, `sum.test.js`.

```bash
mkdir test
cd test
touch sum.test.js
```

## Writing Tests with Chai

### Example: Simple TDD Style Test

#### `sum.js` - The Function We Are Testing

```javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

#### `test/sum.test.js` - Mocha Test with Chai

```javascript
const chai = require("chai");
const assert = chai.assert;
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

### Example: Simple BDD Style Test

#### `test/sum.test.js` - Mocha Test with Chai

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

### Running Tests

Run the tests using the Mocha command line.

```bash
npm test
```

## Chai Assertion Styles

Chai supports three different assertion styles: Assert, Expect, and Should.

### 1. Assert Style

```javascript
const chai = require("chai");
const assert = chai.assert;

assert.strictEqual(sum(1, 2), 3, "sum of 1 and 2 should be 3");
```

### 2. Expect Style

```javascript
const chai = require("chai");
const expect = chai.expect;

expect(sum(1, 2)).to.equal(3, "sum of 1 and 2 should be 3");
```

### 3. Should Style

```javascript
const chai = require("chai");
chai.should();

sum(1, 2).should.equal(3, "sum of 1 and 2 should be 3");
```

## Extending Chai

Chai can be extended with plugins to add additional functionality.

### Example: Chai-as-Promised

Chai-as-Promised is a plugin that allows you to test promises.

#### Installation

```bash
npm install --save-dev chai-as-promised
```

#### Usage

```javascript
const chai = require("chai");
const expect = chai.expect;
const chaiAsPromised = require("chai-as-promised");

chai.use(chaiAsPromised);

function asyncFunction() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Hello, World!");
    }, 1000);
  });
}

describe("Async Function", function () {
  it('should return "Hello, World!" after 1 second', function () {
    return expect(asyncFunction()).to.eventually.equal("Hello, World!");
  });
});
```

## Additional Examples and Best Practices

### Checking Object Equality

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };

expect(obj1).to.deep.equal(obj2);
```

### Checking for Errors

```javascript
function badFunction() {
  throw new Error("Something went wrong");
}

expect(badFunction).to.throw("Something went wrong");
```

### Testing Asynchronous Functions

```javascript
function asyncFunction(callback) {
  setTimeout(() => {
    callback(null, "Hello, World!");
  }, 1000);
}

describe("Async Function", function () {
  it('should return "Hello, World!" after 1 second', function (done) {
    asyncFunction(function (err, result) {
      expect(result).to.equal("Hello, World!");
      done();
    });
  });
});
```

# Chai Doğrulama (Assertion) Kütüphanesi

Chai, JavaScript test çatıları olan Mocha ve Jest ile kullanılan popüler bir doğrulama (assertion) kütüphanesidir. Chai, TDD (Test-Driven Development) ve BDD (Behavior-Driven Development) gibi çeşitli doğrulama stilleri sunarak test yazmayı kolay ve okunabilir hale getirir.

![Chai](Chai.webp)

Görsel kaynağı: Dall-E by OpenAI

- [Chai Doğrulama Kütüphanesi](#chai-dogrulama-kutuphanesi)
  - [Öğrenme Çıktıları](#ogrenme-ciktilari)
  - [Chai Nedir?](#chai-nedir)
    - [Chai'nin Avantajları](#chainin-avantajlari)
  - [Chai Kurulumu ve Yapılandırması](#chai-kurulumu-ve-yapilandirmasi)
    - [1. Chai Kurulumu](#1-chai-kurulumu)
    - [2. Bir Test Çatısı Kurma](#2-bir-test-catisi-kurma)
    - [3. Bir Test Dosyası Oluşturma](#3-bir-test-dosyasi-olusturma)
  - [Chai ile Test Yazma](#chai-ile-test-yazma)
    - [Örnek: Basit TDD Stili Test](#ornek-basit-tdd-stili-test)
      - [`sum.js` - Test Edilen Fonksiyon](#sumjs---test-edilen-fonksiyon)
      - [`test/sum.test.js` - Chai ile Mocha Testi](#testsumtestjs---chai-ile-mocha-testi)
    - [Örnek: Basit BDD Stili Test](#ornek-basit-bdd-stili-test)
      - [`test/sum.test.js` - Chai ile Mocha Testi](#testsumtestjs---chai-ile-mocha-testi-1)
    - [Testleri Çalıştırma](#testleri-calistirma)
  - [Chai Doğrulama Stilleri](#chai-dogrulama-stilleri)
    - [1. Assert Stili](#1-assert-stili)
    - [2. Expect Stili](#2-expect-stili)
    - [3. Should Stili](#3-should-stili)
  - [Chai'yi Genişletme](#chaiyi-genisletme)
    - [Örnek: Chai-as-Promised](#ornek-chai-as-promised)
      - [Kurulum](#kurulum)
      - [Kullanım](#kullanim)
  - [Ek Örnekler ve En İyi Uygulamalar](#ek-ornekler-ve-en-iyi-uygulamalar)
    - [Nesne Eşitliğini Kontrol Etme](#nesne-esitligini-kontrol-etme)
    - [Hata Kontrolü](#hata-kontrolu)
    - [Asenkron Fonksiyonları Test Etme](#asenkron-fonksiyonlari-test-etme)

## Örnek: Basit BDD Stili Test

#### `test/sum.test.js` - Chai ile Mocha Testi

```javascript
const chai = require("chai");
const expect = chai.expect;
const sum = require("../sum");

describe("Toplama Fonksiyonu", function () {
  it("1 ve 2 girdileri için sonucu 3 döndürmelidir", function () {
    expect(sum(1, 2)).to.equal(3);
  });

  it("-2 ve 1 girdileri için sonucu -1 döndürmelidir", function () {
    expect(sum(-2, 1)).to.equal(-1);
  });
});
```

### Testleri Çalıştırma

Mocha komut satırı ile testleri çalıştırın.

```bash
npm test
```

## Chai Doğrulama Stilleri

Chai, üç farklı doğrulama stili destekler: Assert, Expect ve Should.

### 1. Assert Stili

```javascript
const chai = require("chai");
const assert = chai.assert;

assert.strictEqual(sum(1, 2), 3, "1 ve 2 toplamı 3 olmalıdır");
```

### 2. Expect Stili

```javascript
const chai = require("chai");
const expect = chai.expect;

expect(sum(1, 2)).to.equal(3, "1 ve 2 toplamı 3 olmalıdır");
```

### 3. Should Stili

```javascript
const chai = require("chai");
chai.should();

sum(1, 2).should.equal(3, "1 ve 2 toplamı 3 olmalıdır");
```

## Chai'yi Genişletme

Chai, ek işlevsellik eklemek için eklentilerle genişletilebilir.

### Örnek: Chai-as-Promised

Chai-as-Promised, vaatleri (promises) test etmeyi sağlayan bir eklentidir.

#### Kurulum

```bash
npm install --save-dev chai-as-promised
```

#### Kullanım

```javascript
const chai = require("chai");
const expect = chai.expect;
const chaiAsPromised = require("chai-as-promised");

chai.use(chaiAsPromised);

function asyncFunction() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Merhaba, Dünya!");
    }, 1000);
  });
}

describe("Asenkron Fonksiyon", function () {
  it('1 saniye sonra "Merhaba, Dünya!" döndürmelidir', function () {
    return expect(asyncFunction()).to.eventually.equal("Merhaba, Dünya!");
  });
});
```

## Ek Örnekler ve En İyi Uygulamalar

### Nesne Eşitliğini Kontrol Etme

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };

expect(obj1).to.deep.equal(obj2);
```

### Hata Kontrolü

```javascript
function badFunction() {
  throw new Error("Bir hata oluştu");
}

expect(badFunction).to.throw("Bir hata oluştu");
```

### Asenkron Fonksiyonları Test Etme

```javascript
function asyncFunction(callback) {
  setTimeout(() => {
    callback(null, "Merhaba, Dünya!");
  }, 1000);
}

describe("Asenkron Fonksiyon", function () {
  it('1 saniye sonra "Merhaba, Dünya!" döndürmelidir', function (done) {
    asyncFunction(function (err, result) {
      expect(result).to.equal("Merhaba, Dünya!");
      done();
    });
  });
});
```






