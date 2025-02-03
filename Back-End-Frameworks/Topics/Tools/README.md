# API Testing Tools

In this chapter, we will explore various tools that assist in creating and testing APIs.

![API tools](API-tools.webp)

Image source: Dall-E by OpenAI

- [API Testing Tools](#api-testing-tools)
  - [Learning Outcomes](#learning-outcomes)
  - [Postman](#postman)
  - [Thunder Client](#thunder-client)
  - [Command-Line Tool `curl`](#command-line-tool-curl)
  - [Docker Desktop](#docker-desktop)
  - [SQLTools VS Code Extension](#sqltools-vs-code-extension)

## Learning Outcomes

By the end of this chapter, you will be able to:

- Describe various tools that aid in the creation and testing of APIs.

Since web APIs typically support various request methods (`GET`, `POST`, `PUT`, `DELETE`, etc.), simply using a web browser to send requests to the API is no longer sufficient. Instead, dedicated tools are needed.

## Postman

Postman is an application specifically designed for API testing. With Postman, you can send different requests, view responses, save requests and responses, create various environments (e.g., development, testing, production), and more. You can also write tests in Postman to check that API responses are in the expected format.

Postman is available for download here: [Postman Downloads](https://www.postman.com/downloads/)

There is also a Postman extension available for VS Code, which can be found in the VS Code extensions marketplace.

## Thunder Client

Thunder Client is a free extension for the VS Code code editor that also allows for API testing.

You can download Thunder Client from the VS Code extensions marketplace.

## Command-Line Tool `curl`

`cURL` (Command-line URL) is a free and open-source software project that provides a command-line tool and library (libcurl) for transferring data using various protocols. `cURL` supports many internet protocols, including HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, LDAPS, SMTP, POP3, IMAP, RTSP, and many others.

With `cURL`, you can effectively send various requests to an API and view responses.

For example, sending a `GET` request:

```bash
curl http://localhost:3000/
```

Or sending a `POST` request:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username":"xyz","password":"xyz"}' http://localhost:3000/login
```

## Docker Desktop

`Docker Desktop` is an application that allows developers to build, test, and share applications in containers. Containers are lightweight, isolated, and reusable virtual environments that provide developers the ability to develop and run applications anywhere Docker is available.

## SQLTools VS Code Extension

`SQLTools` is a popular Visual Studio Code (VS Code) extension that offers a powerful and user-friendly SQL database management tool directly within the VS Code environment. It allows developers to write and execute SQL queries, manage databases, and view data results without leaving VS Code. `SQLTools` supports several database management systems, including MySQL, PostgreSQL, SQLite, and many others.

# API Test Araçları

Bu bölümde, API'leri oluşturmanıza ve test etmenize yardımcı olan çeşitli araçları keşfedeceğiz.

![API tools](API-tools.webp)

Görsel Kaynağı: Dall-E by OpenAI

- [API Test Araçları](#api-test-araçları)
  - [Öğrenme Kazanımları](#öğrenme-kazanımları)
  - [Postman](#postman)
  - [Thunder Client](#thunder-client)
  - [Komut Satırı Aracı `curl`](#komut-satırı-aracı-curl)
  - [Docker Desktop](#docker-desktop)
  - [SQLTools VS Code Uzantısı](#sqltools-vs-code-uzantısı)

## Öğrenme Kazanımları

Bu bölümü tamamladığınızda şunları yapabiliyor olacaksınız:

- API'lerin oluşturulması ve test edilmesine yardımcı olan çeşitli araçları tanımlamak.

Web API'leri genellikle çeşitli istek yöntemlerini (`GET`, `POST`, `PUT`, `DELETE` vb.) desteklediğinden, yalnızca bir web tarayıcısı kullanarak API'ye istek göndermek artık yeterli değildir. Bunun yerine, özel araçlara ihtiyaç vardır.

## Postman

Postman, özellikle API testi için tasarlanmış bir uygulamadır. Postman ile farklı istekler gönderebilir, yanıtları görüntüleyebilir, istekleri ve yanıtları kaydedebilir, çeşitli ortamlar (örneğin, geliştirme, test, üretim) oluşturabilir ve daha fazlasını yapabilirsiniz. Ayrıca, Postman'da API yanıtlarının beklenen formatta olup olmadığını kontrol etmek için testler yazabilirsiniz.

Postman'ı buradan indirebilirsiniz: [Postman İndir](https://www.postman.com/downloads/)

Ayrıca, VS Code için Postman uzantısı da mevcuttur ve VS Code uzantı pazarında bulunabilir.

## Thunder Client

Thunder Client, VS Code kod editörü için ücretsiz bir uzantıdır ve API testi yapmanıza olanak tanır.

Thunder Client'ı VS Code uzantı pazarından indirebilirsiniz.

## Komut Satırı Aracı `curl`

`cURL` (Komut Satırı URL'si), veri aktarımını çeşitli protokollerle gerçekleştiren bir komut satırı aracı ve kütüphanesi (libcurl) sağlayan ücretsiz ve açık kaynaklı bir yazılım projesidir. `cURL`, HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, LDAPS, SMTP, POP3, IMAP, RTSP ve daha birçok internet protokolünü destekler.

`cURL` ile API'ye çeşitli istekler gönderebilir ve yanıtları görüntüleyebilirsiniz.

Örneğin, bir `GET` isteği göndermek:

```bash
curl http://localhost:3000/

Veya bir `POST` isteği göndermek:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username":"xyz","password":"xyz"}' http://localhost:3000/login
```
## Docker Desktop
`Docker Desktop`, geliştiricilerin uygulamaları konteynerlerde oluşturmasına, test etmesine ve paylaşmasına olanak tanıyan bir uygulamadır. Konteynerler, geliştiricilerin Docker'ın bulunduğu her yerde uygulama geliştirmesine ve çalıştırmasına olanak tanıyan hafif, izole edilmiş ve yeniden kullanılabilir sanal ortamlardır.

## SQLTools VS Code Uzantısı
`SQLTools`, Visual Studio Code (VS Code) ortamında doğrudan güçlü ve kullanıcı dostu bir SQL veritabanı yönetim aracı sunan popüler bir uzantıdır. Geliştiricilerin SQL sorguları yazmasına, veritabanlarını yönetmesine ve veri sonuçlarını görmesine olanak tanır.  `SQLTools`, MySQL, PostgreSQL, SQLite ve diğer birçok veritabanı yönetim sistemini destekler.


