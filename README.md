# Simple translator application

![Screenshot](https://github.com/quertc/translator-app/blob/master/preview.png)

## Description

Application made with Vue.js 2.0 using [Yandex Translate API](https://yandex.ru/dev/translate/).

### Installing

Download or clone the repository and run:

```cmd
npm i
```

After installing the dependencies, you can use these commands:

#### Compiles and hot-reloads for development

```cmd
npm run serve
```

#### Compiles and minifies for production

```cmd
npm run build
```

#### Lints and fixes files

```cmd
npm run lint
```

_For the application to work correctly, don't forget to create a .env.local file with [Yandex Translate API](https://translate.yandex.ru/developers/keys) secret key. Format:_

```env
VUE_APP_SECRET = yourapikey
```
