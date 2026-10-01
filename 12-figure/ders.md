# 12. Gün — Figür ve alt yazı (Figure and Figcaption)

Bu gün, bir fotoğrafı ona ait açıklamayla tek parça yapar. 11. günde resmin altında duran paragraf, görünüşte yakın olsa da belgeye “bu cümle bu resmin alt yazısıdır” demiyordu. Sıradan bir paragraf, bir sonraki cümlenin devamı da olabilirdi. `<figure>` ve `<figcaption>` bu bağı kurar.

## Alt yazı, görsele aittir

`<figure>`, birlikte durması gereken görseli ve yazıyı bir blok yapar. `<figcaption>`, o bloğun alt yazısıdır.

Aynı klasöre `van-golu.jpg` konur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Gölün alt yazısı</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Aşağıdaki parça, gölün fotoğrafı ile onun alt yazısını bir arada tutar.</p>
    <figure>
      <img src="van-golu.jpg" alt="Van Gölü kıyısı" />
      <figcaption>Van Gölü, kentin kıyısından bakılınca.</figcaption>
    </figure>
    <p>Bu paragraf figürün dışındadır ve notun devamıdır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” başlığından sonra bir giriş paragrafı vardır. Onun altında fotoğraf durur. Fotoğraf yoksa kırık simge ve “Van Gölü kıyısı” metni durur. Fotoğrafın hemen altında, ayrı bir satır olarak “Van Gölü, kentin kıyısından bakılınca.” yazar. Bu satır mavi değildir, madde işareti yoktur. Çoğu tarayıcıda normal puntodadır ve blok biraz içeriden başlayabilir. En altta, arada bir boşlukla, “Bu paragraf figürün dışındadır ve notun devamıdır.” cümlesi vardır. Alt yazı, resim görünürken de görünür. `alt` metni ise resim görünürken yazılmaz. İkisi aynı işi yapmaz. `alt`, resmin yerine geçer. Alt yazı, resmin yanında duran ve herkese görünen açıklamadır.

`<figcaption>`, `<figure>` içinde bir kez durur. Resimden sonra gelirse ekranda altta, resimden önce gelirse ekranda üstte durur. Kent notunda yazı, fotoğrafın altında okunur.

## Paragraf, alt yazının yerine geçmez

Bir fotoğrafın altında duran `<p>`, gözle benzer bir satır üretir. Belgede o satır, figürün parçası değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrı düşmüş yazı</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <img src="saat-kulesi.jpg" alt="İzmir Saat Kulesi" />
    <p>Saat Kulesi, Konak meydanındadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Kule fotoğrafı veya kırık simge, altında da “Saat Kulesi, Konak meydanındadır.” cümlesi vardır. Satır, figürlü örnekteki alt yazıya benzer. Aradaki boşluk biraz daha geniş olabilir. Ekranda bağ, göze bırakılmıştır. Kaynakta cümle, resimden sonraki herhangi bir paragraf olabilir. Notun bir sonraki cümlesiyle karışır.

Aynı içerik figüre alınınca bağ etiketin kendisindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Birleşmiş yazı</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <figure>
      <img src="saat-kulesi.jpg" alt="İzmir Saat Kulesi" />
      <figcaption>Saat Kulesi, Konak meydanındadır.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğrafın altında alt yazı tek satır olarak durur. Sayfada ondan sonra gelen başka bir paragraf, figürün içinde kalmaz. Alt yazı, resme ait cümle olduğunu etiketle söyler.

## Figür yalnızca fotoğraf taşımaz

Bir blok, sayfadan çıkarılıp tek başına da okunabiliyorsa figür olabilir. 8. gündeki iç içe liste, bir durağın özeti olarak figüre konabilir. Listenin dersi değişmez. Yeni olan, listenin bir alt yazı almasıdır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Listenin alt yazısı</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <figure>
      <ol>
        <li>Kıyıya in</li>
        <li>Çarşıyı geç</li>
      </ol>
      <figcaption>Trabzon durağındaki iki hazırlık.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
“1. Kıyıya in” ve “2. Çarşıyı geç” satırları, kendi numaralarıyla durur. Listenin altında “Trabzon durağındaki iki hazırlık.” cümlesi vardır. Numaralar alt yazının parçası değildir. Cümle, listenin bütününe aittir. Çerçeve çizilmez. Çerçeve ileride CSS konusudur. Birlik, iki etiketin iç içe olmasından gelir.

Fotoğraf ve liste aynı figürde yan yana süslenmez. Bu rehberde bir figürde bir konu vardır: ya gölün fotoğrafı ya da durağın kısa listesi.

## Sık yapılan hata

Alt yazıyı figürün dışına koymak, cümleyi sıradan bir paragrafa çevirir. Etiket figürün dışında geçersizdir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dışarıda kalan yazı</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <figure>
      <img src="galata.jpg" alt="Galata Kulesi" />
    </figure>
    <figcaption>Galata Kulesi, bir yakada yükselir.</figcaption>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf veya kırık simge görünür. “Galata Kulesi, bir yakada yükselir.” cümlesi de onun altında durabilir. Tarayıcı, yeri yanlış etiketi çoğu zaman yine bir satır olarak çizer. Görüntü doğru figüre benzeyebilir. Kaynakta alt yazı, figürün parçası değildir. Bazı araçlar bu cümleyi resimle ilişkilendirmez.

Doğru belgede alt yazı, figür kapanmadan önce durur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İçeride duran yazı</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <figure>
      <img src="galata.jpg" alt="Galata Kulesi" />
      <figcaption>Galata Kulesi, bir yakada yükselir.</figcaption>
    </figure>
  </body>
</html>
```

Tarayıcıda görünen:
Kulenin fotoğrafı üstte, “Galata Kulesi, bir yakada yükselir.” cümlesi hemen altındadır. İkisi tek figürdür.

İkinci hata, `alt` ile alt yazıyı aynı cümlenin kopyası diye silmektir. Alt yazı ekranda durur. `alt` ise resim yüklenemezse durur. Fotoğraf kırık ve `alt` boşsa simgenin yanında bir açıklama kalmaz. Alt yazı simgenin altında kalır. İkisi birden yazılır. Sözleri birebir aynı olmak zorunda değildir. `alt` daha kısa olabilir. Alt yazı, bakan herkese bir cümle okutabilir.

## Egzersizler

1. `kordon.jpg` ile bir figür kurun. Fotoğrafın altında “İzmir’de Kordon, kıyı boyunca yürünecek yoldur.” satırı görünsün. Bu satır sayfanın son paragrafı gibi, figürden kopuk durmasın.
2. Aynı sayfaya figürün dışına bir paragraf daha ekleyin: “Not burada sürer.” Figürü alt yazısıyla birlikte silmeyi denemeden, dış paragrafın yerinde kaldığını görün. Alt yazı yalnızca fotoğrafa ait olsun.
3. Bir alt yazıyı `</figure>` etiketinden sonraya alın. Sonra onu yeniden figürün içine koyun. “Van Kalesi tepeden bakar.” cümlesi, kale fotoğrafının hemen altında dursun.

[← Önceki gün](../11-images/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../13-tables/ders.md)
