# Authentication and Authorization

In this section, we will discuss the concepts and processes of authentication and authorization. Authentication is the process by which a user verifies their identity in a system, while authorization determines what actions a user is allowed to perform.

![Auth](Auth.webp)

Image source: Dall-E by OpenAI

- [Authentication and Authorization](#authentication-and-authorization)
  - [Learning Outcomes](#learning-outcomes)
  - [Authentication](#authentication)
  - [Authorization](#authorization)
  - [General Overview of Authentication and Authorization](#general-overview-of-authentication-and-authorization)
  - [Authentication and Authorization Process in Front-End Applications](#authentication-and-authorization-process-in-front-end-applications)
  - [Authentication and Authorization Process in Back-End Applications](#authentication-and-authorization-process-in-back-end-applications)

## Learning Outcomes

By the end of this section, students should be able to:

- Explain the concepts of authentication and authorization.
- Describe the processes of authentication and authorization.

## Authentication

Authentication is the process by which one entity (user, system, or object) verifies the identity of another entity, typically based on some type of credentials:

- Something you know (e.g., password, PIN, CAPTCHA, security question);
- Something you have (e.g., ID card, bank card, phone number, email, hardware token, password card, certificate);
- Something you are (e.g., fingerprint, facial recognition, iris structure).

## Authorization

Authorization is the process that grants (or denies) access to (network) resources. For example, most e-commerce security systems rely on a two-step process. First, authentication checks whether the user is indeed who they claim to be, followed by authorization, which allows the user to access designated resources.

[Source](https://sisu.ut.ee/autentimine/m%C3%B5isted)

## General Overview of Authentication and Authorization

When we have an application or API with different users, we likely need to assign different roles to those users. For instance, an API might need a separate administrator role to make changes to user data or other system settings that an average user should not access.

The user authentication process typically follows these steps:

1. The user submits their authentication credentials (e.g., username and password) to the server.
2. The server checks if the provided username and password are correct.
3. The server also verifies the user's permissions (e.g., user, admin).
4. If authentication is successful, the server generates a token for the user, which is sent back to the client for future authentication. The token typically includes the user identifier, user role or permissions, and an expiration time.
5. The user sends the token with each subsequent request, allowing the server to identify the user and their permissions.
6. The server verifies the token and decides if the user has the right to make the requested action.
7. If the user has the right, the request is processed accordingly.
8. If the user does not have the right, the request returns an appropriate error message or status.
9. The authentication token expires after a certain period, and the user must re-authenticate to receive a new token.

```mermaid
sequenceDiagram
    participant Client
    participant Server
    Client->>Server: Send authentication credentials
    Server->>Server: Verify user
    Server->>Server: Generate token
    Server->>Client: Send token
    Client->>Server: Send request with token
    Server->>Server: Verify token
    Server->>Server: Decide if user has access
    Server->>Client: Return response
```

## Authentication and Authorization Process in Front-End Applications

From the front-end perspective, we need to provide the user with a way to enter their username and password (or another authentication method) and then send this data to the server. If authentication is successful, the server sends back an authentication token, which must be stored and sent with each request.

For example, the token is typically stored in the user's browser's `localStorage` or `sessionStorage` object. When the user closes the browser or tab, the `sessionStorage` object is cleared, but the `localStorage` object remains even when the browser is closed and reopened.

## Authentication and Authorization Process in Back-End Applications

From the back-end perspective, we need to create server-side functionality to receive user authentication credentials, verify them, and generate an authentication token. The server must also be able to check the token sent with each request and decide if the user has the right to perform the requested action.

In this course, we will use the `JWT` (JSON Web Token) technology for generating and verifying tokens. JWT is a standard that defines a compact and self-contained way to securely transmit information as a JSON object.

When generating the JWT, a secret key is used, which is kept only on the server side and is used to sign the token. Once signed, the token cannot be modified without altering the signature, ensuring the token's authenticity.

To verify the token, we use the same secret key to decode the token and check if it is valid and the user is authenticated.

We implement the token verification using a middleware function that checks each request and decides whether the user has the right to perform the requested action. This function can be applied to any routes where we want to enforce authentication and authorization.


# Kimlik Doğrulama ve Yetkilendirme

Bu bölümde, kimlik doğrulama ve yetkilendirme kavramlarını ve süreçlerini ele alacağız. Kimlik doğrulama, bir kullanıcının kimliğini bir sistemde doğruladığı süreçtir. Yetkilendirme ise bir kullanıcının hangi işlemleri yapmasına izin verildiğini belirler.

![Kimlik Doğrulama ve Yetkilendirme](Auth.webp)

Görsel Kaynağı: Dall-E by OpenAI

- [Kimlik Doğrulama ve Yetkilendirme](#kimlik-doğrulama-ve-yetkilendirme)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [Kimlik Doğrulama](#kimlik-doğrulama)
  - [Yetkilendirme](#yetkilendirme)
  - [Kimlik Doğrulama ve Yetkilendirme Genel Bakış](#kimlik-doğrulama-ve-yetkilendirme-genel-bakış)
  - [Front-End Uygulamalarda Kimlik Doğrulama ve Yetkilendirme Süreci](#front-end-uygulamalarda-kimlik-doğrulama-ve-yetkilendirme-süreci)
  - [Back-End Uygulamalarda Kimlik Doğrulama ve Yetkilendirme Süreci](#back-end-uygulamalarda-kimlik-doğrulama-ve-yetkilendirme-süreci)

## Öğrenme Çıktıları

Bu bölümü tamamladıktan sonra öğrenciler:

- Kimlik doğrulama ve yetkilendirme kavramlarını açıklayabilecek,
- Kimlik doğrulama ve yetkilendirme süreçlerini tanımlayabileceklerdir.

## Kimlik Doğrulama

Kimlik doğrulama, bir varlığın (kullanıcı, sistem veya nesne), başka bir varlığın kimliğini bazı türde kimlik bilgileri aracılığıyla doğruladığı süreçtir:

- Bildiğiniz bir şey (örn. şifre, PIN, CAPTCHA, güvenlik sorusu);
- Sahip olduğunuz bir şey (örn. kimlik kartı, banka kartı, telefon numarası, e-posta, donanım anahtarı, şifre kartı, sertifika);
- Olduğunuz bir şey (örn. parmak izi, yüz tanıma, iris yapısı).

## Yetkilendirme

Yetkilendirme, (ağ) kaynaklarına erişim izni veren (veya reddeden) süreçtir. Örneğin, çoğu e-ticaret güvenlik sistemi iki aşamalı bir sürece dayanır. İlk olarak, kimlik doğrulama kullanıcının iddia ettiği kişi olduğunu doğrular. Daha sonra yetkilendirme, kullanıcının belirlenen kaynaklara erişmesine izin verir.

[Kaynak](https://sisu.ut.ee/autentimine/m%C3%B5isted)

## Kimlik Doğrulama ve Yetkilendirme Genel Bakış

Bir uygulama veya API'de farklı kullanıcılar olduğunda, büyük olasılıkla bu kullanıcılara farklı roller atamamız gerekir. Örneğin, bir API, kullanıcı verilerini veya diğer sistem ayarlarını değiştirmek için standart bir kullanıcının erişemeyeceği ayrı bir yönetici rolüne ihtiyaç duyabilir.

Kullanıcı kimlik doğrulama süreci genellikle şu adımları izler:

1. Kullanıcı, kimlik doğrulama kimlik bilgilerini (örn. kullanıcı adı ve şifre) sunucuya gönderir.
2. Sunucu, sağlanan kullanıcı adı ve şifrenin doğru olup olmadığını kontrol eder.
3. Sunucu, kullanıcının izinlerini de doğrular (örn. kullanıcı, yönetici).
4. Eğer kimlik doğrulama başarılı olursa, sunucu kullanıcı için bir token (belirteç) oluşturur ve bu token gelecekteki kimlik doğrulama için istemciye gönderilir. Token genellikle kullanıcı kimliği, kullanıcı rolü veya izinleri ve bir son kullanma zamanı içerir.
5. Kullanıcı, sonraki her istekte token'ı gönderir ve sunucu bu sayede kullanıcının kimliğini ve izinlerini belirler.
6. Sunucu, token'ı doğrular ve kullanıcının talep edilen işlemi yapma hakkı olup olmadığına karar verir.
7. Kullanıcının hakkı varsa istek işlenir.
8. Kullanıcının hakkı yoksa istek, uygun bir hata mesajı veya durum döner.
9. Kimlik doğrulama token'ı belirli bir süre sonra sona erer ve kullanıcı, yeni bir token almak için yeniden kimlik doğrulama yapmalıdır.

```mermaid
sequenceDiagram
    participant İstemci
    participant Sunucu
    İstemci->>Sunucu: Kimlik doğrulama kimlik bilgilerini gönder
    Sunucu->>Sunucu: Kullanıcıyı doğrula
    Sunucu->>Sunucu: Token oluştur
    Sunucu->>İstemci: Token gönder
    İstemci->>Sunucu: Token ile istek gönder
    Sunucu->>Sunucu: Token doğrula
    Sunucu->>Sunucu: Kullanıcının erişim hakkına karar ver
    Sunucu->>İstemci: Yanıt döndür

```

## Front-End Uygulamalarda Kimlik Doğrulama ve Yetkilendirme Süreci
Front-end açısından, kullanıcının kullanıcı adı ve şifre (veya başka bir kimlik doğrulama yöntemi) girebileceği bir yöntem sunmamız ve bu veriyi sunucuya göndermemiz gerekir. Eğer kimlik doğrulama başarılı olursa, sunucu bir kimlik doğrulama token'ı gönderir. Bu token saklanmalı ve her istekle birlikte gönderilmelidir.

Örneğin, token genellikle kullanıcının tarayıcısındaki `localStorage` veya `sessionStorage` nesnesine kaydedilir. Kullanıcı tarayıcıyı veya sekmeyi kapattığında, `sessionStorage` nesnesi temizlenir, ancak `localStorage` nesnesi tarayıcı kapatılıp tekrar açıldığında bile kalır.

## Back-End Uygulamalarda Kimlik Doğrulama ve Yetkilendirme Süreci
Back-end açısından, kullanıcı kimlik doğrulama kimlik bilgilerini almak, doğrulamak ve bir kimlik doğrulama token'ı oluşturmak için sunucu tarafında bir işlevsellik oluşturmamız gerekir. Sunucu ayrıca, her istekle gönderilen token'ı kontrol edebilmeli ve kullanıcının talep edilen işlemi yapma hakkına sahip olup olmadığına karar verebilmelidir.

Bu kursta, token oluşturma ve doğrulama için `JWT` (JSON Web Token) teknolojisini kullanacağız. JWT, bilgileri güvenli bir şekilde JSON nesnesi olarak iletmek için kompakt ve bağımsız bir yöntem tanımlayan bir standarttır.

JWT oluşturulurken yalnızca sunucu tarafında saklanan ve token'ı imzalamak için kullanılan bir gizli anahtar kullanılır. İmzalandıktan sonra, token imzası değiştirilmeden düzenlenemez ve bu da token'ın doğruluğunu garanti eder.

Token'ı doğrulamak için aynı gizli anahtar kullanılarak token çözümlenir ve geçerli olup olmadığı kontrol edilir.

Bu işlem, her isteği kontrol eden ve kullanıcının talep edilen işlemi yapmaya yetkili olup olmadığına karar veren bir middleware işleviyle uygulanır. Bu işlev, kimlik doğrulama ve yetkilendirme uygulamak istediğimiz rotalara eklenebilir.




