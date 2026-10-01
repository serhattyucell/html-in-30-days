# 4. Gün — Paragraflar (Paragraphs)

Bu gün, gövdeye gerçek cümleler koyar. 3. günde sayfa yalnızca başlıklardan oluşuyordu. Bugün paragrafın başlıktan farkı, kaynaktaki satır sonunun ekrana geçmediği ve boşlukların birleştiği görülür.

## Bir düşünce, bir paragraf

`<p>` etiketi, ardışık cümleleri tek bir blok yapar ve bir sonraki bloktan görsel olarak ayırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İzmir paragrafları</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>İzmir Ege kıyısındadır. Körfez, kenti denize doğru açar.</p>
    <p>Saat Kulesi, kentin kolay bulunan bir işaretidir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “İzmir paragrafları” yazar. “İzmir” büyük bir başlıktır. Onun altında iki paragraf vardır. Birinci paragrafta iki cümle aynı bloktadır ve aralarında yalnızca bir boşluk vardır; cümleler alt alta kırılmaz. İkinci paragraf, “Saat Kulesi, kentin kolay bulunan bir işaretidir.” diye ayrı bir blok olarak, birinciyle arasında boş bir aralık bırakılmış biçimde durur. Başlık ile ilk paragraf arasında da bir aralık vardır.

Paragraf, başlık değildir. Başlık bölümün adıdır ve kalın, daha büyük bir satırdır. Paragraf o bölümün anlatımıdır ve normal puntodadır. İki paragraf, iki ayrı `<p>` çiftidir. Tek bir `<p>` içine bütün sayfayı yığmak, aradaki konu değişmesini ekranda siler.

## Kaynakta alt satıra inmek yetmez

HTML, kaynaktaki satır sonunu ve fazla boşluğu, metin düzenleyicisinin kolaylığı sayar. Ekranda yeni bir paragraf açmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yok sayılan satır sonu</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>
      Trabzon Karadeniz kıyısındadır.
      Çarşıdan denize inilir.

      Bu satır kaynakta boş bir satırın altında duruyor.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“Trabzon” başlığının altında tek bir paragraf vardır. “Trabzon Karadeniz kıyısındadır.” cümlesinden sonra ekranda alt satıra geçilmez. “Çarşıdan denize inilir.” aynı paragrafın devamı olarak, arada tek boşlukla akar. Kaynakta bırakılan boş satır da yeni bir paragraf açmaz. “Bu satır kaynakta boş bir satırın altında duruyor.” cümlesi, önceki cümlenin peşine yapışır. Uzun satır, pencere kenarına gelince tarayıcı kendisi kırar. O kırılma, kaynaktaki Enter ile aynı yerde olmak zorunda değildir. Pencere daraltılırsa kırılma yeri değişir.

Üç ayrı düşünce üç etikete bölününce görünüş değişir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Üç paragraf</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>Trabzon Karadeniz kıyısındadır.</p>
    <p>Çarşıdan denize inilir.</p>
    <p>Bu satır artık kendi paragrafındadır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Başlığın altında üç blok vardır. Her cümle kendi satır grubundadır. Blokların arasında tarayıcının bıraktığı dikey boşluk görünür. Pencere daralsa da üç blok birbirine karışmaz. Yalnızca her bloğun içindeki satır, pencereye göre yeniden kırılır.

## Yan yana boşluklar tek boşluk olur

Paragraf içindeki art arda boşluk, sekme ve satır sonu, ekranda tek bir boşluğa iner.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Birleşen boşluk</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Van      Gölü      geniştir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü geniştir.” cümlesi, kelimelerin arasında tek boşlukla durur. Kaynakta `Van` ile `Gölü` arasına konmuş uzun boşluk şerit hâlinde görünmez. Metni sütun gibi hizalamak için boşluk tuşuna basmak işe yaramaz. Sütun işi 13. günde tablo ile kurulur. Aralık büyütmek ileride CSS konusudur.

## Başlık ile paragraf yan yana durmaz

Başlık bir bölümü açar, paragraf o bölümü anlatır. İkisi aynı satıra yazılmış gibi kaynakta dursalar da ekranda alt alta inerler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İstanbul iki parça</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Kent, Boğaz ile iki yakaya ayrılır.</p>
    <h2>Avrupa yakası</h2>
    <p>Galata Kulesi bu yakada yükselir.</p>
    <h2>Anadolu yakası</h2>
    <p>Karşı kıyı aynı kentin içindedir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte büyük “İstanbul”, altında normal puntoda Boğaz cümlesi vardır. Sonra orta büyüklükte “Avrupa yakası” ve onun cümlesi gelir. Ardından aynı büyüklükte “Anadolu yakası” ve son cümle durur. Başlıklar kalındır. Paragraflar kalın değildir. Her parçanın arasında bir aralık vardır. İki yaka aynı düzeyde olduğu için iki `<h2>` aynı puntodadır.

## Sık yapılan hata

Paragrafın içine başka bir paragraf koymak, tarayıcının birinci paragrafı erken kapatmasına yol açar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İç içe paragraf</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl geniştir.
      <p>Kale tepeden bakar.</p>
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Ekranda yine iki paragraf varmış gibi durur. “Göl geniştir.” ayrı, “Kale tepeden bakar.” ayrı görünür. Kaynak ise geçersizdir. Tarayıcı, ikinci `<p>` başlarken birincisini kapatır. Sondaki `</p>` fazladan kalır. Görüntü tesadüfen düzgün olabilir. Bir sonraki gün içine satır sonu veya vurgu eklenince onarım şaşırtabilir.

Doğrusu, iki paragrafı kardeş yazmaktır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kardeş paragraflar</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl geniştir.</p>
    <p>Kale tepeden bakar.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” başlığının altında iki ayrı blok durur. Birincide “Göl geniştir.”, ikincide “Kale tepeden bakar.” vardır. İkisi de normal puntodadır ve aralarında boşluk vardır.

Başka bir hata, paragrafları ayırmak için boş `<p></p>` dizmek ya da aynı cümleyi birçok kez kopyalamaktır. Boş paragraf, tarayıcıdan tarayıcıya değişen belirsiz bir aralık bırakır. Asıl anlatılacak ikinci düşünce yoksa ikinci etiket de yazılmaz.

## Egzersizler

1. “İstanbul” başlığının altına iki paragraf yazın. Birincide kentin iki yakası, ikincide Galata Kulesi geçsin. İki paragraf arasında gözle görülür bir aralık olsun. İkisi de aynı puntoda ve kalın olmasın.
2. Aynı paragrafın içine Enter ile üç satır kırın ve fazla boşluk koyun. Ekranda tek blok ve kelimeler arasında tek boşluk kaldığını görün. Sonra her satırı kendi `<p>` etiketine alın. Üç ayrı blok görünsün.
3. Bir paragrafı ikinci bir paragrafın içine koyun. Sayfa yine alt alta dursa bile kaynağı düzeltin. İki `<p>`, birinin diğerinin içinde olmadığı, art arda durduğu bir belgeye dönsün.

[← Önceki gün](../03-headings/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../05-text/ders.md)
