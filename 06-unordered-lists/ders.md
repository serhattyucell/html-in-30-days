# 6. Gün — Sırasız listeler (Unordered Lists)

Bu gün, sırası değişse de anlamı bozulmayan maddeleri bir liste yapar. 5. günde aynı türden satırlar `<br>` ile alt alta dizilmişti. O satırlar birbirinden ayrı maddeler ise liste, adres gibi duran bir paragraf değildir.

## Madde, madde işaretiyle durur

`<ul>` sırasız bir liste açar. `<li>` o listenin tek bir maddesini taşır. Sıra önemli değilse bu çift kullanılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört kent</title>
  </head>
  <body>
    <h1>Serhat'ın not klasörü</h1>
    <p>Sıra bir öncelik bildirmez. Dördü de aynı türden nottur.</p>
    <ul>
      <li>İstanbul</li>
      <li>İzmir</li>
      <li>Trabzon</li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“Serhat'ın not klasörü” büyük başlıktır. Altında, listenin bir öncelik olmadığını söyleyen normal bir paragraf vardır. Onun altında dört satır, soldan içeri girintili durur. Her satırın başında bir madde işareti vardır. İşaret çoğu tarayıcıda dolu bir dairedir. Rakam yoktur. “İstanbul”, “İzmir”, “Trabzon” ve “Van” yukarıdan aşağı bu sırayla okunur. Maddelerin arasında paragraf kadar geniş boşluk yoktur; satırlar listeye özgü daha sık bir aralıkla durur. `<ul>` ve `<li>` yazıları ekranda görünmez.

Liste, paragrafların yerine geçmez. Paragraf, cümleleri anlatır. Liste, aynı türden parçaları dizer. Bir kentin tarihini uzun uzun anlatan iki cümle iki `<p>` olarak kalır. Görülecek yerlerin adları ise madde olur.

## Maddenin içinde vurgu durabilir

`<li>` yalnızca bir kelime taşımak zorunda değildir. İçinde cümle, `<strong>` ve `<em>` durabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İzmir maddeleri</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <h2>Bakılacak yerler</h2>
    <ul>
      <li><strong>Saat Kulesi</strong>, meydanın ortasındadır.</li>
      <li>Kordon, <em>kıyı boyunca</em> yürünecek yoldur.</li>
      <li>Körfez, kentin denize açılan yanıdır.</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” en büyük, “Bakılacak yerler” ondan küçüktür. Üç maddenin başında daire vardır. Birinci maddede yalnızca “Saat Kulesi” kalındır, devamı düzdür. İkinci maddede yalnızca “kıyı boyunca” italiktir. Üçüncü madde bütünüyle düzdür. Kalın veya italik parça, madde işaretinin yanında, aynı satırda durur. Başlık ile liste arasındaki boşluk, başlık ile paragraf arasındaki boşluğa benzer.

## İki ayrı liste, iki ayrı grup

Aynı sayfada iki konu varsa iki `<ul>` açılır. Tek listenin içine ara başlık gibi düz yazı sıkıştırılmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki liste</title>
  </head>
  <body>
    <h1>Kıyı kentleri</h1>
    <h2>Deniz</h2>
    <ul>
      <li>İstanbul</li>
      <li>İzmir</li>
      <li>Trabzon</li>
    </ul>
    <h2>Göl</h2>
    <ul>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“Kıyı kentleri” en büyük başlıktır. “Deniz” altında üç daireli madde vardır: İstanbul, İzmir, Trabzon. “Göl” başlığı o listenin bittiğini, yeni bir bölümün açıldığını gösterir. “Van” tek başına, kendi dairesiyle, ikinci listededir. İki listenin işaretleri aynı görünür. Ayrımı sağlayan, aradaki `<h2>` ve iki ayrı `<ul>` çiftidir. Van, İstanbul’un dördüncü maddesi gibi birinci listenin altında yapışık durmaz. Arada “Göl” başlığı vardır.

Bir maddelik liste de geçerlidir. Tek madde varsa bile `<li>`, `<ul>` içinde durur. Madde işaretini silmek için listeyi paragrafa çevirmek gerekmez. İşaretin görünmemesi ileride CSS konusudur.

## Sık yapılan hata

Liste etiketinin içine maddeyi atlayarak düz yazı koymak, o yazıyı listenin dışında bırakır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Eksik madde</title>
  </head>
  <body>
    <h1>Van</h1>
    <ul>
      Van Gölü
      <li>Van Kalesi</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü” madde işareti olmadan, listenin girintisinden önce veya listenin üstünde durur. “Van Kalesi” ise daireyle, girintili bir madde olarak görünür. İki satır aynı listenin iki maddesi gibi durmaz. Tarayıcı, `<ul>` içinde doğrudan durmasına izin verilen şeyi `<li>` sayar. Düz yazıyı kardeş madde yapmaz.

Doğru belge:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tam maddeler</title>
  </head>
  <body>
    <h1>Van</h1>
    <ul>
      <li>Van Gölü</li>
      <li>Van Kalesi</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
İki satır da daireyle, aynı hizada ve girintili durur. “Van Gölü” ve “Van Kalesi” aynı listenin maddeleridir.

Kapanışsız `<li>` de benzer bir karışıklık üretir. Bir maddenin kapanışı yazılmazsa sonraki maddenin metni birincinin içine kayabilir veya tarayıcı kendi kapatır. Ekran bazen doğru görünür. Kaynak, her maddeyi kendi `</li>` etiketiyle bitirince okunur kalır.

Rakamla “1.” “2.” yazıp onları `<ul>` içine koymak da sıralı liste değildir. Madde işaretinin yanında bir de elde yazılmış numara görünür. Sıra gerçekten önemliyse sonraki günün etiketi kullanılır.

## Egzersizler

1. “Bakılacak yerler” başlığının altına madde işaretli dört satır koyun: Galata Kulesi, Saat Kulesi, Kordon, Van Kalesi. Rakam görünmesin. Dört satır da aynı girintide olsun.
2. Bu listeyi ikiye bölün. “Kentler” altında İstanbul, İzmir, Trabzon ve Van; “İşaretler” altında Galata Kulesi ve Saat Kulesi görünsün. İki listenin arasında bir alt başlık olsun.
3. Bir maddede yalnızca “Boğaz” kelimesi kalın olsun, maddenin geri kalanı düz bir cümle olarak aynı satırda kalsın. Madde işareti kaybolmasın.

[← Önceki gün](../05-text/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../07-ordered-lists/ders.md)
