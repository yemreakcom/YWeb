---
description: Wordpress kullanımı sırasında oluşan sorunlara çözümlerim
---

# 🐞 Wordpress Hata Notları

## ❌ Unable to create directory wp-content/uploads/2019/04. Is its parent directory writable by the server

Bu hata dizin ve dosya yetki sorunlarından kaynaklanır. [🚧 Wordpress Dosyalarının İndirilmesi ve Hazırlanması](localhostta-wordpress.md#wordpress-dosyalarinin-indirilmesi-ve-hazirlanmasi) aşamasındaki izinleri düzgün tamamladığınızdan emin olun.

* Wordpress'in kullanıcı adı `deamon` olarak geçer
* Her dizinin 755 yetkisine \(Create & Delete\)
* Her dosyanın 644 yetkisine \(Read & Write\)

sahip olması gerekir

> Linux için `chmod 755 <dizin_yolu>` \| `chmod 644 <dosya_yolu>` komutunu kullanabilirsin

## ❌ You won’t be able to install new themes from here yet since your install requires SFTP credentials

Çözüm için `wp-config.php` dosyanıza `define('FS_METHOD', 'direct');` satırını ekleyin.

> `wp-config.php` dosyası XAMPP'ın kurulu olduğu dizindeki `htdocs/wordpress/` yolundadır.

