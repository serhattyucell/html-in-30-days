# 2. Gün — Belge iskeleti (Document)

Bu gün, her HTML dosyasının aynı sırayla kurulmuş iskeletini parçalarına ayırır. 1. günde bu iskelet hazır verilmişti. Bugün her satırın ne işe yaradığı ve yanlış yere yazılan bir metnin neden ekranda kaybolduğu görülür.

## Belgenin tarayıcıya türünü söyleyen satır

`<!DOCTYPE html>` satırı, dosyanın güncel HTML kurallarıyla okunacağını tarayıcıya bildirir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İskelet</title>
  </head>
  <body>
    <h1>İzmir notu</h1>
    <p>Bu cümle gövdededir, bu yüzden sayfada görünür.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “İskelet” yazar. Sayfada büyük başlık “İzmir notu” ve altında bir paragraf durur. `DOCTYPE` satırı, `html`, `head` ve `body` kelimeleri ekranda yoktur. Sayfa, tarayıcının eski bir belge sanıp tuhaf boşluklar bırakacağı bir kipe girmez.

Bu satır bir etiket çifti değildir; kapanışı yoktur. Dosyanın en üstünde, başka satırdan önce durur. Büyük-küçük harf bu satırda tarayıcı için genellikle fark etmez; bu rehberde `DOCTYPE` büyük, `html` küçük yazılır.

## Sayfanın dili

`lang` özelliği, sayfadaki yazının hangi dilde olduğunu belirtir.

Aynı iskelet kullanılır; değişen satır `html` etiketidir. Türkçe bir sayfa şöyle açılır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dil</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Boğazın iki yakası aynı belgenin içindedir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Ekranda “İstanbul” başlığı ve “Boğazın iki yakası aynı belgenin içindedir.” paragrafı durur. `lang="tr"` diye bir yazı görünmez. Dil bilgisi ekranın üstüne basılmaz. Ekran okuyucu ve tarayıcının çeviri araçları bu bilgiyi belgeden alır. Türkçe sayfada değer `tr` olur. Belgenin tamamını saran etiket `<html>` ile açılır, `</html>` ile biter. Diğer her şey onun içindedir.

## Baş bölge sayfada görünmez

`<head>` bölgesi, sekmenin adını ve belgenin teknik bilgisini taşır; buraya yazılan düz yazı sayfa gövdesine düşmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Trabzon defteri</title>
    <p>Bu paragraf yanlışlıkla baş bölgeye kondu.</p>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Karadeniz kıyısı gövdedeki paragrafta durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Trabzon defteri” yazar. Sayfada “Trabzon” başlığı ve “Karadeniz kıyısı gövdedeki paragrafta durur.” cümlesi vardır. Baş bölgeye yazılmış “Bu paragraf yanlışlıkla baş bölgeye kondu.” cümlesi ekranda yoktur.

`<head>` ile `<body>` kardeştir; biri diğerinin içinde değildir. İkisi de `<html>` içindedir. `<title>` yalnızca bir tane olur ve sekmenin yazısıdır. Yer imine, tarayıcı geçmişine ve sekme çubuğuna bu yazı gider. Gövdedeki `<h1>` ise sayfanın içindeki ana başlıktır. İkisi aynı kelime olmak zorunda değildir; sekme kısa, sayfa başlığı daha açık olabilir.

## Harflerin bozulmaması

`<meta charset="UTF-8" />` satırı, dosyadaki harflerin hangi eşleşme tablosuyla okunacağını söyler.

Türkçe harfler içeren kısa bir gövde yeter. Karakter satırı yerindeyken belge şöyledir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Türkçe harfler</title>
  </head>
  <body>
    <h1>İçeren köşeler</h1>
    <p>İstanbul, İzmir, Trabzon ve Van. Şehir, göl, dağ, üç köprü.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Başlık “İçeren köşeler” olarak, yani İ ve ç harfleri bozulmadan okunur. Paragrafta dört kentin adı ve “Şehir, göl, dağ, üç köprü.” cümlesi düzgün görünür. `ş`, `ğ`, `ü` harflerinin yerinde kutu, soru işareti ya da `Å` gibi yabancı parçalar durmaz.

Bu satır bir kez yazılır, kapanış etiketi almaz. `<head>` içinde, `<title>` satırından önce durması en güvenli yerdir. `charset` bir özelliktir. Özellik, etiketin içine yazılan ve o etikete ek bilgi veren addır. Özelliklerin genel kuralları 22. günde toplanır. Bugün bunlardan yalnızca dil ve karakter eşlemesi kullanılır.

## Gövde, ekranda duran yerdir

`<body>`, ziyaretçinin okuduğu her şeyi içine alır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört kent</title>
  </head>
  <body>
    <h1>Serhat'ın kent listesi</h1>
    <p>İzmir Ege'dedir.</p>
    <p>Van, gölün kıyısındadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Dört kent” vardır. Sayfada büyük bir başlık, “Serhat'ın kent listesi”, onun altında iki ayrı paragraf vardır. Paragrafların arasında boşluk bırakılmıştır. “İzmir Ege'dedir.” birinci, “Van, gölün kıyısındadır.” ikincidir. Baş bölgedeki teknik satırlar görünmez.

Bir belgede bir `<body>` olur. Görünen başlık, paragraf, daha sonraki günlerde liste, görsel, tablo ve form hep bu bölgenin içine yazılır.

## Sık yapılan hata

Görünmesi istenen cümleyi `<title>` ile gövde arasında, baş bölgenin içine yazmak o cümleyi ekrandan siler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kayıp cümle</title>
    İstanbul iki kıtada durur.
  </head>
  <body>
    <h1>İstanbul</h1>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Kayıp cümle”, sayfada yalnızca “İstanbul” başlığı vardır. “İstanbul iki kıtada durur.” cümlesi kaynakta durduğu hâlde sayfada yoktur. Bazı tarayıcılar bu tür bozuk yerleşimi onarıp cümleyi gövdeye taşıyabilir. Onarım her tarayıcıda aynı değildir. Cümle bir belgede görünür, diğerinde kaybolur. Güvenilir sonuç için görünmesi istenen her yazı `<body>` içine konur.

Doğru belge:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kayıp cümle</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>İstanbul iki kıtada durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” başlığının altında “İstanbul iki kıtada durur.” paragrafı da vardır.

İkinci hata, karakter satırını silmektir. Dosya başka bir eşleşmeyle açılırsa “İzmir” kelimesindeki harfler parçalanır. Satır geri konup dosya UTF-8 olarak kaydedildiğinde kelime eski hâline döner.

## Egzersizler

1. `iskelet.html` dosyasında sekme başlığı “Van defteri”, sayfadaki ana başlık “Van Gölü” olsun. Başlığın altında “Not gövdededir.” cümlesi görünsün. “Not gövdededir.” cümlesini yalnızca `<head>` içine yazıp sayfayı yenileyin. Cümlenin ekrandan kalktığını doğrulayın, sonra cümleyi yeniden gövdeye alın.
2. Karakter satırını silin, dosyayı kaydedin ve “Şehir, göl, dağ” cümlesindeki harflere bakın. Bozulma görünürse satırı geri koyun. Dört kentin adı da düzgün okunsun: İstanbul, İzmir, Trabzon, Van.
3. Aynı dosyada `<html lang="tr">` satırını ve `DOCTYPE` satırını yerinde bırakın. Görünen yazıyı değiştirmeyen bu iki satırın kaynakta durduğunu, ekranda yazı olarak çıkmadığını doğrulayın.

[← Önceki gün](../01-introduction/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../03-headings/ders.md)
