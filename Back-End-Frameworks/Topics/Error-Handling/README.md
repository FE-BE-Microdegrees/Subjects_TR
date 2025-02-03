# Vigade Haldus (Error Handling) Express API-s

Vigade haldus on kriitiline komponent igas API-s. Õige veahaldus aitab mitte ainult parandada kasutajakogemust, vaid ka hoida rakendust turvalisena ja hooldatavana. Express pakub paindlikke meetodeid vigade haldamiseks, mis võimaldavad teil elegantset ja tõhusat vigade käsitlemist oma API-s rakendada.

![Express Error Handling](Express-Error-Handling.webp)

Pildi allikas: Dall-E by OpenAI

- [Vigade Haldus (Error Handling) Express API-s](#vigade-haldus-error-handling-express-api-s)
  - [Õpiväljundid](#õpiväljundid)
  - [Miks on Veahaldus Oluline?](#miks-on-veahaldus-oluline)
  - [Veahaldus Expressis](#veahaldus-expressis)
    - [Kohandatud Veakäsitlejad Lõpp-punktides](#kohandatud-veakäsitlejad-lõpp-punktides)
    - [Keskne Veakäsitleja Vahevara](#keskne-veakäsitleja-vahevara)
    - [Selgitus](#selgitus)
    - [Asünkroonsete Vigade Käsitlemine](#asünkroonsete-vigade-käsitlemine)
    - [Selgitus](#selgitus-1)
  - [Täiendavad Meetodid Vigade Käsitlemiseks](#täiendavad-meetodid-vigade-käsitlemiseks)
    - [Vigade Logimine](#vigade-logimine)
    - [Valesti Tehtud Päringute Käsitlemine](#valesti-tehtud-päringute-käsitlemine)

## Õpiväljundid

Selle õppematerjali lõpuks peaksid õppijad olema võimelised:

- selgitama, miks on veahaldus Expressis oluline.
- rakendama kohandatud veakäsitlejaid Expressi API-s;
- kasutama vahevara (middleware) vigade haldamiseks;
- kasutama keskse veakäsitleja kasutamist kogu rakenduse ulatuses;
- käsitlema asünkroonseid vigu Expressis.

## Miks on Veahaldus Oluline?

- **Kasutajakogemus**: Hästi kavandatud veahaldus annab kasutajale selged ja kasulikud sõnumid, mis aitavad tal mõista, mis valesti läks ja mida teha järgmiseks.
- **Turvalisus**: Peidab süsteemi siseinfo ja hoiab ära tundliku teabe lekkimise.
- **Hooldatavus**: Lihtsustab vigade jälgimist ja parandamist, andes arendajatele täpsed ja kasulikud logid.
- **Usaldusväärsus**: Tagab, et rakendus suudab jätkata tööd isegi siis, kui tekivad vead.

## Veahaldus Expressis

Expressis saab vigu käsitleda mitmel viisil, sealhulgas:

1. **Kohandatud veakäsitlejad**: Funktsioonid, mis käsitlevad vigu kindlates lõpp-punktides.
2. **Vahevara (middleware)**: Keskse veakäsitleja loomine, mis püüab kinni kõik vead, mis tekivad rakenduses.
3. **Asünkroonsete vigade käsitlemine**: Vigade haldamine asünkroonsetes funktsioonides ja promisis.

### Kohandatud Veakäsitlejad Lõpp-punktides

Mõnikord on vaja käsitleda vigu spetsiaalselt teatud lõpp-punktides. Näiteks, kui päringuga kaasneb vale sisend, saate tagastada kohandatud veateate:

```javascript
// routes/users.js
const express = require("express");
const router = express.Router();

// Näidis GET päring, mis võib tekitada vea
router.get("/:id", (req, res, next) => {
  const userId = req.params.id;

  // Kontrollime, kas ID on number
  if (isNaN(userId)) {
    const error = new Error("Invalid user ID");
    error.status = 400;
    return next(error); // Edastame vea järgmisele vahevarale või veakäsitlejale
  }

  // Otsime kasutajat (näidis)
  const user = { id: userId, name: "John Doe" };

  // Kui kasutajat ei leita
  if (!user) {
    const error = new Error("User not found");
    error.status = 404;
    return next(error);
  }

  // Tagastame kasutaja andmed
  res.json(user);
});

module.exports = router;
```

### Keskne Veakäsitleja Vahevara

Expressis saab luua keskse veakäsitleja vahevara, mis püüab kinni kõik vead, mis tekivad rakenduses. See vahevara paigutatakse pärast kõiki teisi teekondi ja vahevarasid.

```javascript
// app.js
const express = require("express");
const bodyParser = require("body-parser");
const usersRouter = require("./routes/users");

const app = express();

app.use(bodyParser.json());

app.use("/users", usersRouter);

// Keskne veakäsitleja
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```

### Selgitus

- **`app.use((err, req, res, next) => { ... })`**: See on Expressi vahevara veakäsitleja signatuur. Kui mõni teekond või vahevara kutsub `next(error)`, püüab see vahevara vea kinni ja käsitleb seda.
- **`err.status`**: See on määratud veakood, kui see on olemas. Kui ei ole määratud, kasutatakse vaiket `500`.
- **`err.message`**: Veateade, mis tagastatakse vastusena.
- **`console.error(err.stack)`**: Logib vea stack trace serveri konsooli.

### Asünkroonsete Vigade Käsitlemine

Asünkroonsed operatsioonid, nagu andmete pärimine API-st või andmebaasist, võivad tekitada vigu, mis tuleb käsitleda. Expressis saate kasutada `try/catch` plokke ja `next` funktsiooni asünkroonsete vigade käsitlemiseks.

```javascript
// routes/todos.js
const express = require("express");
const router = express.Router();
const todosService = require("../services/todosService");

// Näidis GET päring, mis kasutab async/await
router.get("/:id", async (req, res, next) => {
  try {
    const todoId = req.params.id;

    if (isNaN(todoId)) {
      const error = new Error("Invalid todo ID");
      error.status = 400;
      throw error;
    }

    const todo = await todosService.getById(todoId);

    if (!todo) {
      const error = new Error("Todo not found");
      error.status = 404;
      throw error;
    }

    res.json(todo);
  } catch (error) {
    next(error); // Edastame vea järgmisele vahevarale või veakäsitlejale
  }
});

module.exports = router;
```

### Selgitus

- **`try/catch` plokk**: Kasutatakse asünkroonsete operatsioonide vigade püüdmise ja käsitlemise jaoks.
- **`throw error`**: Visatakse vead `try` plokist `catch` plokki, mis seejärel edasi saadetakse Expressi veakäsitlejale.
- **`next(error)`**: Kutsutakse `catch` plokis, et edastada vea järgmisele vahevarale või veakäsitlejale.

## Täiendavad Meetodid Vigade Käsitlemiseks

### Vigade Logimine

Hea tava on logida vead, et saaksite neid hiljem analüüsida ja parandada. Võite kasutada spetsiaalseid logimisteeke, nagu `winston` või `morgan`, et logida vead välisesse faili või logihaldussüsteemi.

```javascript
const express = require("express");
const morgan = require("morgan");

const app = express();

// Morgan logib kõik päringud
app.use(morgan("dev"));

// Teie teekonnad ja vahevara siia

// Keskne veakäsitleja
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```

### Valesti Tehtud Päringute Käsitlemine

Vigade vältimiseks on hea lisada vahevara, mis püüab kinni kõik valesti tehtud päringud ja tagastab 404 vastuse.

```javascript
// app.js
const express = require("express");
const bodyParser = require("body-parser");
const usersRouter = require("./routes/users");

const app = express();

app.use(bodyParser.json());

app.use("/users", usersRouter);

// Kui ükski teekond ei vasta
app.use((req, res, next) => {
  res.status(404).json({
    success: false,
    message: "Resource not found",
  });
});

// Keskne veakäsitleja
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```

# Express API'lerinde Hata Yönetimi

Hata yönetimi, her API'nin kritik bir bileşenidir. Doğru hata yönetimi, yalnızca kullanıcı deneyimini geliştirmekle kalmaz, aynı zamanda uygulamanın güvenli ve bakımı kolay olmasını sağlar. Express, hataları yönetmek için esnek yöntemler sunar ve API'nizde şık ve etkili hata yönetimi uygulamanıza olanak tanır.

![Express Hata Yönetimi](Express-Error-Handling.webp)

Görsel kaynağı: Dall-E by OpenAI

- [Express API'lerinde Hata Yönetimi](#express-api-lerinde-hata-yonetimi)
  - [Öğrenme Kazanımları](#ogrenme-kazanimlari)
  - [Hata Yönetimi Neden Önemlidir?](#hata-yonetimi-neden-onemlidir)
  - [Express'te Hata Yönetimi](#express-te-hata-yonetimi)
    - [Özel Hata İşleyicileri](#ozel-hata-isleyicileri)
    - [Merkezi Hata İşleyici Middleware](#merkezi-hata-isleyici-middleware)
    - [Açıklama](#aciklama)
    - [Asenkron Hataların Yönetimi](#asenkron-hatalarin-yonetimi)
    - [Açıklama](#aciklama-1)
  - [Hata Yönetimi İçin Ekstra Yöntemler](#hata-yonetimi-icin-ekstra-yontemler)
    - [Hata Günlükleme (Logging)](#hata-gunlukleme-logging)
    - [Geçersiz İsteklerin Yönetimi](#gecersiz-isteklerin-yonetimi)

## Öğrenme Kazanımları

Bu bölümü tamamladıktan sonra öğrenenler:

- Express'te hata yönetiminin neden önemli olduğunu açıklayabilecek;
- Express API'lerinde özel hata işleyicileri uygulayabilecek;
- Middleware kullanarak hata yönetimi yapabilecek;
- Tüm uygulama genelinde merkezi hata işleyici oluşturabilecek;
- Express'te asenkron hataları yönetebilecektir.

## Hata Yönetimi Neden Önemlidir?

- **Kullanıcı Deneyimi**: İyi tasarlanmış hata yönetimi, kullanıcıya açık ve yararlı mesajlar sağlar.
- **Güvenlik**: Sistemin iç yapısını gizleyerek hassas bilgilerin sızmasını önler.
- **Bakım Kolaylığı**: Hata takibini kolaylaştırarak geliştiricilere faydalı günlükler sunar.
- **Güvenilirlik**: Uygulamanın hata durumunda bile çalışmaya devam etmesini sağlar.

## Express'te Hata Yönetimi

Express'te hatalar birkaç farklı şekilde yönetilebilir:

1. **Özel hata işleyicileri**: Belirli uç noktalar için özel hata işleme fonksiyonları.
2. **Middleware (Ara katman yazılımı)**: Tüm uygulama genelinde merkezi bir hata işleyici oluşturma.
3. **Asenkron hata yönetimi**: Asenkron işlemlerde hata yakalama ve işleme.

### Özel Hata İşleyicileri

Bazı uç noktalarda özel hata yönetimi gerekebilir. Örneğin, geçersiz girişlerde özel hata mesajları döndürebilirsiniz:

```javascript
// routes/users.js
const express = require("express");
const router = express.Router();

// Kullanıcı GET isteği, hata oluşturabilir
router.get("/:id", (req, res, next) => {
  const userId = req.params.id;

  if (isNaN(userId)) {
    const error = new Error("Geçersiz kullanıcı ID");
    error.status = 400;
    return next(error);
  }

  const user = { id: userId, name: "John Doe" };

  if (!user) {
    const error = new Error("Kullanıcı bulunamadı");
    error.status = 404;
    return next(error);
  }

  res.json(user);
});

module.exports = router;
```

### Merkezi Hata İşleyici Middleware

Tüm uygulama için merkezi bir hata işleyici oluşturabilirsiniz:

```javascript
// app.js
const express = require("express");
const bodyParser = require("body-parser");
const usersRouter = require("./routes/users");

const app = express();
app.use(bodyParser.json());
app.use("/users", usersRouter);

// Merkezi hata işleyici
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "İç Sunucu Hatası",
  });
});

module.exports = app;
```

### Açıklama

- **`app.use((err, req, res, next) => { ... })`**: Express'te hata işleyici middleware'lerin standart yapısıdır.
- **`err.status`**: Eğer belirlenmişse özel hata kodunu kullanır, yoksa `500` döner.
- **`err.message`**: Hata mesajı olarak döndürülen metin.
- **`console.error(err.stack)`**: Hata detaylarını sunucu konsoluna yazdırır.

### Asenkron Hataların Yönetimi

Asenkron işlemler sırasında oluşan hataları `try/catch` ve `next(error)` kullanarak yönetebilirsiniz:

```javascript
// routes/todos.js
const express = require("express");
const router = express.Router();
const todosService = require("../services/todosService");

router.get("/:id", async (req, res, next) => {
  try {
    const todoId = req.params.id;
    if (isNaN(todoId)) {
      throw new Error("Geçersiz todo ID");
    }
    const todo = await todosService.getById(todoId);
    if (!todo) {
      throw new Error("Todo bulunamadı");
    }
    res.json(todo);
  } catch (error) {
    next(error);
  }
});

module.exports = router;
```

## Hata Yönetimi İçin Ekstra Yöntemler

### Hata Günlükleme (Logging)

Hataları kaydetmek için `winston` veya `morgan` gibi günlükleme kütüphaneleri kullanabilirsiniz:

```javascript
const express = require("express");
const morgan = require("morgan");

const app = express();
app.use(morgan("dev"));
```

### Geçersiz İsteklerin Yönetimi

Yanlış URL'lere yapılan istekleri `404` hatasıyla yakalayabilirsiniz:

```javascript
// app.js
const express = require("express");
const app = express();

app.use((req, res, next) => {
  res.status(404).json({
    success: false,
    message: "Kaynak bulunamadı",
  });
});
```

Bu yöntemlerle Express API'lerinizde etkili bir hata yönetimi sağlayabilirsiniz.


