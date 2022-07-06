# 🧱 Nodejs Temelleri

## Paket Yönetimi <a href="#paket-yoenetimi" id="paket-yoenetimi"></a>

Paket kurulumları `npm` komutu yardımıyla yapılır.

### Paketler ve Açıklamaları <a href="#paketler-ve-aciklamalari" id="paketler-ve-aciklamalari"></a>

Paketler NPM ile `npm install <paket>` komutu yardımıyla indirilir.

* **Normal kurulum:** Ön ek gerektirmez
* **Global kurulum:** `-g` ön eki ile yapılır
* **Dev kurulum:** `--save-dev` son eki ile yapılır

#### Normal Paketler <a href="#normal-paketler" id="normal-paketler"></a>

#### Geliştirici Paketleri <a href="#gelistirici-paketleri" id="gelistirici-paketleri"></a>

### NPM Kullanım Yapısı <a href="#npm-kullanim-yapisi" id="npm-kullanim-yapisi"></a>

```
npm <operasyon> <varsa_ön_ek> <paket> <varsa_son_ek>
```

* `<operasyon>` install, remove ...
* `<varsa_ön_ek>` -g ...
* `<paket>` nodemon, colors, express ...
* `<varsa_son_ek>` --save-dev ...

### Paket Kurulum Örnekleri <a href="#paket-kurulum-oernekleri" id="paket-kurulum-oernekleri"></a>

```
npm install nodemon --save-devnpm install -g babel-clinpm install colors
```

### Nodejs Dependency Prefixes <a href="#nodejs-dependency-prefixes" id="nodejs-dependency-prefixes"></a>

`<prefix><dependency_version>`

* \~ This version
* ^ latest version

## Ortam Değişkenleri <a href="#ortam-degiskenleri" id="ortam-degiskenleri"></a>

Ortam ön ayarları scriptler çalıştırılmadan önce girilen komutlardır.

> ​[Heroku](https://www.heroku.com/nodejs) gibi sitelerde üretim modu ön eki uygulama çalıştırılmadan uygulanır.

### Ortam Değişkenleri Açıklamaları <a href="#ortam-degiskenleri-aciklamalari" id="ortam-degiskenleri-aciklamalari"></a>

Kod içerisinde `process.env.<değişken>` şeklinde erişilir.

* `<dosya_ismi>` örnekleri:
  * `*` ile her şeyi
  * `lib\*` ile lib'le başlayan herşeyi
  * `index` ile index.js dosyasını
* `<özel_mod>` örnekleri:
  * `stagging` Normal iskelet
  * `production` Üretim iskeleti
* `<port>` örnekleri:
  * `3000` Normal port
  * `5000` Üretim portu

> Değişken örnekleri keyfidir.

### Ortam Değişkenleri Kullanımı <a href="#ortam-degiskenleri-kullanimi" id="ortam-degiskenleri-kullanimi"></a>

```
set NODE_ENV=production & set DEBUG=* & npm run-script dev
```

### Herokunun Kullandığı Ortam Değişkenleri <a href="#herokunun-kullandigi-ortam-degiskenleri" id="herokunun-kullandigi-ortam-degiskenleri"></a>

Ücretsiz nodejs sunucularından biri olan [heroku](https://www.heroku.com/nodejs)'nun hali hazırda sunduğu ortam değişkenler:

## Nodejs ES6 Yapısını Kullanma <a href="#nodejs-es6-yapisini-kullanma" id="nodejs-es6-yapisini-kullanma"></a>

Nodejs'de ES6 yapısı `babel` yardımcısı ile kullanabilinmektedir.

> Tarayıcı es5 yapısını kullanmaktadır.

### Babel Paketleri <a href="#babel-paketleri" id="babel-paketleri"></a>

* **Global kurulum:** `-g` ön eki ile yapılır
* **Dev kurulum:** `--save-dev` son eki ile yapılır

### Babel Paketlerinin Kurulumu <a href="#babel-paketlerinin-kurulumu" id="babel-paketlerinin-kurulumu"></a>

Global olarak babel consol komutlarını ve işleyicisini ekler.

```
npm install -g babel-clinpm install babel-register babel-preset-env --save-dev
```

> `babel-cli` global olarak kurulmazsa babel komutları her yerde tanınmaz.

### Babel Yapılandırması <a href="#babel-yapilandirmasi" id="babel-yapilandirmasi"></a>

> Bu adım ve sonrasındaki işlemler projenin (`index.js`) dizininde yapılmalıdır

#### Babel Derleyici Yapılandırmasını Oluşturma <a href="#babel-derleyici-yapilandirmasini-olusturma" id="babel-derleyici-yapilandirmasini-olusturma"></a>

Babelrc dosyası belli ayarlarla oluşturma

```
@echo {"presets":[["env",{"targets":{"edge":"17","firefox":"60","chrome":"67","safari":"11.1","node":"current"}}]]} > .babelrc
```

> `targets` isteğe bağlıdır. Hedeflenen tarayıcıları gösterir.

#### Babel Derleme Araçlarını Yapılandırma <a href="#babel-derleme-araclarini-yapilandirma" id="babel-derleme-araclarini-yapilandirma"></a>

Tools dizini oluşturup, içindeki dosyaya derleme parametrelerini yazıyoruz.

```
mkdir tools & @echo require("babel-register") > tools/dev && @echo require("./../index.js") >> tools/dev
```

> Not: Bu kısımdaki `tools/dev` ile diğer adımdaki işlemler yapılmaktadır

### Packege.json Oluşturma <a href="#packege-json-olusturma" id="packege-json-olusturma"></a>

> Bu işlem oluşturulması istenen dizinde yapılmalıdır.

### Package.json Scriptlerini Oluşturma <a href="#package-json-scriptlerini-olusturma" id="package-json-scriptlerini-olusturma"></a>

`package.json` dosyası içerisindeki script kısmında alttakiler eklenir.

```
"scripts": {  "test": "node test",  "start": "node dist/index.js",  "dev": "set DEBUG=* & node tools/dev",  "build": "mkdir dist & babel *.js lib/**/*.js -s -d dist & xcopy public dist\\public /s /i /e /y",  "build:db": "mkdir dist & babel *.js lib/**/*.js -s -d dist & xcopy public dist\\public /s /i /e /y & xcopy database dist\\database /s /i /e /y",  "build:start": "npm run-script build & npm run-script start",  "clean": "xcopy dist\\database database /s /i /e /y & rd /s /q dist",  "clean:all": "rd /s /q dist",  "rebuild": "npm run-script clean & npm run-script build",  "rebuild:db": "npm run-script clean & npm run-script build:db"}
```

#### Build Script Yapısı <a href="#build-script-yapisi" id="build-script-yapisi"></a>

* `mkdir dist` Dist adlı klasör oluşturulur
* `babel [her bir js dosyasının yolu] -s -d dist` Javasciprt dosyaları es5 tipinde düzenlenip dist içine atılır
* `xcopy [klasör] dist\\[klasör] /s /i /e /y` Dinamik veri tutan klasörler varsa dist içine kopyalanır

### Package.json için Script Açıklamaları <a href="#package-json-icin-script-aciklamalari" id="package-json-icin-script-aciklamalari"></a>

### Programı Derleme İşlemi <a href="#programi-derleme-islemi" id="programi-derleme-islemi"></a>

Package.json dosyasındaki scriptleri çalıştırma

* `[script]` scripts içindeki isimler; start, dev, build

## VsCode için Debug Ayarları <a href="#vscode-icin-debug-ayarlari" id="vscode-icin-debug-ayarlari"></a>

Açıklama [videosu](https://www.youtube.com/watch?v=yFtU6\_UaOtA) ve [metni](https://github.com/yedhrab/YWiki/tree/169abadfd1b8862c004399268f6ca1f9f9359d61/1%20-%20Programlama%20Notlar%C4%B1/5%20-%20Web%20Programlama/Uygulama%20Notlar%C4%B1/VsCode.md#nodejs-i%C3%A7in-debug-ayar%C4%B1) için üzerlerine tıklayabilirsin.

````
## Kod Bankası​### Fonksiyon İsmi, Satırı ve Dosya Adı Alma​```jsexport function _getCallerInfo() {  const err = new Error();  let index = 3;  let line = err.stack.split("\n")[index];  let functionName = line.split(" at ")[1].split(" ")[0];​  while (functionName.includes(`C:/`)) {    index++;    line = err.stack.split("\n")[index];    functionName = line.split(" at ")[1].split(" ")[0];  }​  let callerInfo = line.split(`${projectName}/`);  callerInfo = callerInfo[callerInfo.length - 1];​  const filename = callerInfo.split(".")[0];  const lineInfos = callerInfo.replace(filename + ".js:", "").replace(")", "");  return `${filename}:${functionName}:${lineInfos}`; }
````

## Harici Bağlantılar <a href="#harici-baglantilar" id="harici-baglantilar"></a>

*
*
*
*
*
*
*
