# 💜 Heroku

## Heroku Önemli Notlar <a id="heroku-oenemli-notlar"></a>

### Heroku varsayılan atamaları <a id="heroku-varsayilan-atamalari"></a>

```text
NPM_CONFIG_LOGLEVEL=errorNODE_ENV=productionNODE_MODULES_CACHE=trueNODE_VERBOSE=false
```

> Bu atamalara kod içerisinden `process.env.<üsttekilerden biri>` şeklinde erişilebilir.
>
> _console.log\(process.env.NODE\_ENV\) gibi_

### Heroku Script Çalıştırma <a id="heroku-script-calistirma"></a>

* Heroku aldığı node.js uygulamasındaki **start scriptini** çalıştırır. Yani `npm run start` komutunu işler
* Bu sebeple **package.json** dosyası olmak zorunda ve **start scriptini** içermek zorundadır
* Artık heroku yükleme işleminin hemen ardından `build` scriptini çalıştırmaya başlayacak
  * Tarihi ve detaylı bilgi için [buraya](https://devcenter.heroku.com/changelog-items/1557) tıklayabilirsin

Örnek package.json dosyası

```text
{  "name": "temp",  "version": "1.0.0",  "description": "",  "main": "index.js",  "directories": {    "lib": "lib"  },  "scripts": {    "start": "node index.js",    "test": "echo \"Error: no test specified\" && exit 1"  },  "author": "",  "license": "ISC"}
```

### Heroku port ayarı <a id="heroku-port-ayari"></a>

```text
port = process.env.PORT || 5000
```

> Heroku kendiliğinden port atama işlemi yapmaktadır. Bu sebeple dinlediğimiz portu **process.env.PORT** yapmak zorundayız.

## Heroku Komutları <a id="heroku-komutlari"></a>

### Bu komutların çalışması için heroku-cli'nin yüklü olması lazım <a id="bu-komutlarin-calismasi-icin-heroku-clinin-yueklue-olmasi-lazim"></a>

> Npm üzerinden heroku yükleme işlemi

### Heroku'ya giriş yapma <a id="herokuya-giris-yapma"></a>

> Email ve şifre istenecektir. Siteye kayıt olduğunuz bilgileri girin

### Depo \(repository\) kopyalama işlemi <a id="depo-repository-kopyalama-islemi"></a>

```text
heroku git:clone -a [herokudaki uygulama adı] [kopyalanacağı dizin yolu]cd [kopyalanacağı dizin yolu]
```

* herokudaki uygulama adı: mytempsite
* kopyalanacağı dizin yolu: C:\Desktop\Temp

> Heroku'da bulunan uygulamayı istediğimiz dizinin içine kopyalıyoruz. Sonrasında kopyalama işleminin olduğu dizine giriyoruz.

### Değişiklikleri karşıya yükleme <a id="degisiklikleri-karsiya-yuekleme"></a>

```text
git add .git commit -am "Mesaj"git push heroku master
```

> Değişkliklikler heroku uygulmamıza eklenecektir.

### Uygulamayı başlatma <a id="uygulamayi-baslatma"></a>

### Hata raporlarını görüntüleme <a id="hata-raporlarini-goeruentueleme"></a>

```text
heroku logs --tail -a [uygulama adı]
```

* uygulama adı: mytempsite \(herokudaki uygulama adımız\)

> Uygulmamız çalışırken yapılan işlemleri raporlar

## Heroku Ek Ayarlar <a id="heroku-ek-ayarlar"></a>

Babel gibi ek uygulamalar kullanıyorsanız bu kısım sizin için oldukça önemlidir.

> **Not**: Tüm es5 olmayan dosyaları _babel_ ile es5'e çevirip herokuya yüklemek performans açısından daha sağlıklıdır.

### Heroku üretim modunu kapatma <a id="heroku-ueretim-modunu-kapatma"></a>

```text
heroku config:set NPM_CONFIG_PRODUCTION=false
```

> Üretim modunu kapatır. Bu sayede heroku **package.json** dosyasındaki **dev-dependencies** içindekilerini indirir. Ardından tekrar bu mod isteğe bağlı açılabilir

### Heroku Bash Erişimi <a id="heroku-bash-erisimi"></a>

> Bu komut ile terminale erişmiş oluruz. Bu sayede npm komutlarımızı çalıştırabiliriz.

> Yukarıdaki komut ile gerekli olan uygulamaları \(dev-dependencies\) kendimiz indirebiliriz.

