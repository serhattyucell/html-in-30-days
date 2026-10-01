# 11. Gün — Görseller (Images)

Bu gün, bir resim dosyasını sayfaya yerleştirir. 10. güne kadar sayfada yalnızca yazı vardı. Görsel, yazının yerine geçen bir süstür ya da yazının anlattığı yerin fotoğrafıdır. HTML, fotoğrafın kendisini içine saklamaz. Fotoğraf ayrı bir dosyadır. Sayfa, o dosyanın yolunu yazar.

## Sayfa, resmi yolundan çağırır

`<img>` etiketi, `src` özelliğindeki dosyayı sayfaya getirir. `alt` özelliği, resim görünmezse onun yerinde duracak metni taşır.

HTML dosyasıyla aynı klasöre `van-golu.jpg` adlı bir fotoğraf konur. Belge şöyle yazılır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Van Gölü</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Gölün kıyısı aşağıdaki fotoğraftadır.</p>
    <img src="van-golu.jpg" alt="Van Gölü kıyısı" />
    <p>Fotoğrafın altında not devam eder.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” başlığı ve bir paragraf vardır. Fotoğraf dosyası klasördeyse paragrafın altında gölün fotoğrafı görünür. Fotoğraf kendi genişliğince durur. Çerçevesi yoktur. Altındaki “Fotoğrafın altında not devam eder.” cümlesi resmin bittiği yerden sonra gelir. `alt` metni, resim görünürken ekranda yazı olarak durmaz.

Dosya klasörde yoksa ya da adı `Van-Golu.jpg` diye farklıysa resmin yerinde kırık bir görsel simgesi belirir. Simgenin yanında veya altında “Van Gölü kıyısı” yazısı okunur. Sayfanın geri kalanı, başlık ve iki paragraf, yerinde kalır. Tek eksik dosya, belgenin tamamını bozmaz.

`<img>` kapanış etiketi almaz. İçine başka etiket konmaz. Yazı, resmin içine değil, ondan önce ve sonra konan paragraflara yazılır. Resmin üzerine başlık bindirmek ileride CSS konusudur.

## Yanlış yol, görünen alt yazı

`src` bir dosya adıdır. Bağlantıdaki `href` gibi, dosya başka klasördeyse yol yazılır. Aynı klasördeki dosya için yalnızca ad yeter.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Eksik görsel</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <img src="saat-kulesi.jpg" alt="İzmir Saat Kulesi, Konak meydanında" />
  </body>
</html>
```

Tarayıcıda görünen:
`saat-kulesi.jpg` henüz yoksa “İzmir” başlığının altında kırık görsel simgesi ve “İzmir Saat Kulesi, Konak meydanında” cümlesi vardır. Fotoğraf klasöre bu adla konup sayfa yenilenince simge ve cümle kaybolur. Yerlerinde kule fotoğrafı durur. Cümle, resmi göremeyen bir okur için bırakılmıştır. Ekran okuyucu da bu cümleyi okur. Ayrıntı 23. günde erişilebilirlik başlığı altında toplanır. Bugün, resmin görünmediği anda sayfanın dilsiz kalmaması gerekir.

`alt`, “resim”, “fotoğraf” veya dosya adı ile doldurulmaz. “saat-kulesi.jpg” yazmak, göremeyen kişiye bir dosya adı okur. “İzmir Saat Kulesi, Konak meydanında” yazmak, fotoğrafın ne gösterdiğini söyler.

Süs için konmuş ve bir bilgi taşımayan çizgide `alt=""` boş bırakılır. Boş değer, “bu görselin okunacak bir karşılığı yok” demektir. Bilgi taşıyan her fotoğrafta metin dolu olur.

## Ölçü, yer ayırmak içindir

`width` ve `height` özellikleri, resmin kaç piksel yer tutacağını söyler. Bu, rengi veya çerçevesi değiştirmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ölçülü görsel</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <img src="trabzon-kiyi.jpg" alt="Trabzon’da Karadeniz kıyısı" width="320" height="200" />
    <p>Kıyı fotoğrafı bu yüksekliğe sığdırıldı.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf varsa 320 piksel genişliğinde ve 200 piksel yüksekliğinde bir dikdörtgen olarak durur. Pencere çok dar değilse paragraf onun altında başlar. Fotoğraf yoksa kırık simge ile “Trabzon’da Karadeniz kıyısı” yazısı, yine yaklaşık bu dikdörtgenin içinde kalır. Sayfanın altındaki paragraf, resim sonradan yüklenince aşağı zıplamaz. Ölçü yazılmazsa tarayıcı önce küçük bir simge ayırır, gerçek dosya gelince metni iter.

Ölçü, fotoğrafın gerçek oranından çok farklıysa görüntü yassılaşır veya uzar. 320 ve 200, ancak resim de bu orana yakınsa kullanılır. Oranı bozmamak için gerçek dosyanın genişliği ve yüksekliği yazılır. Resmi kırpmak, gölge vermek veya ortaya hizalamak ileride CSS konusudur.

Başka bir sitedeki resim, `src` içine `https://` ile başlayan tam bir adres yazılarak da çağrılabilir. O site adresi değiştirirse veya resmi kaldırırsa sayfada yine kırık simge ve `alt` metni kalır. Bu rehberdeki örnekler, yanına konan dosyayı kullanır. Böylece sayfa, başka bir sitenin açık kalmasına bağlı olmaz.

## Sık yapılan hata

`alt` özelliğini hiç yazmamak, resim kırıkken sayfayı sessiz bırakır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Altsız görsel</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <img src="galata.jpg" />
  </body>
</html>
```

Tarayıcıda görünen:
`galata.jpg` yoksa başlığın altında küçük bir kırık simge durur. Simgenin yanında gölün veya kulenin adı yoktur. Bazı tarayıcılar dosya adını, “galata.jpg”, simgenin yanında gösterir. Bu ad bir açıklama değildir. Resim varken fotoğraf görünür ve eksiklik fark edilmez. Eksiklik, dosya taşınınca veya yol yazılırken bir harf düşünce ortaya çıkar.

Doğru belgede hem yol hem açıklama vardır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Açıklamalı görsel</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <img src="galata.jpg" alt="Galata Kulesi" />
  </body>
</html>
```

Tarayıcıda görünen:
Dosya yoksa simgenin yanında “Galata Kulesi” okunur. Dosya varsa kule fotoğrafı görünür, bu iki kelime görünmez.

İkinci hata, `<img>` etiketine kapanış yazıp içine paragraf koymaktır. `<img>Kule</img>` biçiminde “Kule” çoğu tarayıcıda resmin dışında, ardından gelen düz bir yazı olarak durur. Yazı, resmi anlatan ayrı bir paragraf olur. Resimle açıklamayı tek parça yapmak 12. günün konusudur.

Üçüncü hata, `src` ile `alt` değerlerini karıştırmaktır. `src` dosya yoludur. `alt` okunan cümledir. Yol, `alt` içine konursa ekranda dosya adı, dosya olarak da bulunamayan bir cümle kalır.

## Egzersizler

1. Klasöre herhangi bir fotoğrafı `izmir.jpg` adıyla koyun. Sayfada “İzmir” başlığının altında fotoğraf, fotoğrafın altında bir paragraf görünsün. Resim görünürken alternatif metin ekranda yazı olarak durmasın.
2. Dosyanın adını `izmir-eski.jpg` yapın, HTML içindeki yolu değiştirmeyin. Yeniledikten sonra kırık simge ve “İzmir Saat Kulesi” metni görünsün. Yolu yeni ada uydurun. Simge kalksın, fotoğraf geri gelsin.
3. `width` ve `height` değerlerini gerçek orandan çok farklı seçin. Fotoğrafın yassılaştığını görün. Sonra ölçüleri kaldırın veya dosyanın kendi ölçüsüne getirin. Kıyı veya kule yeniden doğal oranında dursun.

[← Önceki gün](../10-fragment-links/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../12-figure/ders.md)
