# Simple translator app
![Screenshot](https://github.com/quertc/translator-app/blob/master/preview.PNG)

## Description
This app is made on Vue.js using the Vue CLI 3 development tool.  
**The app works with the help of [Yandex Translate API](https://tech.yandex.ru/translate/).**

### Installing
Download or clone the repository and run
```
npm install
```

After installing the dependencies, you can use these commands:

#### Compiles and hot-reloads for development
```
npm run serve
```

#### Compiles and minifies for production
```
npm run build
```

_To make the app work correctly, you need:_  
Create .env file with [Yandex Translate API](https://tech.yandex.ru/translate/) secret key.  
Format:
```
VUE_APP_SECRET = yourapikey
```
