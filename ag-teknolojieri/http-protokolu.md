---
description: 'HTTP protokolü nedir, nasıl kullanılır'
---

# 💌 HTTP Protokolü

## 💎 HTTP İstek Türleri

| 👮‍♂️ Get | 👨‍💼 Post |
| :--- | :--- |
| Sadece veri **almak** için kullanılır, verileri değiştiremez | Sunucudaki verileri **değiştirmek** için kullanılır \(GET kullanamazsın\) |
| Ön belleğe alınabilir | Ön belleğe alınamaz |
| Tarayıcının geçmişinde saklanabilir | Tarayıcı geçmişinde saklanmaz |
| Yer imlerine kaydedilebilir | Yer imlerine kaydedilemez |
| Hassas veriler ile uğraşılırken kullanılmamalıdır | - |
| Uzunluk sınırlandırması vardır | Veri uzunluğu sınırlaması yoktur |

### 👮‍♂️ Get Request

```markup
/test/demo_form.php?name1=value1&name2=value2 <!-- URL örneği -->
```

### 🧱 Head Request

* Get request yapısına alttakiler hariç benzer
* Sonuç bilgisine `body` içeriği olmaz
* İlk gelen verileri alır. \(Users ile istek atılırsa sadece user alır, hepsini almaz\)
* Yüksek boyutlu veriler için tercih edilen bir yapıdır

### 👨‍⚖️ Post Request

```markup
POST /test/demo_form.php HTTP/1.1
Host: w3schools.com
name1=value1&name2=value2
```

### 👩‍⚖️ Put Request

* Post request yapısına alttakiler hariç benzer
* Tekrarlı kullanımında aynı sonuçları döndürür

{% hint style="warning" %}
📢 POST request'in tekrarlı kullanılmasının yan etkileri vardır.
{% endhint %}

## 🆚 Get vs Post Detaylı

| Case | GET | POST |
| :--- | :--- | :--- |
| BACK button/Reload | Harmless | Data will be re-submitted \(the browser should alert the user that the data are about to be re-submitted\) |
| Bookmarked | Can be bookmarked | Cannot be bookmarked |
| Cached | Can be cached | Not cached |
| Encoding type | application/x-www-form-urlencoded | application/x-www-form-urlencoded or multipart/form-data. Use multipart encoding for binary data |
| History | Parameters remain in browser history | Parameters are not saved in browser history |
| Restrictions on data length | Yes, when sending data, the GET method adds the data to the URL; and the length of a URL is limited \(maximum URL length is 2048 characters\) | No restrictions |
| Restrictions on data type | Only ASCII characters allowed | No restrictions. Binary data is also allowed |
| Security | GET is less secure compared to POST because data sent is part of the URL  Never use GET when sending passwords or other sensitive information! | POST is a little safer than GET because the parameters are not stored in browser history or in web server logs |
| Visibility | Data is visible to everyone in the URL | Data is not displayed in the URL |

## 🌎 Online HTTP İsteği Atma

* **POST / PUT** metotları için `Content` alanına **JSON** verisi yazılır
* **GET / HEAD** metotları için `URL` alnına **query** eklenir

{% embed url="https://reqbin.com/" %}

## 🔗 Faydalı Bağlantılar

* [🧱 HTTP Request Methods](https://www.w3schools.com/tags/ref_httpmethods.asp)
* ❔ [If HTTP is Hyper Text Transfer Protocol, how can we upload documents and images? \[closed\]](https://stackoverflow.com/a/15422046)

