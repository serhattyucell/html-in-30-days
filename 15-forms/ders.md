# 15. Gün — Form iskeleti (Forms)

Bu gün, ziyaretçinin dolduracağı bir alanı sayfaya koyar ve o alanın tarayıcıda nereye gideceğini kurar. 14. güne kadar sayfa yalnızca okunuyordu. Form, yazılan bir kelimeyi bir adla paketler. Bu rehberde paketi alacak bir sunucu yoktur. Görülen sonuç, adres çubuğuna eklenen sorgu ya da sunucusuz dosyanın duruşudur.

## Form, alanları bir gönderime bağlar

`<form>` etiketi, içindeki alanları tek bir gönderim yapar. `action`, gönderimin hangi adrese gideceğini söyler. `method`, paketin nasıl taşınacağını söyler.

`method="get"` paketi adresin sonuna ekler. Sayfa yenilenir ve yazılan kelime adres çubuğunda görünür. Aşağıdaki belge `get-form.html` adıyla kaydedilip tarayıcıda açılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Get formu</title>
  </head>
  <body>
    <h1>Kent sorusu</h1>
    <p>Kutuya bir kent adı yazılıp düğmeye basılınca adres çubuğu değişir.</p>
    <form action="get-form.html" method="get">
      <p>
        Kent adı
        <input type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent sorusu” başlığının altında bir açıklama vardır. Sonra “Kent adı” yazısının yanında boş, tek satırlık beyaz bir kutu durur. Kutunun altında “Gönder” yazılı bir düğme vardır. Düğmenin rengi ve köşesi tarayıcıya aittir. Kenarlık ileride CSS konusudur. Kutunun içine `Van` yazılıp düğmeye basılınca sayfa yeniden yüklenir. Başlık ve boş kutu geri gelir. Kutudaki “Van” silinmiş olabilir. Asıl sonuç adres çubuğundadır. Dosya yolunun sonunda `?kent=Van` görünür. `kent`, alanın adıdır. `Van`, yazılan değerdir. İkisi `=` ile birleşir. Soru işareti, adresin bittiğini ve paketin başladığını söyler.

Kutunun türleri 16. günde, düğmenin türleri 19. günde açılır. Bugün bu ikisi, formun çalıştığını gözle görmek için iskelete konur. `name` yazılmazsa adresin sonunda `?kent=Van` oluşmaz. Yalnızca `?` veya hiçbir ek görünür. Paket, adsız alanı taşımaz.

`action` boş bırakılırsa veya hiç yazılmazsa gönderim, şu an açık olan dosyanın adresine gider. Sonuç yine aynı dosyanın yenilenmesi ve adresin sonuna eklenen sorgu olur. Başka bir dosya adı yazılırsa o dosya açılır ve sorgu onun adresine eklenir. `action="https://example.com"` yazılırsa tarayıcı bu bilgisayardaki dosyadan çıkıp o siteye gider. Example Domain bir form alıcısı değildir. Sitenin kendi sayfası açılır. Kent adı orada işlenmez.

## Post, adresi değiştirmez

`method="post"` paketi adres çubuğuna yazmaz. Paket, isteğin gövdesinde gider. Gövdeyi kabul edecek bir program bu repoda yoktur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Post formu</title>
  </head>
  <body>
    <h1>İleti denemesi</h1>
    <form action="post-form.html" method="post">
      <p>
        Kısa not
        <input type="text" name="not" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Yine bir kutu ve “Gönder” düğmesi vardır. Kutuya `İzmir` yazılıp düğmeye basılınca adres çubuğunda `?not=İzmir` belirmez. Dosya `file:///` yoluyla açıksa tarayıcı, aynı dosyaya bir gövde göndermeye çalışır ve çoğu zaman uyarı verir ya da sayfayı olduğu gibi bırakır. Bir sunucu olmadığı için “ileti yollandı” diye bir sonuç sayfası açılmaz. Bu bir bozuk belgedir anlamına gelmez. `post`, alıcısı olan bir adreste kullanılır. Alıcı yokken paketin adres çubuğunda görünmesi isteniyorsa `get` seçilir.

Kent notundaki arama ve sıralama denemeleri `get` ile yapılır. Yazılan kelime adres çubuğunda kaldığı için yenilemek, sonucu sürdürmek ve linki kopyalamak kolaydır. `post`, adresin içine sığmaması gereken uzun bir ileti içindir. Bu günün geri kalan denemeleri `get` ile kalır.

## İki alan, tek sorgu

Aynı formun içindeki bütün adlı alanlar tek gönderimde birleşir. Alanların arası adreste `&` ile ayrılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki alan</title>
  </head>
  <body>
    <h1>Durak sorusu</h1>
    <form action="iki-alan.html" method="get">
      <p>
        Ad
        <input type="text" name="ad" value="Serhat" />
      </p>
      <p>
        Kent
        <input type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
İki kutu alt alta durur. “Ad” kutusunun içinde, daha yazılmadan, “Serhat” vardır. `value` başlangıçta kutuya konan metindir. “Kent” kutusu boştur. Kente `Trabzon` yazılıp düğmeye basılınca adres şöyle biter: `?ad=Serhat&kent=Trabzon`. Sıra, alanların formdaki sırasıdır. “Serhat” değiştirilip `Van` notu gibi başka bir kelime yazılırsa adres, kutuda duran yeni kelimeyi taşır. İkinci kutu boş gönderilirse `kent=` ifadesinin sağında hiçbir harf durmaz. Alan yine listede vardır. Değeri boştur.

Türkçe harfler adreste `%C4%B0` gibi yüzde koduna dönüşebilir. `İzmir` yazılınca adres çubuğunda kelimenin kendisi ya da onun kodu görünür. İkisi de aynı değerdir. Tarayıcı, boşluk karakterini de `+` veya `%20` yapabilir. Kutu, ekranda yine düzgün “İzmir” gösterebilir. Kod, adresin yazım kuralıdır. 2. gündeki UTF-8 satırı yerindeyse sayfanın kendisindeki Türkçe bozulmaz.

## Sık yapılan hata

Alanı formun dışında bırakmak, o alanı gönderimin dışında bırakır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dışarıda kalan kutu</title>
  </head>
  <body>
    <h1>Kopuk kutu</h1>
    <p>
      Kent
      <input type="text" name="kent" />
    </p>
    <form action="kopuk.html" method="get">
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Kutu ve düğme ekranda alt alta durduğu için ikisi de aynı forma aitmiş gibi görünür. Kutuya `Van` yazılıp düğmeye basılınca adresin sonunda `kent=Van` yoktur. Düğme, yalnızca kendi `<form>` içindeki alanları taşır. Dışarıdaki kutu yazıyla orada kalır. Gönderim onu görmez.

Doğru belgede kutu, form kapanmadan önce durur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İçeride kalan kutu</title>
  </head>
  <body>
    <h1>Bağlı kutu</h1>
    <form action="bagli.html" method="get">
      <p>
        Kent
        <input type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
`Van` yazılıp düğmeye basılınca adres `?kent=Van` ile biter. Kutu ile düğme aynı formun içindedir.

İkinci hata, iki alana aynı `name` değerini vermektir. İkisi de `name="kent"` ise adreste tek bir `kent` kalabilir veya ilki ikincisiyle çakışır. Ad kutusu `ad`, kent kutusu `kent` olur.

Üçüncü hata, `post` ile açılmış bir dosyada “adres değişmedi, form çalışmadı” sanmaktır. Adres çubuğu `post` için günlük değildir. Deneme `get` ile yapılırsa yazılan kelime orada görünür.

## Egzersizler

1. `form.html` içinde bir kutu ve bir “Gönder” düğmesi kurun. Kutunun adı `kent` olsun. `İzmir` yazılıp gönderilince adres çubuğunda `kent=İzmir` görünsün. Sayfa bir sonuç cümlesi basmasın. Sonuç adresin kendisi olsun.
2. İkinci bir kutu ekleyin. Adı `ad`, başlangıç metni “Serhat” olsun. Gönderilince adres hem `ad` hem `kent` değerini, ikisinin arasında `&` ile taşısın.
3. Kutu `form` etiketinin dışında kalsın, düğme içinde kalsın. Gönderince `kent` adreste yer almasın. Kutuyu formun içine alın. Aynı kelime yeniden `?kent=` ifadesinin sağında görünsün.

[← Önceki gün](../14-table-head/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../16-text-inputs/ders.md)
