# Express

In this lesson, we will explore Express, a popular web application framework for Node.js. We will learn how to install Express, use its methods, and work with request and response objects in Express.

![Express](Express.webp)

Image source: Dall-E by OpenAI

- [Express](#express)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Express?](#what-is-express)
  - [Installing Express](#installing-express)
  - [Express App Methods](#express-app-methods)
  - [Request and Response in Express](#request-and-response-in-express)
    - [Sources](#sources)

## Learning Outcomes

By the end of this lesson, you will be able to:

- Explain what Express is and why it is used.
- Install Express in a Node.js project.
- Create a simple Express application and run it.

## What is Express?

Express is a popular web application framework for Node.js, designed for building scalable and flexible web applications. It provides a range of features for developing web applications, such as routing, middleware, and support for handling HTTP requests and responses.

Express simplifies the process of building web applications by offering a lightweight yet powerful framework that allows developers to focus on creating core application functionality. It includes a simple API that enables developers to easily create HTTP routes, define middleware functions to handle requests, and work with various templating engines and other tools.

## Installing Express

To install Express in a Node.js project, follow these steps:

1. Create a new directory for your project and navigate to that directory in the terminal.
2. Initialize a new Node.js project using the command `npm init`. This will create a `package.json` file that tracks your project's dependencies.
3. Install Express using the command `npm install express`. This will download and install the latest version of Express and its dependencies.

Here is an example of installing Express using the command line:

```bash
mkdir myapp
cd myapp
npm init -y
npm install express
```

After installing Express, you can create a new file named `app.js` and start building your application using the Express framework. To use Express in your application, you need to import it in your `app.js` file like this:

```javascript
const express = require("express");
const app = express();
```

Here’s a simple example of an Express application:

```javascript
const express = require("express");
const app = express();

const port = 3000;

app.get("/", (req, res) => {
  return res.send("Hello!");
});

app.listen(port, () => {
  console.log(`Listening on port: ${port}`);
});
```

## Express App Methods

Similar to [HTTP request methods](../http-methods/README.md), Express provides a wide range of methods that can be used to create web applications and receive requests from clients. Here are some of the most common methods in an Express application:

- **GET**: (`app.get()`) This method is used to retrieve data from the server. It is used to request a specific resource, such as a webpage, image, or video.

- **POST**: (`app.post()`) This method is used to send data to the server. It is typically used to submit forms or send data to the server for processing.

- **PUT**: (`app.put()`) This method is used to update existing data on the server. It is typically used to update a specific resource (e.g., a user profile or product information).

- **DELETE**: (`app.delete()`) This method is used to delete data from the server. It is typically used to remove a specific resource, such as a user account or product.

- **USE**: (`app.use()`) This method is used to define middleware functions that execute for every request that matches a specific route.

- **SET**: (`app.set()`) This method is used to set application-level variables (e.g., port number or view engine).

These are just a few of the many methods offered by Express. Each method can be used to create routes that handle specific types of HTTP requests, enabling developers to build powerful and flexible web applications.

## Request and Response in Express

Similar to the HTTP protocol, Express provides options for receiving and sending request and response objects.

When a request is received, Express creates its version of the request, which has many different properties, including:

- **params**: (req.params) This attribute is an object containing parameters matched to the named route "parameters." For example, if you have a route `/users/:id`, the params object will have the attribute `id` with the value `:id`.

- **query**: (req.query) This attribute is an object containing attributes for each query string parameter of the route. For example, if the URL is `/users?sort=desc`, the request object will contain `{ sort: 'desc' }`.

- **body**: (req.body) This attribute is an object containing the parsed body of the request when the request method is `POST`, `PUT`, or `PATCH`, and the content-type header is `application/x-www-form-urlencoded` or `application/json`.

- **headers**: (req.headers) This attribute is an object containing the headers sent by the client.

- **method**: (req.method) This attribute is a string that contains the HTTP request method (e.g., `GET`, `POST`, `PUT`, `DELETE`, etc.).

- **url**: (req.url) This attribute is a string that contains the request URL.

- **cookies**: (req.cookies) This attribute is an object that contains cookies sent by the client.

- **ip**: (req.ip) This attribute is a string that contains the client's IP address.

- **protocol**: (req.protocol) This attribute is a string that contains the protocol used for the request (http or https).

Overall, the Express request object provides developers with a wealth of information about the client's request, enabling them to create powerful and flexible web applications.

To send a response, Express offers several functions, the most common of which are:

- **send**: (res.send()) This method is used to send a string, buffer, or JSON response back to the client. It automatically sets the `Content-Type` header based on the type of data.

- **json**: (res.json()) This method is used to send a JSON response back to the client. It sets the `Content-Type` header to `application/json`.

- **redirect**: (res.redirect()) This method is used to redirect the client to another URL. It sets the location header to the specified URL and defaults to the `302` status code.

- **render**: (res.render()) This method is used to render a view template and send an HTML response back to the client. It takes the name of the template and a data object as arguments.

- **status**: (res.status()) This method is used to set the HTTP response status code. It can be used to specify any valid HTTP status code.

- **sendFile**: (res.sendFile()) This method is used to send a file in response. It takes the file path as an argument and automatically sets the content-type header based on the file extension.

These are just a few of the many response methods offered by Express. Each method can be used to send different types of responses back to the client.

### Sources

- [Express Official Website](https://expressjs.com/)
- [Express API Reference](https://expressjs.com/en/4x/api.html#app.METHOD)
- [Request Object in Express](https://expressjs.com/en/api.html#req)
- [Response Object in Express](https://expressjs.com/en/api.html#res)
- 
# Express

Bu derste, Node.js için popüler bir web uygulama çatısı olan Express'i keşfedeceğiz. Express'i nasıl kuracağımızı, yöntemlerini nasıl kullanacağımızı ve Express'teki istek ve yanıt nesneleriyle nasıl çalışacağımızı öğreneceğiz.

![Express](Express.webp)

Görsel kaynağı: Dall-E by OpenAI

- [Express](#express)
  - [Öğrenim Hedefleri](#öğrenim-hedefleri)
  - [Express Nedir?](#express-nedir)
  - [Express Kurulumu](#express-kurulumu)
  - [Express Uygulama Yöntemleri](#express-uygulama-yöntemleri)
  - [Express'te Istek ve Yanıt](#expresste-istek-ve-yanıt)
    - [Kaynaklar](#kaynaklar)

## Öğrenim Hedefleri

Bu dersten sonunda şu becerilere sahip olacaksınız:

- Express'in ne olduğunu ve neden kullanıldığını açıklayabileceksiniz.
- Express'i bir Node.js projesine kurabileceksiniz.
- Basit bir Express uygulaması oluşturup çalıştırabileceksiniz.

## Express Nedir?

Express, Node.js için popüler bir web uygulama çatısıdır ve ölçeklenebilir ve esnek web uygulamaları oluşturmak için tasarlanmıştır. Yönlendirme, ara yazılım ve HTTP istek ve yanıtlarını işleme desteği gibi bir dizi özellik sunar.

Express, web uygulamaları oluşturma sürecini basitleştirir ve geliştiricilerin uygulamanın temel işlevselliğine odaklanmalarını sağlar. HTTP rotaları oluşturmak, istekleri işlemek için ara yazılım fonksiyonları tanımlamak ve çeşitli şablon motorları ve diğer araçlarla çalışmak için basit bir API içerir.

## Express Kurulumu

Express'i bir Node.js projesine kurmak için şu adımları izleyin:

1. Projeniz için yeni bir dizin oluşturun ve terminalde bu dizine gidin.
2. `npm init` komutunu kullanarak yeni bir Node.js projesi başlatın. Bu, projenizin bağımlılıklarını takip eden bir `package.json` dosyası oluşturur.
3. `npm install express` komutunu kullanarak Express'i kurun. Bu, Express'in en son sürümünü ve bağımlılıklarını indirir.

Express'i komut satırını kullanarak kurmak için örnek:

```bash
mkdir myapp
cd myapp
npm init -y
npm install express

```
Express'i kurduktan sonra, `app.js` adında yeni bir dosya oluşturabilir ve Express çatısını kullanarak uygulamanızı inşa etmeye başlayabilirsiniz. Express'i uygulamanızda kullanmak için şu şekilde içeri aktarın:

```javascript
const express = require("express");
const app = express();

```
İşte basit bir Express uygulamasının örneği:

```javascript
const express = require("express");
const app = express();

const port = 3000;

app.get("/", (req, res) => {
  return res.send("Merhaba!");
});

app.listen(port, () => {
  console.log(`Port üzerinde dinleniyor: ${port}`);
});
```
## Express Uygulama Yöntemleri
[HTTP request methods](../http-methods/README.md) istek yöntemleri gibi, Express de web uygulamaları oluşturmak ve istemcilerden gelen istekleri almak için kullanılabilecek çok sayıda yöntem sunar. İşte bir Express uygulamasındaki en yaygın yöntemlerden bazıları:

-**GET**: (`app.get()`) Bu yöntem, sunucudan veri almak için kullanılır. Bir web sayfası, resim veya video gibi belirli bir kaynağı istemek için kullanılır.

-**POST**: (`app.post()`) Bu yöntem, sunucuya veri göndermek için kullanılır. Genellikle form göndermek veya verileri işleme için sunucuya göndermek için kullanılır.

-**PUT**: (`app.put()`) Bu yöntem, sunucudaki mevcut verileri güncellemek için kullanılır. Genellikle belirli bir kaynağı (örneğin, bir kullanıcı profili veya ürün bilgisi) güncellemek için kullanılır.

-**DELETE**: (`app.delete()`) Bu yöntem, sunucudan veri silmek için kullanılır. Genellikle belirli bir kaynağı (örneğin, bir kullanıcı hesabı veya ürün) silmek için kullanılır.

-**USE**: (`app.use()`) Bu yöntem, belirli bir rota ile eşleşen her istek için çalışan ara yazılım işlevleri tanımlamak için kullanılır.

-**SET**: (`app.set()`) Bu yöntem, uygulama düzeyinde değişkenler (örneğin, port numarası veya görünüm motoru) ayarlamak için kullanılır.

Bunlar, Express'in sunduğu birçok yöntemden sadece birkaçıdır. Her bir yöntem, belirli türdeki HTTP isteklerini işleyen rotalar oluşturmak için kullanılabilir, bu da geliştiricilerin güçlü ve esnek web uygulamaları oluşturmasına olanak tanır.

## Express'te İstek ve Yanıt

HTTP protokolüne benzer olarak, Express, istek ve yanıt nesnelerini almak ve göndermek için seçenekler sunar.

Bir istek alındığında, Express, istek nesnesinin birçok farklı özelliği içeren versiyonunu oluşturur, bunlar arasında şunlar bulunur:

## İstek Nesnesi (Request Object)

Express, HTTP istekleri hakkında zengin bilgi sağlayan bir `request` (istek) nesnesi sunar. Aşağıda en yaygın kullanılan özellikler bulunmaktadır:

- **params**: (req.params) Bu özellik, adlandırılmış rota "parametrelerine" eşleşen parametreleri içeren bir nesnedir. Örneğin, `/users/:id` gibi bir rotanız varsa, params nesnesi `id` özelliğini `:id` değeriyle içerir.

- **query**: (req.query) Bu özellik, rotanın her bir sorgu dizesi parametresi için özellikler içeren bir nesnedir. Örneğin, URL `/users?sort=desc` ise, istek nesnesi `{ sort: 'desc' }` içerecektir.

- **body**: (req.body) Bu özellik, `POST`, `PUT` veya `PATCH` istek metoduna ve `application/x-www-form-urlencoded` veya `application/json` içerik türüne sahip isteklerin ayrıştırılmış gövdesini içeren bir nesnedir.

- **headers**: (req.headers) Bu özellik, istemci tarafından gönderilen başlıkları içeren bir nesnedir.

- **method**: (req.method) Bu özellik, HTTP istek metodunu içeren bir dizedir (örneğin, `GET`, `POST`, `PUT`, `DELETE`, vb.).

- **url**: (req.url) Bu özellik, istek URL'sini içeren bir dizedir.

- **cookies**: (req.cookies) Bu özellik, istemci tarafından gönderilen çerezleri içeren bir nesnedir.

- **ip**: (req.ip) Bu özellik, istemcinin IP adresini içeren bir dizedir.

- **protocol**: (req.protocol) Bu özellik, istek için kullanılan protokolü içeren bir dizedir (http veya https).

Genel olarak, Express istek nesnesi, geliştiricilere istemcinin isteği hakkında zengin bilgi sunar, bu da güçlü ve esnek web uygulamaları oluşturmalarına olanak tanır.

## Yanıt Nesnesi (Response Object)

Yanıt göndermek için Express, aşağıda en yaygın kullanılan birkaç fonksiyon sunar:

- **send**: (res.send()) Bu yöntem, istemciye bir dize, tampon veya JSON yanıtı göndermek için kullanılır. Gönderilen verinin türüne göre `Content-Type` başlığını otomatik olarak ayarlar.

- **json**: (res.json()) Bu yöntem, istemciye JSON yanıtı göndermek için kullanılır. `Content-Type` başlığını `application/json` olarak ayarlar.

- **redirect**: (res.redirect()) Bu yöntem, istemciyi başka bir URL'ye yönlendirmek için kullanılır. Konum başlığını belirtilen URL'ye ayarlar ve varsayılan olarak `302` durum kodunu kullanır.

- **render**: (res.render()) Bu yöntem, bir görünüm şablonunu render etmek ve istemciye HTML yanıtı göndermek için kullanılır. Şablonun adını ve bir veri nesnesini argüman olarak alır.

- **status**: (res.status()) Bu yöntem, HTTP yanıt durum kodunu ayarlamak için kullanılır. Geçerli herhangi bir HTTP durum kodunu belirtmek için kullanılabilir.

- **sendFile**: (res.sendFile()) Bu yöntem, bir dosyayı yanıt olarak göndermek için kullanılır. Dosya yolunu argüman olarak alır ve dosya uzantısına göre `Content-Type` başlığını otomatik olarak ayarlar.

Bunlar, Express'in sunduğu birçok yanıt yönteminden sadece birkaçıdır. Her bir yöntem, istemciye farklı türde yanıtlar göndermek için kullanılabilir.

### Kaynaklar

- [Express Resmi Web Sitesi](https://expressjs.com/)
- [Express API Referansı](https://expressjs.com/en/4x/api.html#app.METHOD)
- [Express'teki İstek Nesnesi](https://expressjs.com/en/api.html#req)
- [Express'teki Yanıt Nesnesi](https://expressjs.com/en/api.html#res)


