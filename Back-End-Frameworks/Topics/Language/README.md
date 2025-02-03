# Language Selection in Express API

To implement language selection in an Express API, you can use internationalization (i18n) frameworks like `i18next`, `i18next-express-middleware`, and `i18next-http-backend`. These tools allow managing multilingual translations and setting the language based on client preferences.

---

## Install Required Packages

Install `i18next`, `i18next-express-middleware`, and `i18next-http-backend`:

```bash
npm install i18next i18next-express-middleware i18next-http-backend
```

## Configure i18next

Create an `i18next.js` file containing the i18next configuration:

```javascript
// i18next.js
const i18n = require('i18next');
const Backend = require('i18next-http-backend');
const middleware = require('i18next-express-middleware');

i18n
  .use(Backend)
  .use(middleware.LanguageDetector)
  .init({
    fallbackLng: 'en', // default language
    preload: ['en', 'et'], // preload languages
    backend: {
      loadPath: __dirname + '/locales/{{lng}}/{{ns}}.json'
    }
  });

module.exports = i18n;

```

## Create Translation Files

Create a `locales` folder and subfolders for each language, such as `en` and `et`. Inside each folder, create translation files like `translation.json`:

### `locales/en/translation.json`

```json
{
  "welcome": "Welcome",
  "message": "This is an internationalized message."
}
```

### `locales/et/translation.json`

```json
{
  "welcome": "Tere tulemast",
  "message": "See on rahvusvaheline sõnum."
}
```

## Add i18next Middleware to Express API

Configure Express API to use i18next:

```javascript
// server.js
const express = require('express');
const i18next = require('./i18next');
const middleware = require('i18next-express-middleware');

const app = express();

app.use(middleware.handle(i18next));

// Bodyparser Middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Example route with translation
app.get('/api', (req, res) => {
  const welcomeMessage = req.t('welcome');
  const message = req.t('message');
  res.json({ welcomeMessage, message });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server started on port ${PORT}`));

```

## Use Language Selection on the Client

You can set the language on the client side using the `Accept-Language` HTTP header or a URL parameter.

### Example: Using HTTP Header

Include the `Accept-Language` header in the API request:

```sh
curl -H "Accept-Language: et" http://localhost:5000/api
```

This should return a response in Estonian:

```json
{
  "welcomeMessage": "Tere tulemast",
  "message": "See on rahvusvaheline sõnum."
}
```

### Example: Using URL Parameter

To use a URL parameter for language selection, configure i18next middleware to detect the language from the query string:

```javascript
// i18next.js (add lookupQuery)
i18n
  .use(Backend)
  .use(middleware.LanguageDetector)
  .init({
    fallbackLng: 'en',
    preload: ['en', 'et'],
    backend: {
      loadPath: __dirname + '/locales/{{lng}}/{{ns}}.json'
    },
    detection: {
      order: ['querystring', 'cookie', 'header'],
      caches: ['cookie'],
      lookupQuerystring: 'lng'
    }
  });

module.exports = i18n;

```

Now, set the language using the URL parameter:

```sh
curl http://localhost:5000/api?lng=et
```

This should also return a response in Estonian.

## Summary

In this example, we used i18next and i18next-express-middleware to add internationalization support to an Express API. We configured language selection using the Accept-Language header and URL parameters. This enables delivering multilingual responses based on user preferences.
