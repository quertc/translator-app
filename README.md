# Simple translator app

![Screenshot](https://github.com/quertc/translator-app/blob/master/preview.png)

## Description

This app is made on Vue.js 2.  
**The app works using the [Yandex Translate API](https://yandex.ru/dev/translate/).**

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

### Lints and fixes files

```cmd
npm run lint
```

_For the app to work correctly, don't forget to create a .env.local file with the [Yandex Translate API](https://translate.yandex.ru/developers/keys) secret key. Format:_

```env
VUE_APP_SECRET = yourapikey
```
