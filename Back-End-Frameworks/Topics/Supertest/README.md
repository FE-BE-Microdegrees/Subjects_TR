# Supertest: Testing HTTP Requests

## Introduction

Supertest is a JavaScript library used for testing HTTP requests in a Node.js environment. It is especially useful when testing your API endpoints, as it allows you to easily send HTTP requests and check responses. Supertest can be used in conjunction with popular testing frameworks like Mocha and Jest.

- [Supertest: Testing HTTP Requests](#supertest-testing-http-requests)
  - [Introduction](#introduction)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Supertest?](#what-is-supertest)
  - [Installing and Setting Up Supertest](#installing-and-setting-up-supertest)
    - [1. Installing Supertest](#1-installing-supertest)
    - [2. Installing a Testing Framework](#2-installing-a-testing-framework)
    - [3. Creating a Simple Express Application](#3-creating-a-simple-express-application)
      - [`app.js` - Express Application](#appjs---express-application)
      - [`server.js` - Starting the Server](#serverjs---starting-the-server)
  - [Writing Tests with Supertest](#writing-tests-with-supertest)
    - [Example: Simple Test](#example-simple-test)
      - [`__tests__/app.test.js`](#__tests__apptestjs)
    - [Example: Testing a POST Request](#example-testing-a-post-request)
      - [`__tests__/app.test.js`](#__tests__apptestjs-1)
    - [Running Tests](#running-tests)
  - [Additional Examples and Best Practices](#additional-examples-and-best-practices)
    - [1. Parameter Checking](#1-parameter-checking)
      - [`app.js` - Updated](#appjs---updated)
      - [`__tests__/app.test.js`](#__tests__apptestjs-2)
    - [2. Header Checking](#2-header-checking)
      - [`app.js` - Updated](#appjs---updated-1)
      - [`__tests__/app.test.js`](#__tests__apptestjs-3)
    - [3. Error Handling](#3-error-handling)
      - [`app.js` - Updated](#appjs---updated-2)
      - [`__tests__/app.test.js`](#__tests__apptestjs-4)

## Learning Outcomes

By the end of this material, learners should be able to:

- Explain what Supertest is and why it is used.
- Install and set up Supertest for writing tests.
- Write and run tests related to HTTP requests using Supertest.
- Use Supertest with testing frameworks like Jest.

## What is Supertest?

Supertest is a library that allows you to make HTTP requests to Node.js servers and verify responses. It is designed to be simple and intuitive, providing several features that make API testing easy and effective.

## Installing and Setting Up Supertest

### 1. Installing Supertest

Install Supertest at the project level using npm or yarn.

```bash
npm install --save-dev supertest
```

Or, if you are using yarn:

```bash
yarn add --dev supertest
```

### 2. Installing a Testing Framework

In this example, we will use Mocha, but you can also use another testing framework.

```bash
npm install --save-dev mocha
```

Add a script to your `package.json` file to run tests with Mocha.

```json
{
  "scripts": {
    "test": "mocha"
  }
}
```

### 3. Creating a Simple Express Application

Let's create a simple Express application that we will test with Supertest.

#### `app.js` - Express Application

```javascript
const express = require("express");
const app = express();

app.get("/hello", (req, res) => {
  res.status(200).send("Hello, World!");
});

app.post("/data", (req, res) => {
  res.status(201).send({ message: "Data received" });
});

module.exports = app;
```

#### `server.js` - Starting the Server

```javascript
const app = require("./app");

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

## Writing Tests with Supertest

### Example: Simple Test

Let's create a test to check the response of the GET request to the `/hello` endpoint.

#### `__tests__/app.test.js`

```javascript
const request = require("supertest");
const app = require("../app");

describe("GET /hello", () => {
  it('should return "Hello, World!"', async () => {
    const response = await request(app).get("/hello");
    expect(response.status).toBe(200);
    expect(response.text).toBe("Hello, World!");
  });
});
```

### Example: Testing a POST Request

Let's add a test to check the response of the POST request to the `/data` endpoint.

#### `__tests__/app.test.js`

```javascript
const request = require("supertest");
const app = require("../app");

describe("GET /hello", () => {
  it('should return "Hello, World!"', async () => {
    const response = await request(app).get("/hello");
    expect(response.status).toBe(200);
    expect(response.text).toBe("Hello, World!");
  });
});

describe("POST /data", () => {
  it('should return "Data received"', async () => {
    const response = await request(app).post("/data").send({ name: "John" });
    expect(response.status).toBe(201);
    expect(response.body.message).toBe("Data received");
  });
});
```

### Running Tests

Run the tests using Jest from the command line.

```bash
npm test
```

## Additional Examples and Best Practices

### 1. Parameter Checking

Test how the API handles URL parameters and query strings.

#### `app.js` - Updated

```javascript
app.get("/user/:id", (req, res) => {
  res.status(200).send({ id: req.params.id });
});
```

#### `__tests__/app.test.js`

```javascript
describe("GET /user/:id", () => {
  it("should return the user id", async () => {
    const userId = "12345";
    const response = await request(app).get(`/user/${userId}`);
    expect(response.status).toBe(200);
    expect(response.body.id).toBe(userId);
  });
});
```

### 2. Header Checking

Test how the API handles HTTP headers.

#### `app.js` - Updated

```javascript
app.get("/headers", (req, res) => {
  res.status(200).set("X-Custom-Header", "value").send("Headers");
});
```

#### `__tests__/app.test.js`

```javascript
describe("GET /headers", () => {
  it("should return custom header", async () => {
    const response = await request(app).get("/headers");
    expect(response.status).toBe(200);
    expect(response.headers["x-custom-header"]).toBe("value");
  });
});
```

### 3. Error Handling

Test how the API handles errors and invalid requests.

#### `app.js` - Updated

```javascript
app.get("/error", (req, res) => {
  res.status(500).send({ error: "Something went wrong" });
});
```

#### `__tests__/app.test.js`

```javascript
describe("GET /error", () => {
  it("should return an error", async () => {
    const response = await request(app).get("/error");
    expect(response.status).toBe(500);
    expect(response.body.error).toBe("Something went wrong");
  });
});
```

# Supertest: HTTP İsteklerini Test Etme

## Giriş

Supertest, Node.js ortamında HTTP isteklerini test etmek için kullanılan bir JavaScript kütüphanesidir. API uç noktalarınızı test etmek için özellikle kullanışlıdır, çünkü HTTP isteklerini kolayca göndermenizi ve yanıtları kontrol etmenizi sağlar. Supertest, Mocha ve Jest gibi popüler test çerçeveleriyle birlikte kullanılabilir.

- [Supertest: HTTP İsteklerini Test Etme](#supertest-http-isteklerini-test-etme)
  - [Giriş](#giriş)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [Supertest Nedir?](#supertest-nedir)
  - [Supertest'i Yükleme ve Ayarlama](#supertesti-yükleme-ve-ayarlama)
    - [1. Supertest'i Yükleme](#1-supertesti-yükleme)
    - [2. Bir Test Çerçevesi Yükleme](#2-bir-test-çerçevesi-yükleme)
    - [3. Basit Bir Express Uygulaması Oluşturma](#3-basit-bir-express-uygulaması-oluşturma)
      - [`app.js` - Express Uygulaması](#appjs---express-uygulaması)
      - [`server.js` - Sunucuyu Başlatma](#serverjs---sunucuyu-başlatma)
  - [Supertest ile Test Yazma](#supertest-ile-test-yazma)
    - [Örnek: Basit Test](#örnek-basit-test)
      - [`__tests__/app.test.js`](#__tests__apptestjs)
    - [Örnek: POST İsteği Test Etme](#örnek-post-isteği-test-etme)
      - [`__tests__/app.test.js`](#__tests__apptestjs-1)
    - [Testleri Çalıştırma](#testleri-çalıştırma)
  - [Ekstra Örnekler ve En İyi Uygulamalar](#ekstra-örnekler-ve-en-iyi-uygulamalar)
    - [1. Parametre Kontrolü](#1-parametre-kontrolü)
      - [`app.js` - Güncellenmiş](#appjs---güncellenmiş)
      - [`__tests__/app.test.js`](#__tests__apptestjs-2)
    - [2. Başlık Kontrolü](#2-başlık-kontrolü)
      - [`app.js` - Güncellenmiş](#appjs---güncellenmiş-1)
      - [`__tests__/app.test.js`](#__tests__apptestjs-3)
    - [3. Hata Yönetimi](#3-hata-yönetimi)
      - [`app.js` - Güncellenmiş](#appjs---güncellenmiş-2)
      - [`__tests__/app.test.js`](#__tests__apptestjs-4)

## Öğrenme Çıktıları

Bu materyalin sonunda öğrenciler şunları yapabilmelidir:

- Supertest'in ne olduğunu ve neden kullanıldığını açıklamak.
- Test yazmak için Supertest'i yüklemek ve ayarlamak.
- Supertest kullanarak HTTP istekleri ile ilgili testler yazmak ve çalıştırmak.
- Supertest'i Jest gibi test çerçeveleriyle kullanmak.

## Supertest Nedir?

Supertest, Node.js sunucularına HTTP istekleri yapmanıza ve yanıtları doğrulamanıza olanak tanıyan bir kütüphanedir. Basit ve sezgisel olacak şekilde tasarlanmıştır, API testini kolay ve etkili hale getiren birkaç özellik sunar.

## Supertest'i Yükleme ve Ayarlama

### 1. Supertest'i Yükleme

Supertest'i proje seviyesinde npm veya yarn kullanarak yükleyin.

```bash
npm install --save-dev supertest
```
Ya da yarn kullanıyorsanız:
```bash
yarn add --dev supertest
```
### 2. Bir Test Çerçevesi Yükleme
Bu örnekte Mocha kullanacağız, ancak başka bir test çerçevesi de kullanabilirsiniz.
```bash
npm install --save-dev mocha
```
`package.json` dosyanıza, Mocha ile testleri çalıştırmak için bir script ekleyin.
```json
{
  "scripts": {
    "test": "mocha"
  }
}
```
### 3. Basit Bir Express Uygulaması Oluşturma
Supertest ile test edeceğimiz basit bir Express uygulaması oluşturalım.

## `app.js` - Express Uygulaması
```javascript
const express = require("express");
const app = express();

app.get("/hello", (req, res) => {
  res.status(200).send("Merhaba, Dünya!");
});

app.post("/data", (req, res) => {
  res.status(201).send({ message: "Veri alındı" });
});

module.exports = app;
```
## `server.js` - Sunucuyu Başlatma
```javascript
const app = require("./app");

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Sunucu ${PORT} portunda çalışıyor`);
});
```

### Supertest ile Test Yazma
Örnek: Basit Test
GET isteğine /`hello` uç noktasının yanıtını kontrol etmek için bir test oluşturalım.

`__tests__/app.test.js`

```javascript

const request = require("supertest");
const app = require("../app");

describe("GET /hello", () => {
  it('Merhaba, Dünya! döndürmelidir', async () => {
    const response = await request(app).get("/hello");
    expect(response.status).toBe(200);
    expect(response.text).toBe("Merhaba, Dünya!");
  });
});
```

### Örnek: POST İsteği Test Etme
POST isteğine /`data` uç noktasının yanıtını kontrol etmek için bir test ekleyelim.

`__tests__/app.test.js`
```javascript
const request = require("supertest");
const app = require("../app");

describe("GET /hello", () => {
  it('Merhaba, Dünya! döndürmelidir', async () => {
    const response = await request(app).get("/hello");
    expect(response.status).toBe(200);
    expect(response.text).toBe("Merhaba, Dünya!");
  });
});

describe("POST /data", () => {
  it('Veri alındı döndürmelidir', async () => {
    const response = await request(app).post("/data").send({ name: "John" });
    expect(response.status).toBe(201);
    expect(response.body.message).toBe("Veri alındı");
  });
});
```
### Testleri Çalıştırma
Testleri komut satırından çalıştırmak için Jest'i kullanın.
```bash
npm test

```

## Ekstra Örnekler ve En İyi Uygulamalar
## 1. Parametre Kontrolü
API'nin URL parametreleri ve sorgu dizeleri ile nasıl çalıştığını test edin.

### `app.js` - Güncellenmiş
```javascript
app.get("/user/:id", (req, res) => {
  res.status(200).send({ id: req.params.id });
});
```

`__tests__/app.test.js`

```javascript
describe("GET /user/:id", () => {
  it("kullanıcı id'sini döndürmelidir", async () => {
    const userId = "12345";
    const response = await request(app).get(`/user/${userId}`);
    expect(response.status).toBe(200);
    expect(response.body.id).toBe(userId);
  });
});
```
## 2. Başlık Kontrolü
API'nin HTTP başlıkları ile nasıl çalıştığını test edin.

### `app.js` - Güncellenmiş
```javascript
app.get("/headers", (req, res) => {
  res.status(200).set("X-Custom-Header", "value").send("Başlıklar");
});

```
`__tests__/app.test.js`
```javascript
describe("GET /headers", () => {
  it("özel başlık döndürmelidir", async () => {
    const response = await request(app).get("/headers");
    expect(response.status).toBe(200);
    expect(response.headers["x-custom-header"]).toBe("value");
  });
});
```

## 3. Hata Yönetimi
API'nin hatalar ve geçersiz isteklerle nasıl başa çıktığını test edin.

### `app.js` - Güncellenmiş

```javascript
app.get("/error", (req, res) => {
  res.status(500).send({ error: "Bir şeyler yanlış gitti" });
});
```
`__tests__/app.test.js`

```javascript
describe("GET /error", () => {
  it("hata döndürmelidir", async () => {
    const response = await request(app).get("/error");
    expect(response.status).toBe(500);
    expect(response.body.error).toBe("Bir şeyler yanlış gitti");
  });
});
```













