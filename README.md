# Simple translator app
![Screenshot](https://github.com/quertc/translator-app/blob/master/preview.PNG)

### Description and installation
This app is made on Vue.js using the Vue CLI 3 development tool.  
**The app works with the help of [Yandex Translate API](https://tech.yandex.ru/translate/)**

1. Download or clone the repository

	```
	git clone https://github.com/quertc/translator-app.git
	cd translator-app
	```
2. Install Dependencies

	```
	npm i
	```

After these steps, you can use these commands:

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

.

_Do not forget that the application worked correctly, you need:_  
Create .env file with [Yandex Translate API](https://tech.yandex.ru/translate/) special key.  
Format:
```
VUE_APP_SECRET = yourapikey
```