# 17. Gün — Seçim, onay, radyo (Select, Checkbox, Radio)

Bu gün, serbest yazı yerine hazır seçenek sunar. 16. gündeki kutu her kelimeyi kabul ediyordu. Kent dört taneyse ziyaretçi beşinci bir adı yanlışlıkla yazamasın. Seçim listesi tek bir seçenek, onay kutusu birden çok işaret, radyo düğmesi ise birbirini dışlayan seçenekler içindir.

## Listeden tek kent seçilir

`<select>` açılır listeyi kurar. `<option>` listenin bir satırıdır. Gönderilen değer, ekranda görünen cümle değil, `value` özelliğindeki kısa addır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent listesi</title>
  </head>
  <body>
    <h1>Hangi kent</h1>
    <form action="secim.html" method="get">
      <p>
        Kent
        <select name="kent">
          <option value="">Seçin</option>
          <option value="istanbul">İstanbul</option>
          <option value="izmir">İzmir</option>
          <option value="trabzon">Trabzon</option>
          <option value="van">Van</option>
        </select>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” yazısının yanında kapalı bir kutu vardır. Kutuda “Seçin” yazar. Yanında tarayıcının kendi oku durur. Ok tıklanınca dört kent alta dökülür: İstanbul, İzmir, Trabzon, Van. “Van” seçilince kutu kapanır ve üzerinde “Van” kalır. Diğer üç ad görünmez. “Gönder” basılınca adres `kent=van` ile biter. Ekrandaki “Van” değil, `value` içindeki `van` gider. İkisi aynı olmak zorunda değildir. Görünen ad okuyana, kısa değer pakete aittir.

İlk seçenek `value=""` ile boştur. Ziyaretçi listeyi açmadan gönderirse `kent=` sağında harf kalmaz. Bir seçenek `selected` ile işaretlenirse sayfa açıldığında o kent zaten kutudadır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hazır seçim</title>
  </head>
  <body>
    <h1>Hazır kent</h1>
    <form action="hazir.html" method="get">
      <p>
        Kent
        <select name="kent">
          <option value="istanbul">İstanbul</option>
          <option value="izmir" selected>İzmir</option>
          <option value="trabzon">Trabzon</option>
          <option value="van">Van</option>
        </select>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa ilk açıldığında kapalı kutuda “İzmir” yazar. “Seçin” satırı yoktur. Gönderilince `kent=izmir` gider. Başka bir kent seçilirse onun değeri gider. `selected` bir başlangıçtır, kilit değildir.

Uzun listeler `<optgroup>` ile öbeğe ayrılır. `label`, öbeğin adıdır ve kendisi seçilemez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Öbek</title>
  </head>
  <body>
    <h1>Suya göre</h1>
    <form action="obek.html" method="get">
      <p>
        Yer
        <select name="yer">
          <optgroup label="Deniz">
            <option value="istanbul">İstanbul</option>
            <option value="izmir">İzmir</option>
            <option value="trabzon">Trabzon</option>
          </optgroup>
          <optgroup label="Göl">
            <option value="van">Van</option>
          </optgroup>
        </select>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Liste açılınca “Deniz” ve “Göl” diye, seçilemeyen iki başlık vardır. “Deniz”in altında İstanbul, İzmir ve Trabzon durur. “Göl”ün altında yalnızca Van vardır. “Deniz”e tıklanınca kutu bir değer almaz. Van seçilince adres `yer=van` olur. Öbek adı adrese yazılmaz.

## Onay kutusu birden çoğunu işaretler

`<input type="checkbox">`, tek başına açılıp kapanan bir kutudur. Aynı addan birkaç tane varsa birden fazlası işaretli kalabilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Birden çok durak</title>
  </head>
  <body>
    <h1>Notta kalsın</h1>
    <form action="onay.html" method="get">
      <p>
        <input type="checkbox" name="durak" value="istanbul" />
        İstanbul
      </p>
      <p>
        <input type="checkbox" name="durak" value="izmir" checked />
        İzmir
      </p>
      <p>
        <input type="checkbox" name="durak" value="trabzon" />
        Trabzon
      </p>
      <p>
        <input type="checkbox" name="durak" value="van" checked />
        Van
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Dört küçük kare alt alta durur. Her karenin sağında bir kent adı vardır. İzmir ve Van karelerinin içinde onay işareti vardır. İstanbul ve Trabzon boştur. İşaretler tıklanınca değişir. İkisi birden, dördü birden veya hiçbiri işaretli olabilir. Yalnızca İzmir ve Van işaretliyken gönderilince adres `durak=izmir&durak=van` olur. Aynı ad iki kez gelir. İşaretsiz kutu pakete hiç girmez. Boş bir `durak=` değeri oluşmaz.

`checked`, sayfa açıldığında kutunun dolu olmasını sağlar. Ziyaretçi işareti kaldırırsa gönderimde o kent yer almaz.

## Radyo, birini seçince diğerini bırakır

`<input type="radio">` da küçük bir dairedir. Aynı `name` değerini paylaşan dairelerden yalnızca biri dolu kalır. Biri seçilince öteki boşalır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek yol</title>
  </head>
  <body>
    <h1>İletişim yolu</h1>
    <form action="radyo.html" method="get">
      <p>
        <input type="radio" name="yol" value="eposta" checked />
        E-posta
      </p>
      <p>
        <input type="radio" name="yol" value="telefon" />
        Telefon
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
İki yuvarlak vardır. “E-posta”nın yuvarlağı doludur. “Telefon”unkisi boştur. Telefona tıklanınca e-postanın içindeki doluluk kaybolur. İkisi birden dolu kalamaz. Gönderilince adreste tek bir `yol=eposta` veya `yol=telefon` durur. İkisi birden yazılmaz.

Onay kutusu ile radyo yan yana düşünülünce ayrım şudur. Notta hem İzmir hem Van kalabiliyorsa kare kullanılır. İletişim ya e-posta ya telefon ise yuvarlak kullanılır. İkisi birden serbest metin kutusuna yazdırılmaz.

## Sık yapılan hata

Her radyoya ayrı `name` vermek, “yalnızca biri seçilsin” kuralını kaldırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrılmış radyolar</title>
  </head>
  <body>
    <h1>Kopuk seçim</h1>
    <form action="kopuk.html" method="get">
      <p>
        <input type="radio" name="yol1" value="eposta" />
        E-posta
      </p>
      <p>
        <input type="radio" name="yol2" value="telefon" />
        Telefon
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
İki yuvarlak da tıklanınca dolu kalır. Biri diğerini boşaltmaz. Gönderilince adres `yol1=eposta&yol2=telefon` olabilir. Tek yol sorulmuş, iki cevap gitmiştir. Dairelerin görünüşü radyo olduğu hâlde davranış onay kutusuna dönmüştür.

Doğru belgede ikisinin de adı `yol` olur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ortak ad</title>
  </head>
  <body>
    <h1>Tek seçim</h1>
    <form action="ortak.html" method="get">
      <p>
        <input type="radio" name="yol" value="eposta" checked />
        E-posta
      </p>
      <p>
        <input type="radio" name="yol" value="telefon" />
        Telefon
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Telefon seçilince e-posta boşalır. Adreste yalnızca bir `yol` değeri vardır.

İkinci hata, `value` yazmadan kentin görünen adını paketlemek istemektir. Onay kutusunda `value` yoksa tarayıcı, işaretli kutu için `on` gönderir. Dört kent de `durak=on` olur. Hangi kentin işaretlendiği kaybolur. Her kutunun `value` değeri ayrıdır.

Üçüncü hata, radyo grubunda hiçbirini `checked` yapmamak ve ziyaretçinin hiçbirine dokunmadan göndermesidir. O zaman `yol` adreste hiç yoktur. Bir seçenek baştan seçiliyse paket her zaman bir yol taşır.

## Egzersizler

1. Açılır listede İstanbul, İzmir, Trabzon ve Van görünsün. Sayfa açıldığında kutuda İzmir yazsın. Gönderilince adres `kent=izmir` olsun. Listede görünen “İzmir” ile giden `izmir` aynı karakter değildir. Büyük harfli ad ekranda, kısa ad adreste kalsın.
2. Dört onay kutusu kurun. İzmir ve Van baştan işaretli olsun. İkisi işaretliyken gönderin. Adreste `durak` iki kez, `izmir` ve `van` değerleriyle görünsün. İstanbul’un işareti boşsa adresinde `istanbul` olmasın.
3. E-posta ve telefon radyolarına bilerek ayrı adlar verin. İkisini birden doldurun. Sonra adları ortak yapın. Telefon seçilince e-postanın dairesi boşalsın. Adreste tek `yol` kalsın.

[← Önceki gün](../16-text-inputs/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../18-number-date-file/ders.md)
