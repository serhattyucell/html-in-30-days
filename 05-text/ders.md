# 5. Gün — Kalın, italik, satır sonu (Text)

Bu gün, paragrafın içindeki birkaç kelimeyi önemine göre ayırır ve aynı paragrafın içinde alt satıra iner. 4. günde yeni bir düşünce yeni bir `<p>` istiyordu. Bugün düşünce değişmeden vurgu ve satır kırılması yapılır.

## Önemli söz kalın durur

`<strong>`, cümleden çıkarılınca anlamın zayıflayacağı kadar önemli bir parçayı işaretler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Önemli uyarı</title>
  </head>
  <body>
    <h1>Van Gölü</h1>
    <p>Tekne saatine <strong>rüzgârdan önce</strong> bakılır. Göl geniş, kıyı uzaktır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü” büyük başlıktır. Altındaki paragraf normal puntodadır. Yalnızca “rüzgârdan önce” kalın görünür. “Tekne saatine” ve “bakılır” kalın değildir. Kalın parça, paragrafın içinde, yeni bir satır açmadan durur. Çerçeve veya renk yoktur. Rengi ileride CSS değiştirir.

`<strong>` bir paragrafın yerini tutmaz. Bütün cümleyi bu etikete almak, cümlenin tamamını kalın yapar ve vurguyu siler. Etiket, vurguyu hak eden kısa parçanın etrafına konur. Kapanış unutulursa tarayıcı, paragraf kapanana kadar kalan sözcükleri de kalın çizer.

## Vurgu italik durur

`<em>`, okunurken sesin üzerine basılacak kelimeyi işaretler. Önemden çok, cümledeki karşıtlığı taşır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Vurgu</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Galata Kulesi bu yakadadır, karşı kıyı ise <em>aynı kentin</em> parçasıdır.</p>
    <p>Kuleye <strong>sabah</strong> çıkılır, <em>öğleden sonra</em> değil.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Birinci paragrafta yalnızca “aynı kentin” sözü yatık (italik) durur. İkinci paragrafta “sabah” kalın, “öğleden sonra” italiktir. Diğer kelimeler düzdür. İki paragraf arasında boşluk vardır. Kalınlık ve yatıklık aynı kelimede birleşecekse etiketler iç içe konur: önem bir de vurgu istiyorsa `<strong><em>sabah</em></strong>` hem kalın hem italik görünür. Önce açılan etiket sonra kapanır.

## Kalınlık her zaman önem değildir

`<b>`, sözü sayfadaki diğer kelimelerden ayırır ama ona ek bir önem yüklemez. `<i>` de sözü yatık yapar; bu, bir eser adı veya başka bir dilde kalmış bir ifade içindir, sesli vurgu için değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayırmak ve önem</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Notun konu adı: <b>Saat Kulesi</b>.</p>
    <p>Kule, <i>Konak</i> meydanının içindedir.</p>
    <p>Ziyaretten önce <strong>saate bakılır</strong>.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Saat Kulesi” kalın, “Konak” italik, “saate bakılır” yine kalındır. Ekranda `<b>` ile `<strong>` aynı kalınlığı, `<i>` ile `<em>` aynı yatıklığı verir. Fark kaynakta ve anlamda durur. “Saat Kulesi” yalnızca konunun adıdır, uyarı değildir. “saate bakılır” ise çıkarılınca notun eksileceği bir uyarıdır. Görünüşü birincisi gibi yapmak, ikincisinin yerini tutmaz. Rengi ayrı boyamak ileride CSS konusudur. Bu sayfada ayrım, doğru etiketle yapılır.

Üç cümle de düz kalın veya düz italik gibi durabilir. Hangi etiketin seçildiği, sayfayı okuyan bir program için değişir. Program, `<strong>` içindeki sözü önemli, `<b>` içindeki sözü yalnızca ayırt edilmiş sayar.

## Aynı paragrafın içinde satır sonu

`<br>` etiketi, paragrafı ikiye bölmeden, bulunduğu yerde alt satıra iner. Adres, kısa bir dörtlük veya üst üste durması gereken birkaç satır için kullanılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Satır sonu</title>
  </head>
  <body>
    <h1>Serhat'ın notu</h1>
    <p>
      İzmir, Kordon<br />
      Trabzon, kıyı<br />
      Van, göl<br />
      İstanbul, Boğaz
    </p>
    <p>Bu ikinci paragraftır ve bir önceki dörtlüden ayrı durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Serhat'ın notu” büyük başlıktır. Hemen altında dört kısa satır, aralarında paragraf boşluğu olmadan, sık dizilir:

İzmir, Kordon
Trabzon, kıyı
Van, göl
İstanbul, Boğaz

Bu dört satır tek bir paragrafın içindedir. Onların altında, arada genişçe bir boşlukla, “Bu ikinci paragraftır ve bir önceki dörtlüden ayrı durur.” cümlesi ayrı bir paragraf olarak durur. `<br>` ekranda “br” diye yazılmaz. Kapanış etiketi de almaz. Açılışın içindeki eğik çizgi, bu boş etiketin bittiğini belirtir. Karakter satırındaki `/>` ile aynı biçimdir.

İki düşünceyi ayırmak için art arda `<br>` dizilmez. Düşünce değiştiyse yeni bir `<p>` açılır. `<br>` yalnızca aynı düşüncenin içindeki satırı kırar.

## Sık yapılan hata

Önem etiketini kapatmamak, paragrafın geri kalanını da kalın yapar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Açık kalan vurgu</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Yola <strong>erken çıkılır. İskele kalabalıktır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“erken çıkılır. İskele kalabalıktır.” sözlerinin tamamı kalın durur. Amaç yalnızca “erken” kelimesini ayırmaktı. Paragraf bittiği için tarayıcı vurguyu çoğu zaman bir sonraki başlığa taşımaz. Yine de bu paragrafın bütün kalanı kalındır ve kaynak geçersizdir.

Doğru belge:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapanmış vurgu</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Yola <strong>erken</strong> çıkılır. İskele kalabalıktır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Yalnızca “erken” kalındır. “çıkılır” ve sonraki cümle düzdür.

İç içe etiketleri ters kapatmak da aynı aileden bir hatadır. `<strong><em>Boğaz</strong></em>` yazılırsa tarayıcı çoğu zaman hem kalın hem italik çizerek hatayı örter. Kaynak yine düzgün değildir. Önce `<em>` kapanır, sonra `<strong>` kapanır.

İkinci hata, her cümlenin sonuna `<br>` koyup paragrafları birbirinden ayırmaktır. Cümleler birbirine yapışık, aralıksız bir şerit olur. Ayrı düşünceler ayrı `<p>` ile yazılır.

## Egzersizler

1. İstanbul paragrafında yalnızca “Boğaz” kelimesi kalın görünsün. Cümlenin geri kalanı düz olsun.
2. Aynı sayfada “öğleden sonra” sözü italik, “sabah” sözü hem kalın hem italik görünsün. İki söz aynı paragrafın içinde kalsın.
3. İzmir, Trabzon, Van ve İstanbul adlarını tek paragraf içinde dört satıra dizin. Satırların arasında paragraf boşluğu olmasın. Altlarına, arada boşluk bırakarak, “Dört satır tek nottur.” cümlesini ayrı bir paragraf olarak koyun.

[← Önceki gün](../04-paragraphs/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../06-unordered-lists/ders.md)
