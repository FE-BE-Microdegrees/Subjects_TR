# JWT (_JSON Web Token_)

In this section, we will discuss JWT (_JSON Web Token_), an open standard used for securely transmitting data between parties in JSON format.

![JWT](JWT.webp)

Image source: DALL-E by OpenAI

## Learning Outcomes

By the end of this section, students should be able to:

- Explain what JWT is and how it works.
- Describe the structure of JWT and its components.
- Create and validate JWTs.
- Use JWTs in authentication and authorization processes.

## JWT

JWT (_JSON Web Token_) is an open standard (RFC 7519) used for securely transmitting data between parties in JSON format. It is particularly useful for authentication and information exchange, allowing reliable and efficient information transfer. JWTs are compact and easy to use in various scenarios, including authentication and authorization in web applications.

### JWT Components

A JWT consists of three parts, separated by periods (.):

- **Header:** Contains information about the type of token and the signing algorithm being used (e.g., HMAC SHA256 or RSA).

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

- **Payload:** Contains claims, which are the encoded information in the JWT. Claims can be standardized, public, or private.

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

- **Signature:** Created to ensure the integrity and authenticity of the token. The signature is generated using a secret key or a public/private key pair.

```bash
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)
```

### JWT Structure

The complete JWT structure looks like this:

```bash
xxxxx.yyyyy.zzzzz
```

Where `xxxxx` is the header, `yyyyy` is the payload, and `zzzzz` is the signature, all encoded in base64-url.

## When to Use JWT?

- **Authorization:** This is the most common scenario for using JWTs. Once a user logs in, each subsequent request contains a JWT, allowing the user to access the routes, services, and resources authorized for that token.
- **Information Exchange:** JSON Web Tokens are a good way to securely transmit information between parties. Since JWTs can be signed, for example, using public/private key pairs, you can be sure the senders are who they say they are. Additionally, because the signature is computed using the header and payload, you can also verify that the content has not been altered.

### Advantages

- **Compactness:** JWTs are compact, meaning they can be easily transmitted via URLs, HTTP headers, and POST data.
- **Self-Contained:** Tokens are self-contained as they contain all the necessary information. You can validate the token without additional data, making the system more efficient and flexible.
- **Security:** JWTs ensure data integrity and enable authentication and authorization, which is useful for establishing secure connections.

### Disadvantages

- **Token Leakage:** JWTs cannot be revoked or invalidated once issued. If a JWT is leaked, it can be dangerous as it may grant unauthorized access, necessitating additional protective measures.

## Creating and Validating JWTs

### Creating JWTs

The process of creating a JWT involves generating the header, payload, and signature, then combining them.

#### Example in Node.js

To create and validate JWTs in Node.js, you can use the `jsonwebtoken` library.

- **Install the jsonwebtoken library:**

```bash
npm install jsonwebtoken
```

- **Creating a JWT:**

```javascript
const jwt = require("jsonwebtoken");

const payload = {
  sub: "1234567890",
  name: "John Doe",
  admin: true,
};

const secret = "your-256-bit-secret";

const token = jwt.sign(payload, secret, { algorithm: "HS256" });
console.log(token);
```

### Validating JWTs

Validating a JWT involves decoding the received token and verifying the signature to ensure its authenticity and integrity.

#### Example in Node.js

1. **Validating a JWT:**

```javascript
const token =
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.D1lvcHfxDQn0EnyFCWm08FUBKm0tC3GtBCVm5qkaGTI";

jwt.verify(token, secret, (err, decoded) => {
  if (err) {
    console.log("Token is invalid or expired.");
  } else {
    console.log("Token is valid:", decoded);
  }
});
```

## Using JWT for Authentication and Authorization

### Authentication

JWTs are often used for user authentication. When a user logs in, the server creates a JWT containing the user's identity and possible permissions. This JWT is sent back to the user and stored in the browser as a cookie or in local storage.

#### Example - 1

- **User Login and JWT Creation:**

```javascript
app.post("/login", (req, res) => {
  const { username, password } = req.body;
  // Check the username and password
  const user = users.find(
    (u) => u.username === username && u.password === password
  );
  if (user) {
    const token = jwt.sign({ sub: user.id, name: user.username }, secret, {
      expiresIn: "1h",
    });
    res.json({ token });
  } else {
    res.status(401).send("Invalid credentials");
  }
});
```

### Authorization

Once a user is authenticated and has a JWT, the server can use that token to check the user's identity and permissions when they request protected resources.

#### Example - 2

- **Using JWT for Authorization:**

```javascript
const authenticateJWT = (req, res, next) => {
  const token = req.header("Authorization");
  if (!token) return res.status(401).send("Access Denied");

  try {
    const verified = jwt.verify(token, secret);
    req.user = verified;
    next();
  } catch (error) {
    res.status(400).send("Invalid Token");
  }
};

app.get("/protected", authenticateJWT, (req, res) => {
  res.send("This is a protected route");
});
```

## Sources

- [JWT.io](https://jwt.io/)
- [RFC 7519: JSON Web Token (JWT)](https://tools.ietf.org/html/rfc7519)
- [jsonwebtoken Documentation](https://www.npmjs.com/package/jsonwebtoken)
- [Node.js Official Documentation](https://nodejs.org/en/docs/)

## Review Questions

- What is JWT and how does it work?
- Describe the structure of JWT and its components.
- How do you create and validate JWTs in Node.js using the `jsonwebtoken` library?
- How is JWT used in authentication and authorization processes?
- What are the advantages of using JWT?

# JWT (_JSON Web Token_)

Bu bölümde, JSON formatında güvenli bir şekilde veri iletimi için kullanılan açık bir standart olan JWT (_JSON Web Token_) hakkında konuşacağız.

![JWT](JWT.webp)

Görsel Kaynağı: DALL-E by OpenAI

## Öğrenme Çıktıları

Bu bölümü tamamladıktan sonra öğrenciler:

- JWT'nin ne olduğunu ve nasıl çalıştığını açıklayabilecek,
- JWT'nin yapısını ve bileşenlerini tanımlayabilecek,
- JWT oluşturup doğrulayabilecek,
- JWT'yi kimlik doğrulama ve yetkilendirme süreçlerinde kullanabileceklerdir.

## JWT Nedir?

JWT (_JSON Web Token_), JSON formatında veri iletimi için kullanılan açık bir standarttır (RFC 7519). Kimlik doğrulama ve bilgi alışverişi için oldukça kullanışlıdır ve güvenilir, verimli bir bilgi aktarımı sağlar. JWT'ler kompakt bir yapıya sahiptir ve web uygulamalarında kimlik doğrulama ve yetkilendirme gibi çeşitli senaryolarda kullanımı kolaydır.

### JWT Bileşenleri

Bir JWT, üç kısımdan oluşur ve noktalar (.) ile ayrılır:

- **Header (Başlık):** Token türü ve kullanılan imzalama algoritması (örneğin, HMAC SHA256 veya RSA) hakkındaki bilgileri içerir.

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```
**Payload(Yük)**: JWT içindeki kodlanmış bilgileri (claims) içerir. Bu bilgiler standart, genel veya özel olabilir.

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
**Signature (İmza)**: Token'ın bütünlüğünü ve doğruluğunu sağlamak için oluşturulur. İmza, gizli bir anahtar veya açık/özel anahtar çifti kullanılarak oluşturulur.

```bash
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)
```
## JWT Yapısı
Tam bir JWT şu şekilde görünür:
```bash
xxxxx.yyyyy.zzzzz
```

Burada `xxxxx` başlık, `yyyyy` yük ve `zzzzz` imzadır. Tüm bu parçalar base64-url ile kodlanmıştır.

## JWT Ne Zaman Kullanılır?
**Yetkilendirme**: JWT'nin en yaygın kullanım senaryosu yetkilendirmedir. Bir kullanıcı giriş yaptıktan sonra, her sonraki istekte JWT gönderilir ve bu token, kullanıcıya belirli yollar, servisler ve kaynaklara erişim yetkisi sağlar.
**Bilgi Alışverişi**: JSON Web Token'lar, taraflar arasında güvenli bilgi iletimi için iyi bir yoldur. JWT'ler imzalanabilir (örneğin, açık/özel anahtar çifti kullanılarak), bu da göndericilerin kimliğini doğrulamayı sağlar. Ayrıca, imza başlık ve yük üzerinden hesaplandığından içeriğin değişmediğinden emin olunabilir.

## Avantajlar
**Kompaktlık**: JWT'ler kompakt bir yapıya sahiptir, bu yüzden URL'ler, HTTP başlıkları ve POST verileri ile kolayca iletilebilirler.
**Kendi Kendine Yeterlilik**: Token'lar, tüm gerekli bilgileri içerdiğinden bağımsız olarak doğrulanabilir. Bu da sistemi daha verimli ve esnek hale getirir.
**Güvenlik**: JWT'ler veri bütünlüğünü sağlar ve kimlik doğrulama ile yetkilendirme süreçlerinde güvenli bağlantılar oluşturur.
## Dezavantajlar
**Token Sızıntısı**: JWT'ler oluşturulduktan sonra iptal edilemez veya geçersiz kılınamaz. Eğer bir JWT sızdırılırsa, yetkisiz erişim sağlayabilir. Bu nedenle ek koruyucu önlemler alınmalıdır.
## JWT Oluşturma ve Doğrulama
**JWT Oluşturma**
JWT oluşturma işlemi, başlık, yük ve imza oluşturmayı ve bunları birleştirmeyi içerir.

**Node.js Örneği**
JWT oluşturmak ve doğrulamak için jsonwebtoken kütüphanesini kullanabilirsiniz.

**jsonwebtoken kütüphanesini yükleyin**:

```bash
npm install jsonwebtoken
```
**JWT oluşturma:**

```javascript
const jwt = require("jsonwebtoken");

const payload = {
  sub: "1234567890",
  name: "John Doe",
  admin: true,
};

const secret = "your-256-bit-secret";

const token = jwt.sign(payload, secret, { algorithm: "HS256" });
console.log(token);
```

## JWT Doğrulama
JWT doğrulama işlemi, alınan token'ı çözmeyi ve imzayı doğrulamayı içerir. Böylece token'ın bütünlüğü ve doğruluğu sağlanır.

**Node.js Örneği**

**JWT doğrulama**:
```javascript

const token =
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.D1lvcHfxDQn0EnyFCWm08FUBKm0tC3GtBCVm5qkaGTI";

jwt.verify(token, secret, (err, decoded) => {
  if (err) {
    console.log("Token geçersiz veya süresi dolmuş.");
  } else {
    console.log("Token geçerli:", decoded);
  }
});
```
## JWT Kullanarak Kimlik Doğrulama ve Yetkilendirme

### Kimlik Doğrulama

JWT, genellikle kullanıcı kimlik doğrulaması için kullanılır. Bir kullanıcı giriş yaptığında, sunucu kullanıcının kimliğini ve izinlerini içeren bir JWT oluşturur. Bu JWT, kullanıcıya geri gönderilir ve tarayıcıda çerez veya `localStorage` içinde saklanır.

#### Örnek - 1

**Kullanıcı Girişi ve JWT Oluşturma:**

```javascript
app.post("/login", (req, res) => {
  const { username, password } = req.body;
  // Kullanıcı adı ve şifre kontrolü
  const user = users.find(
    (u) => u.username === username && u.password === password
  );
  if (user) {
    const token = jwt.sign({ sub: user.id, name: user.username }, secret, {
      expiresIn: "1h",
    });
    res.json({ token });
  } else {
    res.status(401).send("Geçersiz kimlik bilgileri");
  }
});
```

### Yetkilendirme
Bir kullanıcı kimlik doğrulaması yapıp bir JWT aldıktan sonra, sunucu bu token'ı kullanarak kullanıcının kimliğini ve yetkilerini, korunan kaynaklara istek yaptığında kontrol edebilir.

## Örnek - 2
**JWT Kullanarak Yetkilendirme**:
```javascript
const authenticateJWT = (req, res, next) => {
  const token = req.header("Authorization");
  if (!token) return res.status(401).send("Erişim Reddedildi");

  try {
    const verified = jwt.verify(token, secret);
    req.user = verified;
    next();
  } catch (error) {
    res.status(400).send("Geçersiz Token");
  }
};

app.get("/protected", authenticateJWT, (req, res) => {
  res.send("Bu korunan bir rotadır");
});
```


Here’s the translated part in Turkish with GitHub-compatible Markdown formatting:

markdown
Kopyala
Düzenle
## JWT Kullanarak Kimlik Doğrulama ve Yetkilendirme

### Kimlik Doğrulama

JWT, genellikle kullanıcı kimlik doğrulaması için kullanılır. Bir kullanıcı giriş yaptığında, sunucu kullanıcının kimliğini ve izinlerini içeren bir JWT oluşturur. Bu JWT, kullanıcıya geri gönderilir ve tarayıcıda çerez veya `localStorage` içinde saklanır.

#### Örnek - 1

**Kullanıcı Girişi ve JWT Oluşturma:**

```javascript
app.post("/login", (req, res) => {
  const { username, password } = req.body;
  // Kullanıcı adı ve şifre kontrolü
  const user = users.find(
    (u) => u.username === username && u.password === password
  );
  if (user) {
    const token = jwt.sign({ sub: user.id, name: user.username }, secret, {
      expiresIn: "1h",
    });
    res.json({ token });
  } else {
    res.status(401).send("Geçersiz kimlik bilgileri");
  }
});
```
## Yetkilendirme
Bir kullanıcı kimlik doğrulaması yapıp bir JWT aldıktan sonra, sunucu bu token'ı kullanarak kullanıcının kimliğini ve yetkilerini, korunan kaynaklara istek yaptığında kontrol edebilir.

## Örnek - 2
**JWT Kullanarak Yetkilendirme**:
```javascript
const authenticateJWT = (req, res, next) => {
  const token = req.header("Authorization");
  if (!token) return res.status(401).send("Erişim Reddedildi");

  try {
    const verified = jwt.verify(token, secret);
    req.user = verified;
    next();
  } catch (error) {
    res.status(400).send("Geçersiz Token");
  }
};

app.get("/protected", authenticateJWT, (req, res) => {
  res.send("Bu korunan bir rotadır");
});
```
## Kaynaklar

- [JWT.io](https://jwt.io/)
- [RFC 7519: JSON Web Token (JWT)](https://tools.ietf.org/html/rfc7519)
- [jsonwebtoken Documentation](https://www.npmjs.com/package/jsonwebtoken)
- [Node.js Official Documentation](https://nodejs.org/en/docs/)

## Gözden Geçirme Soruları

- JWT nedir ve nasıl çalışır?
- JWT'nin yapısını ve bileşenlerini tanımlayın.
- Node.js'te jsonwebtoken kütüphanesini kullanarak JWT nasıl oluşturulur ve doğrulanır?
- JWT kimlik doğrulama ve yetkilendirme süreçlerinde nasıl kullanılır?
- JWT kullanmanın avantajları nelerdir?
