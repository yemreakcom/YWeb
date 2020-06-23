# 🔶 JQuery

## JQuery Kurulumu <a id="jquery-kurulumu"></a>

### Tarayıcı Consoluna Kurulum <a id="tarayici-consoluna-kurulum"></a>

```text
async function loadScript(url) {  let response = await fetch(url);  let script = await response.text();  eval(script);}​let scriptUrl = 'https://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js'loadScript(scriptUrl);
```

## Temel Giriş <a id="temel-giris"></a>

* `$ veya $$` karakteri `document.querySelectorAll()` komutuna karşılık gelir
* Sayfadaki JQuery kontrolü için _console_'a `jQuery` yazıldığında tepki vermesi gerekir
* Jquery versiyonunu `$().jquery` komutuyla öğrenebilirsin.

> Ek bilgi için [buraya](https://stackoverflow.com/a/14309038/9770490) bakabilirsin.

## HTML Seçme İşlemleri <a id="html-secme-islemleri"></a>

Tüm seçme işlemleri `$(<işlem>)` ve `$$(<işlem>)` komutu ile yapılır.

* Ana kaynak için [buraya](https://www.w3schools.com/jquery/jquery_selectors.asp) bakabilirsin
* Online olarak test etmek için [buraya](https://www.w3schools.com/jquery/trysel.asp) bakabilirsin

> Alttaki işlemler _Chrome DOM_'unda gömülü gelen işlemlerdir, ek işlemler için sitenin _jQuery_'i içermesi lazımdır

## Temel Metodlar <a id="temel-metodlar"></a>

## Harici Bağlantılar <a id="harici-baglantilar"></a>

* 
