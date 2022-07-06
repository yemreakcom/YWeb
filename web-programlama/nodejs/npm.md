# 🥬 NPM

## CLI Uygulaması Yapma <a href="#cli-uygulamasi-yapma" id="cli-uygulamasi-yapma"></a>

### CLI Args (Komut Argümanları) <a href="#cli-args-komut-arguemanlari" id="cli-args-komut-arguemanlari"></a>

Komut argümanları `node index.js arg1 arg2 ...` ile verilir.

* `process.argv` ile erişilir
* `process.argv[0]` Node'un yolu
* `process.argv[1]` Script'in yolu
* Geri kalanları kullanıcının yazıdığı parametrelerdir
* `process.argv.slice(2)` ile kullanıcı parametrelerine erişilir

#### Yargs ile Args Yönetme <a href="#yargs-ile-args-yoenetme" id="yargs-ile-args-yoenetme"></a>

Nodejs sitesindenki açıklamaya [buradan](https://nodejs.org/en/knowledge/command-line/how-to-parse-command-line-arguments/) erişebilirsin.

#### Minimist ile Args Yönetme <a href="#minimist-ile-args-yoenetme" id="minimist-ile-args-yoenetme"></a>

* İlk olarak projeye dahil edilmeli `npm install -save minimist`

```
minimist(process.argv.slice(2))
```

> Ek bağlantılar:
>
> *
> *

### Bin Klasörü <a href="#bin-klasoerue" id="bin-klasoerue"></a>

Özel komutların tanımlanmasını sağlar.

* `<komut1>` Örnek komut ismidir
  * Örn: `yemreak`

**Dizin yapısı:**

```
+ bin  - <komut1>  - <komut2>- index.js- README.md
```

**Dosya içeriği:**

```
#!/usr/bin/env node require('../')() 
```

**Package json'a eklenecek ayar:**

Bu ayar ile bin dosyamız indirilip gerekli yere konumlandırılacaktır.

```
"bin": {    "<komut1>": "bin/<komut1>",    "<komut2>": "bin/<komut2>"},
```

## Paket Yapımı Örnekleri <a href="#paket-yapimi-oernekleri" id="paket-yapimi-oernekleri"></a>

*

## Paketleri Online Test Etme <a href="#paketleri-online-test-etme" id="paketleri-online-test-etme"></a>

* Paketleri indirmeden önce [buradan](https://npm.runkit.com/) test edebilirsin.

## Paket Oluşturma ve Yayınlama <a href="#paket-olusturma-ve-yayinlama" id="paket-olusturma-ve-yayinlama"></a>

* İlk olarak npm hesabını [buradan](https://www.npmjs.com/signup) oluşturun
* `npm adduser` ile kullanıcı oluşturun
  * `npm login` komutunu da kullana bilirsiniz
  * Oluşturulan token bilgisine [buradan](https://www.npmjs.com/settings/yedhrab/tokens) bakabilirsiniz
* `npm version v1.0.0` ile paketin sürümünü tanımlayın
* `npm publish` ile [npm sitesine](https://www.npmjs.com/) yükleyebilirsiniz

### Paket için Package.json Ayarları <a href="#paket-icin-package-json-ayarlari" id="paket-icin-package-json-ayarlari"></a>

**Node sürümü ayarı:**

```
"engines": {    "node": ">=8"}
```

**Global yükleme önerisi:**

**Tam Örnek:**

```
{  "name": "ytools",  "version": "1.0.0",  "description": "Faydalı olacak araçların, toparlanmış hali",  "main": "index.js",  "scripts": {    "test": "echo \"Error: no test specified\" && exit 1"  },  "engines": {    "node": ">=8"  },  "preferGlobal": true,  "bin": {    "ytools": "bin/ytools"  },  "keywords": [    "yemreak",    "tools",  ],  "repository": {    "type": "git",    "url": "git+https://github.com/yedhrab/YTools.git"  },  "keywords": [    "tools"  ],  "author": "yedhrab",  "license": "MIT",  "bugs": {    "url": "https://github.com/yedhrab/YTools/issues"  },  "homepage": "https://github.com/yedhrab/YTools#readme",  "dependencies": {    "yargs": "^13.2.4"  }}
```

> Video örneğine [buradan](https://www.google.com/search?q=make+npm+module\&oq=make+npm+module\&aqs=chrome.0.0l6.2476j0j7\&sourceid=chrome\&ie=UTF-8#kpvalbx=1) erişebilirsin.
