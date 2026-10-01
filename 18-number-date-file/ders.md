# 18. Gün — Sayı, tarih, dosya (Number, Date, File)

Bu gün, serbest metin kutusuna yazılması gerekmeyen üç değeri ayırır. 17. günde seçim, hazır kelimelerdendi. Sayı, takvim günü ve bir dosya da serbest cümle değildir. Tarayıcı, bu üçü için kendi küçük aracını açar. Araç, işletim sistemine ve tarayıcıya göre biraz değişir. Değişmeyen şey, giden değerin biçimidir.

## Sayı, oklarla artar

`type="number"` alanı, yalnız sayı kabul etmeye yönelir. `min` en küçük, `max` en büyük, `step` her adımda ne kadar artılacağını söyler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kişi sayısı</title>
  </head>
  <body>
    <h1>Trabzon notu</h1>
    <form action="sayi.html" method="get">
      <p>
        Kişi sayısı
        <input type="number" name="kisi" min="1" max="6" step="1" value="2" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kişi sayısı” yanında dar bir kutu vardır. İçinde `2` yazar. Kutunun sağında, çoğu masaüstü tarayıcıda, yukarı ve aşağı oklar durur. Yukarı ok `3` yapar, aşağı ok `1` yapar. `1` altındayken aşağı ok yeni bir sayı yazmaz. `6` üstünde de ok durur. Kutuya `Trabzon` yazmaya çalışınca tarayıcı harfi kabul etmeyebilir veya gönderimde “bir sayı girin” diye uyarı verir. Uyarı çıkarsa sayfa yenilenmez.

`4` ile gönderilince adres `kisi=4` olur. `step="1"` tam sayı adımıdır. `step="2"` yapılırsa oklar 2, 4, 6 arasında zıplar. `value="2"` başlangıçta duran sayıdır. Ziyaretçi onu değiştirirse giden, başlangıç değil, kutuda kalan sayıdır.

## Tarih, takvimden seçilir

`type="date"` bir gün ister. `type="time"` bir saat ister. Gün, yıl-ay-gün sırasıyla paketlenir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Günün notu</title>
  </head>
  <body>
    <h1>Van’a bakış</h1>
    <form action="tarih.html" method="get">
      <p>
        Gün
        <input type="date" name="gun" value="2026-10-01" />
      </p>
      <p>
        Saat
        <input type="time" name="saat" value="09:30" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Gün” yanında bir tarih kutusu vardır. Türkçe bir tarayıcıda 01.10.2026 veya 1 Ekim 2026 gibi, yerel biçimle görünür. Kutunun içinde bir takvim simgesi bulunur. Simge tıklanınca küçük bir takvim açılır. Bir gün seçilince kutu o günü gösterir. “Saat” yanında 09:30 yazar. Bazı tarayıcılarda saat ve dakika ayrı bölmelerdir, oklarla artar. Dosya gönderilince adres `gun=2026-10-01&saat=09%3A30` biçimine benzer. `%3A`, iki noktadır. Ekranda gün yerelde görünse de adreste sıra yıl, ay, gündür. Ayın önce yazıldığı bir Amerikan kısaltması adres çubuğuna konmaz.

`value` da aynı sırayı kullanır. `value="01-10-2026"` çoğu tarayıcıda boş bir kutu bırakır. Gün seçilmemiş sayılır. `min="2026-10-01"` ve `max="2026-10-31"` yazılırsa takvim, ekim dışındaki günleri seçtirmeyebilir. Sınır, o aya ait bir not için konur. Sınır yoksa herhangi bir gün seçilir.

`type="month"` yıl ve ay, `type="datetime-local"` hem gün hem saat ister. Bu rehberdeki kent notu için gün ve saat ayrı durur. İkisi de tek kutuda karışmaz.

## Dosya, belgenin yanına konacak fotoğrafı seçtirir

`type="file"` bir dosya seçme penceresi açar. Seçilen fotoğraf, `get` adresinin içine konmaz. Dosya göndermek `method="post"` ve `enctype="multipart/form-data"` ister.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Fotoğraf seçimi</title>
  </head>
  <body>
    <h1>İzmir fotoğrafı</h1>
    <form action="dosya.html" method="post" enctype="multipart/form-data">
      <p>
        Fotoğraf
        <input type="file" name="foto" accept="image/*" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Fotoğraf” yanında tarayıcının kendi düğmesi vardır. Türkçe arayüzde düğme çoğu zaman “Dosya seçin” diye okunur. İngilizce arayüzde “Choose File” yazar. Düğmenin yanında, henüz seçim yoksa “Dosya seçilmedi” benzeri bir not durur. Düğme tıklanınca işletim sisteminin dosya penceresi açılır. Bir resim seçilince pencere kapanır. Düğmenin yanında o dosyanın adı görünür. Sayfada fotoğrafın kendisi hemen çizilmez. Yalnızca adı durur. 11. gündeki `<img>` ile bu kutu aynı işi yapmaz. `<img>` sayfada duran resmi gösterir. Dosya alanı, gönderilecek dosyayı seçtirir.

`accept="image/*"` pencereyi resimlere yöneltir. Başka türler bütünüyle yasaklanmayabilir. İşletim sistemi yine de bir metin dosyası seçtirmeye izin verebilir. Bu özellik bir ipucudur. `multiple` eklenirse birden çok dosya seçilebilir. O özellik 22. günde boolean özellik olarak da anılır. Bugün tek fotoğraf yeter.

“Gönder” basılınca, sayfa dosyadan `file:///` ile açılmışsa, 15. günde anlatılan post uyarısı yeniden çıkar. Fotoğraf bir sunucuya gitmez. Dosya adının düğmenin yanında belirmesi, bu günün gözlenen sonucudur. Adres çubuğunda fotoğrafın adı `?foto=` diye durmaz. Dosya, sorgu cümlesine sığmaz. `method` yanlışlıkla `get` bırakılırsa tarayıcı dosyayı bu biçimde gönderemez. Yalnızca dosyanın adından ibaret bir diziyi yola ekleyebilir veya alanı boş bırakır. Fotoğrafın kendisi gitmez.

## Sık yapılan hata

Tarihi düz metin kutusuna `01.10.2026` diye yazdırmak, paketlerin her birinde başka bir biçim üretir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Düzgün olmayan gün</title>
  </head>
  <body>
    <h1>Gün kutusu</h1>
    <form action="metin-gun.html" method="get">
      <p>
        Gün
        <input type="text" name="gun" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Sıradan bir yazı kutusu açılır. Takvim simgesi yoktur. `1 Ekim`, `01/10/2026` veya `2026-10-01` hepsi uyarısız gider. Üçü de `gun` adıyla adrese düşer. Hangisinin gün, hangisinin ay olduğu belirsiz kalır.

Doğru belgede gün, tarih alanındadır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Takvim</title>
  </head>
  <body>
    <h1>Gün kutusu</h1>
    <form action="takvim.html" method="get">
      <p>
        Gün
        <input type="date" name="gun" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Takvimden bir gün seçilip gönderilince adres `gun=2026-10-01` gibi, yıl-ay-gün sırasıyla biter. Nokta ile ayrılmış bir gün metni kutuda beklenmez.

İkinci hata, sayı alanına `min` ve `max` koyup harfin yine de adrese gideceğini unutmaktır. Bazı eski tarayıcılar `type="number"` kutusunu düz metin gibi gösterir. Harf yazılırsa güncel bir tarayıcı gönderimi keser. Kesilmezse sunucu tarafı olmadığı için değer olduğu gibi adreste görünür. Deneme güncel bir tarayıcıda yapılır. `aaa` gönderilmez.

Üçüncü hata, dosya alanını `get` formunun içinde bırakmaktır. Ekranda düğme yine durur. Seçilen fotoğraf sayfada da görünür, adreste de görünmez. Dosya alanı `post` formunda ve `multipart/form-data` ile durur.

## Egzersizler

1. Kişi sayısı 1 ile 6 arasında, birer birer artsın. Sayfa açıldığında kutuda 2 görünsün. Oklarla 7 yazılamasın. 4 gönderilince adres `kisi=4` olsun.
2. Bir gün alanı ve bir saat alanı kurun. Takvimden 1 Ekim 2026, saatten 09:30 seçin. Adreste gün `2026-10-01` sırasıyla, saat ise `09:30` değeriyle dursun.
3. Bir dosya alanı koyun. Türkçe tarayıcıdaysa düğmede “Dosya seçin” veya buna yakın bir yazı görünsün. Bir resim seçin. Düğmenin yanında dosyanın adı belirsın. Fotoğrafın kendisi bu sayfada `<img>` gibi çizilmesin. Formun yöntemi `post` olsun.

[← Önceki gün](../17-select-checkbox-radio/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../19-button-label/ders.md)
