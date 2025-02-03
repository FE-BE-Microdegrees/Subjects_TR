# Environment Variables

- [Environment Variables](#environment-variables)
  - [Learning Outcomes](#learning-outcomes)
  - [Using Environment Variables in Node.js](#using-environment-variables-in-nodejs)
    - [Example of a `.env` File](#example-of-a-env-file)
    - [Using the `dotenv` Module](#using-the-dotenv-module)
    - [Using Environment Variables Directly from the Command Line](#using-environment-variables-directly-from-the-command-line)
    - [Environment Detection](#environment-detection)
    - [Adding Environment Variables to `package.json`](#adding-environment-variables-to-packagejson)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- configure environment variables in Node.js;
- use environment variables in Node.js.

Environment variables are variables that are available to all processes running on a computer. They are useful for defining various settings and parameters, such as database connections, API keys, etc. By using environment variables, we can change the configuration of an application without modifying the code, allowing for smooth transitions between different environments, such as development, testing, and production.

## Using Environment Variables in Node.js

Environment variables can be used in Node.js in several ways. A common practice is to store variables in a separate `.env` file and use them in the application.

### Example of a `.env` File

```bash
DB_HOST=localhost
DB_USER=root
DB_PASS=secret
```

### Using the `dotenv` Module

1. **Install the `dotenv` module:**

```bash
npm install dotenv
```

2. **Load the `.env` file in the application:**

```javascript
require("dotenv").config();
```

3. **Use the variables in the application:**

```javascript
const host = process.env.DB_HOST;
const user = process.env.DB_USER;
const pass = process.env.DB_PASS;
```

### Using Environment Variables Directly from the Command Line

You can also set environment variables directly from the command line. For example:

```bash
PORT=3000 node index.js
```

In the application:

```javascript
const port = process.env.PORT;
```

### Environment Detection

You can determine whether the application is running in a development, production, or test environment:

```bash
NODE_ENV=development node index.js
```

In the application:

```javascript
const env = process.env.NODE_ENV;
const db = env === "test" ? "testdb" : "db";
```

### Adding Environment Variables to `package.json`

To add environment variables in `package.json`, it's convenient to use the `cross-env` module:

1. **Install `cross-env`:**

```bash
npm install cross-env
```

2. **Add a script in `package.json`:**

```json
{
  "scripts": {
    "start": "cross-env NODE_ENV=production node index.js"
  }
}
```

`cross-env` allows you to set environment variables in a way that works similarly across different operating systems, ensuring that commands work in both Windows and UNIX-based systems.

Using these practices helps keep the application configuration clean and secure, avoiding the exposure of sensitive data such as passwords and API keys.

# Ortam Değişkenleri

- [Ortam Değişkenleri](#ortam-degiskenleri)
  - [Öğrenme Kazanımları](#ogrenme-kazanimlari)
  - [Node.js'te Ortam Değişkenlerini Kullanma](#nodejste-ortam-degiskenlerini-kullanma)
    - [`.env` Dosyası Örneği](#env-dosyasi-ornegi)
    - [`dotenv` Modülünü Kullanma](#dotenv-modulunu-kullanma)
    - [Komut Satırından Ortam Değişkenlerini Kullanma](#komut-satirindan-ortam-degiskenlerini-kullanma)
    - [Ortam Algılama](#ortam-algilama)
    - [`package.json` Dosyasına Ortam Değişkenleri Ekleme](#packagejson-dosyasina-ortam-degiskenleri-ekleme)

## Öğrenme Kazanımları

Bu bölümü tamamladığınızda:

- Node.js'te ortam değişkenlerini konfigüre edebileceksiniz;
- Node.js'te ortam değişkenlerini kullanabileceksiniz.

Ortam değişkenleri, bir bilgisayarda çalışan tüm süreçler tarafından erişilebilen değişkenlerdir. Veritabanı bağlantıları, API anahtarları gibi farklı ayarları ve parametreleri tanımlamak için kullanılırlar. Ortam değişkenleri kullanarak bir uygulamanın yapılandırmasını kodu değiştirmeden değiştirebiliriz. Bu, geliştirme, test ve üretim ortamları arasında sorunsuz geçiş sağlar.

## Node.js'te Ortam Değişkenlerini Kullanma

Node.js'te ortam değişkenleri birkaç farklı yöntemle kullanılabilir. Yaygın bir uygulama, değişkenleri ayrı bir `.env` dosyasında saklamak ve bunları uygulamada kullanmaktır.

### `.env` Dosyası Örneği

```bash
DB_HOST=localhost
DB_USER=root
DB_PASS=secret
```

### `dotenv` Modülünü Kullanma

1. **`dotenv` modülünü yükleyin:**

```bash
npm install dotenv
```

2. **`.env` dosyasını uygulamaya yüklenmesini sağlayın:**

```javascript
require("dotenv").config();
```

3. **Değişkenleri uygulamada kullanın:**

```javascript
const host = process.env.DB_HOST;
const user = process.env.DB_USER;
const pass = process.env.DB_PASS;
```

### Komut Satırından Ortam Değişkenlerini Kullanma

Ortam değişkenlerini doğrudan komut satırından da ayarlayabilirsiniz. Örneğin:

```bash
PORT=3000 node index.js
```

Uygulama içinde:

```javascript
const port = process.env.PORT;
```

### Ortam Algılama

Bir uygulamanın geliştirme, üretim veya test ortamında çalışıp çalışmadığını belirleyebilirsiniz:

```bash
NODE_ENV=development node index.js
```

Uygulamada:

```javascript
const env = process.env.NODE_ENV;
const db = env === "test" ? "testdb" : "db";
```

### `package.json` Dosyasına Ortam Değişkenleri Ekleme

Ortam değişkenlerini `package.json` dosyasına eklemek için `cross-env` modülü kullanılabilir:

1. **`cross-env` modülünü yükleyin:**

```bash
npm install cross-env
```

2. **`package.json` içinde bir script ekleyin:**

```json
{
  "scripts": {
    "start": "cross-env NODE_ENV=production node index.js"
  }
}
```

`cross-env`, farklı işletim sistemlerinde aynı şekilde çalışmasını sağlayarak ortam değişkenlerini ayarlamanın daha tutarlı bir yöntemini sunar. Bu sayede Windows ve UNIX tabanlı sistemlerde komutlar sorunsuz çalışır.

Bu uygulamalar, uygulamanın yapılandırmasını temiz ve güvenli tutmaya yardımcı olur, özellikle şifreler ve API anahtarları gibi hassas verilerin açığa çıkmasını önler.

