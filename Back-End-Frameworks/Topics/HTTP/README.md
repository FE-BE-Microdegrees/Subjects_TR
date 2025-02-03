# HTTP (_Hypertext Transfer Protocol_)

In this chapter, we will discuss HTTP, its request methods, and response codes.

![HTTP](HTTP.webp)

Image source: Dall-E by OpenAI

- [HTTP (_Hypertext Transfer Protocol_)](#http-hypertext-transfer-protocol)
  - [Learning Outcomes](#learning-outcomes)
  - [What is HTTP?](#what-is-http)
  - [HTTP Request Methods](#http-request-methods)
  - [HTTP Response Codes](#http-response-codes)
  - [Examples of HTTP Response Codes](#examples-of-http-response-codes)
    - [1xx (Informational)](#1xx-informational)
    - [2xx (Successful)](#2xx-successful)
    - [3xx (Redirection)](#3xx-redirection)
    - [4xx (Client Error)](#4xx-client-error)
    - [5xx (Server Error)](#5xx-server-error)

## Learning Outcomes

By the end of this chapter, you will be able to:

- Explain what HTTP is and how it works.
- Describe various HTTP request methods and their use cases.
- Define HTTP response codes and their meanings.
- Explain how HTTP response codes are used to indicate the results and statuses of requests.

## What is HTTP?

HTTP stands for Hypertext Transfer Protocol. It is an application layer protocol used for transmitting data over the Internet.

HTTP is the foundation of the World Wide Web, used by web browsers to request and retrieve web pages, images, videos, and other content from web servers. Web servers also use HTTP to respond to these requests and send the requested content back to the client.

HTTP operates on a client-server model, where the client sends a request message to the server, and the server responds with a response message. HTTP requests are typically initiated by the user's web browser or other client-side applications and can contain various types of information, such as request methods (e.g., GET, POST, PUT, DELETE), headers, and data.

HTTP is a stateless protocol, meaning that each request and response is independent and does not rely on previous communication between the client and the server. This allows for greater scalability and flexibility but also requires additional mechanisms, such as cookies or session tokens, to maintain session-based communication between the client and server.

## HTTP Request Methods

HTTP request methods indicate the desired action to be performed on a resource identified by the URI (Uniform Resource Identifier) in the HTTP request. The most common HTTP request methods include:

- **GET**: Used to request a resource from the server. It is a safe and idempotent method, meaning that multiple identical requests have the same effect as a single request. The response to a GET request typically includes the requested resource or its representation in the message body.

- **POST**: Used to send data to the server to create or update a resource. It is not idempotent, meaning that multiple identical requests may have different effects. The response to a POST request typically includes the representation of the created or updated resource in the message body.

- **PUT**: Used to update an existing resource on the server. It is idempotent, meaning that multiple identical requests have the same effect as a single request. The response to a PUT request typically includes the representation of the updated resource in the message body.

- **DELETE**: Used to delete a resource from the server. It is idempotent, meaning that multiple identical requests have the same effect as a single request. The response to a DELETE request typically includes a confirmation message in the message body.

- **PATCH**: Used to partially update an existing resource on the server. It is not idempotent, meaning that multiple identical requests may have different effects. The response to a PATCH request typically includes the representation of the updated resource in the message body.

- **OPTIONS**: Used to retrieve the available options for a resource. It is a safe and idempotent method, meaning that multiple identical requests have the same effect as a single request. The response to an OPTIONS request typically includes information about the supported methods, headers, and other options for the resource.

These HTTP request methods allow clients to interact with server resources in a standardized and consistent manner, regardless of the specific implementation details of the server.

## HTTP Response Codes

HTTP response codes are three-digit codes that indicate the status of the HTTP response message. There are five classes of HTTP response codes, each representing a different type of response:

- **1xx** (_Informational_): These status codes indicate that the server has received the request and is continuing to process it. The most common of these codes is `100`, which indicates that the server has received the initial part of the request and is waiting for the client to send the remaining parts.

- **2xx** (_Successful_): These status codes indicate that the server has successfully received, understood, and processed the request. The most common of these codes is `200`, which indicates that the request was successful and the server is returning the requested data.

- **3xx** (_Redirection_): These status codes indicate that the client needs to take additional action to complete the request. The most common of these codes is `302`, which indicates that the requested resource has temporarily moved to a new URL.

- **4xx** (_Client Error_): These status codes indicate that the server could not process the request due to an error on the client's side. The most common of these codes is `404`, which indicates that the requested resource could not be found on the server.

- **5xx** (_Server Error_): These status codes indicate that the server could not process the request due to an error on the server's side. The most common of these codes is `500`, which indicates that an internal server error occurred, preventing the request from being processed.

HTTP response codes provide a standardized way for servers to communicate the status of a request back to the client, allowing clients to respond appropriately to errors or other unexpected situations. By checking HTTP response codes, clients can determine whether the request was successful or not and take necessary actions based on the response.

## Examples of HTTP Response Codes

### 1xx (Informational)

- 100 - Continue
- 101 - Switching Protocols
- 102 - Processing

### 2xx (Successful)

- 200 - OK
- 201 - Created
- 202 - Accepted
- 204 - No Content

### 3xx (Redirection)

- 300 - Multiple Choices
- 301 - Moved Permanently
- 302 - Found
- 304 - Not Modified
- 307 - Temporary Redirect

### 4xx (Client Error)

- 400 - Bad Request
- 401 - Unauthorized
- 403 - Forbidden
- 404 - Not Found
- 409 - Conflict
- 415 - Unsupported Media Type
- 429 - Too Many Requests

### 5xx (Server Error)

- 500 - Internal Server Error
- 501 - Not Implemented
- 502 - Bad Gateway
- 503 - Service Unavailable
- 504 - Gateway Timeout

These are just a few examples of the many HTTP response codes available. It's important to note that different web servers or applications may implement additional response codes specific to their implementation.

Sources:

- [HTTP Methods - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [HTTP Status Codes - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- 
# HTTP (_Hypertext Transfer Protocol_)

Bu bölümde, HTTP, istek yöntemleri ve yanıt kodları hakkında konuşacağız.

![HTTP](HTTP.webp)

Görsel kaynağı: Dall-E by OpenAI

- [HTTP (_Hypertext Transfer Protocol_)](#http-hypertext-transfer-protocol)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [HTTP Nedir?](#http-nedir)
  - [HTTP İstek Yöntemleri](#http-istek-yöntemleri)
  - [HTTP Yanıt Kodları](#http-yanıt-kodları)
  - [HTTP Yanıt Kodu Örnekleri](#http-yanıt-kodu-örnekleri)
    - [1xx (Bilgilendirme)](#1xx-bilgilendirme)
    - [2xx (Başarılı)](#2xx-başarılı)
    - [3xx (Yönlendirme)](#3xx-yönlendirme)
    - [4xx (İstemci Hatası)](#4xx-istemci-hatası)
    - [5xx (Sunucu Hatası)](#5xx-sunucu-hatası)

## Öğrenme Çıktıları

Bu bölümün sonunda şunları yapabiliyor olacaksınız:

- HTTP'nin ne olduğunu ve nasıl çalıştığını açıklayabileceksiniz.
- Çeşitli HTTP istek yöntemlerini ve kullanım senaryolarını açıklayabileceksiniz.
- HTTP yanıt kodlarını ve anlamlarını tanımlayabileceksiniz.
- HTTP yanıt kodlarının, isteklerin sonuçlarını ve durumlarını belirtmek için nasıl kullanıldığını açıklayabileceksiniz.

## HTTP Nedir?

HTTP, **Hypertext Transfer Protocol** (Hiper Metin Transfer Protokolü) anlamına gelir. İnternet üzerinden veri iletimi için kullanılan bir uygulama katmanı protokolüdür.

HTTP, Dünya Çapında Ağ'ın (World Wide Web) temelini oluşturur ve web tarayıcılarının web sayfalarını, resimleri, videoları ve diğer içerikleri web sunucularından talep etmesini ve almasını sağlar. Web sunucuları da bu istekleri yanıtlamak için HTTP kullanır ve talep edilen içeriği istemciye geri gönderir.

HTTP, istemci-sunucu modelinde çalışır; burada istemci, sunucuya bir istek mesajı gönderir ve sunucu, yanıt mesajı ile geri döner. HTTP istekleri genellikle kullanıcının web tarayıcısı veya diğer istemci tarafı uygulamaları tarafından başlatılır ve çeşitli türde bilgiler içerebilir; örneğin istek yöntemleri (GET, POST, PUT, DELETE gibi), başlıklar ve veriler.

HTTP, **stateless** (durumsuz) bir protokoldür; yani her istek ve yanıt bağımsızdır ve istemci ile sunucu arasındaki önceki iletişimlere dayanmaz. Bu, daha büyük ölçeklenebilirlik ve esneklik sağlar ancak istemci ve sunucu arasında oturum bazlı iletişimi sürdürmek için çerezler veya oturum belirteçleri gibi ek mekanizmalar gerektirir.

## HTTP İstek Yöntemleri

HTTP istek yöntemleri, HTTP isteğinde yer alan URI (Uniform Resource Identifier - Evrensel Kaynak Tanımlayıcı) tarafından tanımlanan bir kaynağa yapılacak işlemi belirtir. En yaygın HTTP istek yöntemleri şunlardır:

- **GET**: Sunucudan bir kaynak talep etmek için kullanılır. Güvenli ve idempotent bir yöntemdir, yani birden fazla aynı istek, tek bir isteğin etkisiyle aynı sonuca yol açar. GET isteğine verilen yanıt genellikle talep edilen kaynağın veya onun temsili olan verinin mesaj gövdesini içerir.

- **POST**: Sunucuya veri göndermek ve bir kaynağı oluşturmak veya güncellemek için kullanılır. İdempotent değildir, yani birden fazla aynı istek farklı etkiler yaratabilir. POST isteğine verilen yanıt genellikle oluşturulan veya güncellenen kaynağın temsili olan veriyi içerir.

- **PUT**: Sunucudaki mevcut bir kaynağı güncellemek için kullanılır. İdempotenttir, yani birden fazla aynı istek, tek bir isteğin etkisiyle aynı sonuca yol açar. PUT isteğine verilen yanıt genellikle güncellenen kaynağın temsili olan veriyi içerir.

- **DELETE**: Sunucudan bir kaynağı silmek için kullanılır. İdempotenttir, yani birden fazla aynı istek, tek bir isteğin etkisiyle aynı sonuca yol açar. DELETE isteğine verilen yanıt genellikle silme işleminin onayını içerir.

- **PATCH**: Sunucudaki mevcut bir kaynağı kısmi olarak güncellemek için kullanılır. İdempotent değildir, yani birden fazla aynı istek farklı etkiler yaratabilir. PATCH isteğine verilen yanıt genellikle güncellenen kaynağın temsili olan veriyi içerir.

- **OPTIONS**: Bir kaynak için mevcut olan seçenekleri almak için kullanılır. Güvenli ve idempotent bir yöntemdir, yani birden fazla aynı istek, tek bir isteğin etkisiyle aynı sonuca yol açar. OPTIONS isteğine verilen yanıt genellikle desteklenen yöntemler, başlıklar ve kaynak için diğer seçenekler hakkında bilgi içerir.

Bu HTTP istek yöntemleri, istemcilerin sunucu kaynaklarıyla standart ve tutarlı bir şekilde etkileşimde bulunmalarını sağlar, sunucunun özel uygulama detaylarından bağımsız olarak.

## HTTP Yanıt Kodları

HTTP yanıt kodları, HTTP yanıt mesajının durumunu belirten üç haneli kodlardır. HTTP yanıt kodları beş sınıfa ayrılır, her bir sınıf farklı bir yanıt türünü temsil eder:

- **1xx** (_Bilgilendirme_): Bu durum kodları, sunucunun isteği aldığını ve işlemeye devam ettiğini gösterir. Bu kodlardan en yaygın olanı `100`'dür ve sunucunun isteğin ilk kısmını aldığını ve istemcinin geri kalan kısmı göndermesini beklediğini gösterir.

- **2xx** (_Başarılı_): Bu durum kodları, sunucunun isteği başarıyla alıp anladığını ve işlediğini gösterir. Bu kodlardan en yaygın olanı `200`'dür ve isteğin başarılı olduğunu ve sunucunun talep edilen veriyi döndüğünü gösterir.

- **3xx** (_Yönlendirme_): Bu durum kodları, istemcinin isteği tamamlamak için ek bir işlem yapması gerektiğini gösterir. Bu kodlardan en yaygın olanı `302`'dir ve talep edilen kaynağın geçici olarak yeni bir URL'ye taşındığını gösterir.

- **4xx** (_İstemci Hatası_): Bu durum kodları, sunucunun isteği, istemcinin tarafında bir hata nedeniyle işleyemediğini gösterir. Bu kodlardan en yaygın olanı `404`'tür ve talep edilen kaynağın sunucuda bulunamadığını gösterir.

- **5xx** (_Sunucu Hatası_): Bu durum kodları, sunucunun isteği, sunucunun tarafındaki bir hata nedeniyle işleyemediğini gösterir. Bu kodlardan en yaygın olanı `500`'dür ve sunucuda bir iç hata oluştuğunu, bu nedenle isteğin işlenemediğini gösterir.

HTTP yanıt kodları, sunucuların isteğin durumunu istemciye iletmek için standart bir yol sunar ve istemcilerin hatalara veya diğer beklenmedik durumlardaki yanıtları uygun şekilde yönetmelerine olanak tanır. HTTP yanıt kodlarını kontrol ederek istemciler, isteğin başarılı olup olmadığını belirleyebilir ve yanıt doğrultusunda gerekli işlemleri yapabilir.

## HTTP Yanıt Kodu Örnekleri

### 1xx (Bilgilendirme)

- 100 - Devam Et
- 101 - Protokol Değiştiriliyor
- 102 - İşlem Yapılıyor

### 2xx (Başarılı)

- 200 - Tamam
- 201 - Oluşturuldu
- 202 - Kabul Edildi
- 204 - İçerik Yok

### 3xx (Yönlendirme)

- 300 - Birden Fazla Seçenek
- 301 - Kalıcı Olarak Taşındı
- 302 - Bulundu
- 304 - Değiştirilmedi
- 307 - Geçici Yönlendirme

### 4xx (İstemci Hatası)

- 400 - Kötü İstek
- 401 - Yetkisiz
- 403 - Yasak
- 404 - Bulunamadı
- 409 - Çatışma
- 415 - Desteklenmeyen Medya Türü
- 429 - Çok Fazla İstek

### 5xx (Sunucu Hatası)

- 500 - İç Sunucu Hatası
- 501 - Uygulanmadı
- 502 - Kötü Ağ Geçidi
- 503 - Hizmet Kullanılamaz
- 504 - Ağ Geçidi Zaman Aşımı

Bunlar, mevcut olan birçok HTTP yanıt kodunun sadece birkaç örneğidir. Farklı web sun

