# Using Router in Express Framework

In this section, we will discuss the `Router` in the Express.js framework.

![Express Router](Express-Router.webp)

Image source: Dall-E by OpenAI

- [Using Router in Express Framework](#using-router-in-express-framework)
  - [Learning Outcomes](#learning-outcomes)
  - [Router](#router)
  - [Creating a Router](#creating-a-router)
  - [Using Middleware with Routers](#using-middleware-with-routers)
  - [Conclusion](#conclusion)

## Learning Outcomes

By the end of this section, you will be able to:

- Explain what a `Router` is and how it is used.
- Create `Router`s in an Express.js application.
- Use `Router`s for grouping routes.

So far, we have had different routes defined directly in the `app.js` file. However, as the number of routes increases, the content of the file can become very large and difficult to read. To better structure the code and make the `app.js` file more readable, we can use the `express Router`.

## Router

The `Router` is an object in the `Express` framework that allows us to group routes. For example, if we need separate routes for users and for posts, we can place them in separate `Router`s.

Currently, if our `app.js` file has routes defined like this:

```javascript
app.get("/logs", logger, loggerControllers.getLogs);
app.post("/login", authControllers.login);
app.post("/users", usersControllers.createUser);
app.use(isLoggedInMiddleware);
app.get("/users", isAdmin, usersControllers.getUsers);
app.get("/users/:id", usersControllers.getUserById);
app.get("/statuses", statusesControllers.getStatuses);
app.get("/statuses/:id", statusesControllers.getStatusById);
app.get("/subjects", subjectsControllers.getSubjects);
app.get("/subjects/:id", subjectsControllers.getSubjectById);
app.post("/subjects", subjectsControllers.createSubject);
app.get("/homeworks", homeworksControllers.getHomeworks);
app.get("/homeworks/:id", homeworksControllers.getHomeworkById);
app.post("/homeworks", homeworksControllers.createHomework);
```

We see that these routes already form groups according to resources. For example, we have user routes, topic-related routes, and homework-related routes. Now we can move these groups into separate `Router`s.

## Creating a Router

First, create a new file in the corresponding component folder that will contain routes related to that resource. For instance, routes related to subjects could be in a file named `subjectsRoutes.js`. First, import `express` in that file:

```javascript
const express = require("express");
```

Then, we can create a `Router` object:

```javascript
const router = express.Router();
```

Additionally, we should import the corresponding controllers that the routes will use:

```javascript
const subjectsControllers = require("./subjectsControllers");
```

Next, move all the subject-related routes from `app.js` to `subjectsRoutes.js` and rewrite them slightly to use `router` instead of `app`:

```javascript
router.get("/", subjectsControllers.getSubjects);
router.get("/:id", subjectsControllers.getSubjectById);
router.post("/", subjectsControllers.createSubject);
```

Finally, export the `router` and import it into `app.js`:

```javascript
module.exports = router;
```

In the `app.js` file, import the `subjectsRoutes.js` file and use `app.use` method to let Express know that we have such a `Router`:

```javascript
const subjectsRoutes = require("./subjects/subjectsRoutes");

app.use("/subjects", subjectsRoutes);
```

The final `subjectsRoutes.js` file will look like this:

```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");

const router = express.Router();

router.get("/", subjectsControllers.getSubjects);
router.get("/:id", subjectsControllers.getSubjectById);
router.post("/", subjectsControllers.createSubject);

module.exports = router;
```

## Using Middleware with Routers

Using middleware with `Router`s works just like with `app`. For example, if we need to use `isLoggedInMiddleware`, we can do it like this:

```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");
const isLoggedInMiddleware = require("../auth/isLoggedInMiddleware");

const router = express.Router();

router.get("/", isLoggedInMiddleware, subjectsControllers.getSubjects);

module.exports = router;
```

It is also important to remember that when we use `Router`, we cannot use the `app.use` method to apply middleware for all routes. Instead, we need to use the `router.use` method:

```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");
const isLoggedInMiddleware = require("../auth/isLoggedInMiddleware");

const router = express.Router();

router.use(isLoggedInMiddleware);

router.get("/subjects", subjectsControllers.getSubjects);

module.exports = router;
```

Alternatively, we can register the middleware in the `app.js` file before using the corresponding `router`:

```javascript
const subjectsRoutes = require("./subjects/subjectsRoutes");

app.use(isLoggedInMiddleware);
app.use(subjectsRoutes);
```

## Conclusion

`Router`s are very useful when we have many routes and want to group them. They also make our code more readable and better structured. Additionally, we can use middleware in `Router`s just as we do in `app`.

# Express Framework'te Router Kullanımı

Bu bölümde, Express.js framework'ündeki `Router` kavramını ele alacağız.

![Express Router](Express-Router.webp)

Görsel kaynağı: Dall-E by OpenAI

- [Express Framework'te Router Kullanımı](#express-frameworkte-router-kullanımı)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [Router](#router)
  - [Router Oluşturma](#router-oluşturma)
  - [Middleware ile Router Kullanımı](#middleware-ile-router-kullanımı)
  - [Sonuç](#sonuç)

## Öğrenme Çıktıları

Bu bölümü tamamladıktan sonra şunları yapabileceksiniz:

- `Router`'ın ne olduğunu ve nasıl kullanıldığını açıklayabilirsiniz.
- Express.js uygulamasında `Router` oluşturabilirsiniz.
- `Router`ları kullanarak rotaları gruplandırabilirsiniz.

Şu ana kadar farklı rotaları doğrudan `app.js` dosyasında tanımladık. Ancak rota sayısı arttıkça, dosyanın içeriği çok büyük ve okunamaz hale gelebilir. Kodu daha iyi yapılandırmak ve `app.js` dosyasını daha okunabilir hale getirmek için `express Router` kullanabiliriz.

## Router

`Router`, Express framework'ünde rotaları gruplamamıza olanak tanıyan bir nesnedir. Örneğin, kullanıcılar ve gönderiler için ayrı rotalara ihtiyacımız varsa, bunları farklı `Router`lara yerleştirebiliriz.

Şu anda `app.js` dosyamız şu şekilde tanımlanmış rotalara sahip olabilir:

```javascript
app.get("/logs", logger, loggerControllers.getLogs);
app.post("/login", authControllers.login);
app.post("/users", usersControllers.createUser);
app.use(isLoggedInMiddleware);
app.get("/users", isAdmin, usersControllers.getUsers);
app.get("/users/:id", usersControllers.getUserById);
app.get("/statuses", statusesControllers.getStatuses);
app.get("/statuses/:id", statusesControllers.getStatusById);
app.get("/subjects", subjectsControllers.getSubjects);
app.get("/subjects/:id", subjectsControllers.getSubjectById);
app.post("/subjects", subjectsControllers.createSubject);
app.get("/homeworks", homeworksControllers.getHomeworks);
app.get("/homeworks/:id", homeworksControllers.getHomeworkById);
app.post("/homeworks", homeworksControllers.createHomework);

```

Bu rotaların zaten belirli kaynaklara göre gruplandığını görebiliriz. Örneğin, kullanıcı rotaları, konu ile ilgili rotalar ve ödev ile ilgili rotalar var. Şimdi bu grupları ayrı `Routerlara` taşıyabiliriz.

## Router Oluşturma
```javascript
Öncelikle, belirli bir kaynağa ait rotaları içeren yeni bir dosya oluşturun. Örneğin, konu ile ilgili rotalar `subjectsRoutes.js` adlı bir dosyada yer alabilir. Bu dosyada önce `expressi` içe aktarmalıyız:
const express = require("express");
```
Daha sonra, bir `Router` nesnesi oluşturabiliriz:

```javascript
const router = express.Router();
```
Ayrıca, rotaların kullanacağı ilgili denetleyicileri (controllers) içe aktarmalıyız:
```javascript
const subjectsControllers = require("./subjectsControllers");
```
Şimdi, `app.js` içindeki konu ile ilgili tüm rotaları `subjectsRoutes.js` içine taşıyıp, `app` yerine `router` kullanarak tekrar yazalım:
```javascript
router.get("/", subjectsControllers.getSubjects);
router.get("/:id", subjectsControllers.getSubjectById);
router.post("/", subjectsControllers.createSubject);
```
Son olarak, `routerı` dışa aktarıp app.js içine aktarmalıyız:
```javascript
module.exports = router;
```
`app.js` dosyasında, `subjectsRoutes.js` dosyasını içe aktarın ve  `app.use ` metodunu kullanarak Express'e bu  `Routerın ` var olduğunu bildirin:
```javascript
const subjectsRoutes = require("./subjects/subjectsRoutes");

app.use("/subjects", subjectsRoutes);
```

Son haliyle `subjectsRoutes.js` şu şekilde görünecektir:
```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");

const router = express.Router();

router.get("/", subjectsControllers.getSubjects);
router.get("/:id", subjectsControllers.getSubjectById);
router.post("/", subjectsControllers.createSubject);

module.exports = router;
```
## Middleware ile Router Kullanımı
`Routerlar` ile middleware kullanımı, `app` ile kullanıma oldukça benzerdir. Örneğin, `isLoggedInMiddleware` kullanmamız gerekirse bunu şu şekilde yapabiliriz:
```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");
const isLoggedInMiddleware = require("../auth/isLoggedInMiddleware");

const router = express.Router();

router.get("/", isLoggedInMiddleware, subjectsControllers.getSubjects);

module.exports = router;
```

Ayrıca, `Router` kullanırken tüm rotalara middleware uygulamak için `app.use` yerine `router.use` kullanmalıyız:
```javascript
const express = require("express");
const subjectsControllers = require("./subjectsControllers");
const isLoggedInMiddleware = require("../auth/isLoggedInMiddleware");

const router = express.Router();

router.use(isLoggedInMiddleware);

router.get("/subjects", subjectsControllers.getSubjects);

module.exports = router;
```

Alternatif olarak, middleware'i `app.js` içinde, ilgili `Routerı` kullanmadan önce kaydedebiliriz:

```javascript
const subjectsRoutes = require("./subjects/subjectsRoutes");

app.use(isLoggedInMiddleware);
app.use(subjectsRoutes);
```

## Sonuç
`Routerlar`, birçok rotamız olduğunda ve bunları gruplamak istediğimizde oldukça kullanışlıdır. Kodumuzu daha okunabilir ve daha iyi yapılandırılmış hale getirirler. Ayrıca, middleware'i `Routerlar` içinde `app`içindeki gibi kullanabiliriz.

