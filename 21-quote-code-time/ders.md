# 21. Gün — Alıntı, kod, zaman (Quote, Code, Time)

Bu gün, başka bir yerden alınmış sözü, bir kod parçasını ve bir tarihi normal paragraftan ayırır. 20. günde bölgeler konunun sayfadaki yerini söylüyordu. Bugünkü etiketler, bir cümlenin türünü söyler. Uzun bir alıntı girintilenir. Kod, eşit aralıklı harflerle durur. Tarih, gözle normal yazı gibi görünse de makinenin okuyacağı bir gün taşır.

## Uzun söz girintilenir, kısa söz tırnak ister

`<blockquote>`, başka bir kaynaktan alınmış, kendi paragrafını hak eden sözü taşır. `cite` özelliği, sözün adresini saklar ve ekranda yazı olarak durmaz. `<q>` ise cümlenin içindeki kısa sözü işaretler. `<cite>` de eserin veya kaynağın adını taşır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Alıntı</title>
  </head>
  <body>
    <h1>İstanbul notundan</h1>
    <p>Serhat’ın kısa notu bir cümleye sığar.</p>
    <blockquote cite="https://example.com">
      <p>Boğaz, iki yakayı aynı kentin içinde tutar.</p>
    </blockquote>
    <p>
      Notun sıkıştırılmış hâli şudur:
      <q>Boğaz aynı kentin içindedir.</q>
    </p>
    <p>
      Kaynak adı:
      <cite>Serhat’ın kent notları</cite>
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul notundan” büyük başlıktır. İlk paragraf soldan, normal bir cümledir. Altındaki “Boğaz, iki yakayı aynı kentin içinde tutar.” cümlesi sağa doğru içeri girintilidir. Bu girinti, uzun alıntının varsayılan görünüşüdür. Çerçeve ve tırnak, uzun alıntının çevresine otomatik çizilmez. Kısa sözün çevresinde ise tarayıcı tırnak işaretleri koyar. “Boğaz aynı kentin içindedir.” cümlesi, paragrafın içinde, tırnaklar arasında durur. Tırnağın biçimi dile göre değişebilir. `lang="tr"` olan bir sayfada Türkçe tırnak da çıkabilir. “Serhat’ın kent notları” çoğu tarayıcıda italik durur. Bu, kaynak adıdır. Uzun alıntının içindeki cümle italik olmak zorunda değildir. `cite="https://example.com"` adres çubuğuna veya sayfaya yazı olarak düşmez. Sözün nereden geldiğini kaynakta tutar.

Alıntı, önemli olduğu için `<strong>` ile boyanmaz. Başkasının cümlesi olduğu için `<blockquote>` veya `<q>` olur. Vurgu, alıntının içinde tek bir kelimeyi ayırmak için ayrıca kullanılabilir.

## Kod, eşit aralıklı harf ister

`<code>`, bir etiketin veya dosya adının kendisini normal cümleden ayırır. `<pre>`, boşlukları ve satır sonlarını olduğu gibi bırakır. 4. günde paragraf bu boşlukları siliyordu. Kod örneği silinirse okunmaz. `<kbd>` bir tuşun adını, `<samp>` de programın ekrana bastığı örneği taşır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kod ve tuş</title>
  </head>
  <body>
    <h1>Dosya nasıl açılır</h1>
    <p>
      Belge <code>van.html</code> adıyla kaydedilir.
    </p>
    <pre><code>&lt;h1&gt;Van&lt;/h1&gt;
&lt;p&gt;Göl geniştir.&lt;/p&gt;</code></pre>
    <p>
      Sayfayı yenilemek için
      <kbd>F5</kbd>
      tuşuna basılır.
    </p>
    <p>
      Dosya yoksa tarayıcı şöyle bir sonuç da yazabilir:
      <samp>Dosya bulunamadı</samp>
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“van.html” cümlenin içinde, çoğu tarayıcıda eşit aralıklı bir yazı tipiyle durur. Çevresindeki “Belge” ve “adıyla kaydedilir” normal yazı tipindedir. Altında iki satırlık bir blok vardır. Birinci satır `<h1>Van</h1>` gibi okunur. İkinci satır `<p>Göl geniştir.</p>` diye onun tam altında, sol boşlukları korunarak durur. Kaynakta bu iki satır arasında Enter vardır ve ekranda da alt alta dururlar. 4. gündeki paragraf olsaydı iki satır tek cümleye yapışırdı.

Kaynakta `<` yerine `&lt;`, `>` yerine `&gt;` yazılır. Bunlar karakter karşılıklarıdır. Böyle yazılmazsa tarayıcı `<h1>` ifadesini örnek diye değil, gerçek bir başlık diye açar. Ekranda “Van” büyük bir başlık olur, kod kaybolur. `&lt;` yazılınca ziyaretçi etiket işaretlerini görür. Sayfada gerçek bir ikinci başlık açılmaz.

“F5” çoğu tarayıcıda yine eşit aralıklı ve sınırları belli bir kısa parça olarak durur. “Dosya bulunamadı” da eşit aralıklı örnek çıktıdır. İkisi de mavi bağlantı değildir. Tuş ile çıktı aynı puntoda görünebilir. Ayrım etikettedir. Biri basılan tuş, öteki görülen mesajdır.

## Zaman, hem okunur hem sıralanır

`<time>`, bir günü veya saati insan cümlesinden ayırır. `datetime` özelliği, makinenin okuduğu biçimi taşır. Etiketin arasındaki yazı, insanın okuduğu biçimdir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Notun günü</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <p>
      Not,
      <time datetime="2026-10-01">1 Ekim 2026</time>
      günü güncellendi. Bakış saati
      <time datetime="09:30">09.30</time>
      olarak yazıldı.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Cümle normal bir paragraftır. “1 Ekim 2026” kalın değildir, çerçeve içinde değildir, bağlantı da değildir. “09.30” da aynı puntodadır. İki parça, cümlenin içinde sıradan söz gibi durur. `datetime` değerleri ekranda görünmez. Kaynakta gün `2026-10-01`, saat `09:30` diye durur. 18. gündeki tarih alanının gönderdiği biçim ile aynı sıradır. Ziyaretçi “1 Ekim 2026” okur. Bir takvim aracı ise `2026-10-01` değerini alır. İkisi birden yazılır. Yalnızca “geçen perşembe” denirse araç bir gün seçemez. Yalnızca `2026-10-01` ekrana basılırsa okuyan kişi yıl-ay-gün düzenini her seferinde çözmek zorunda kalır.

`<time>` bir tarih alanı değildir. Kutuya tıklanıp takvim açılmaz. O iş 18. gündeki `<input type="date">` ile yapılır. Bugünkü etiket, bitmiş bir notun içindeki günü işaretler.

## Sık yapılan hata

Kod örneğindeki küçüktür işaretini düz yazmak, örneği gerçek etikete çevirir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaçan kod</title>
  </head>
  <body>
    <h1>Örnek sanılan başlık</h1>
    <pre><code><h2>İzmir</h2></code></pre>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfada iki başlık vardır. Biri “Örnek sanılan başlık”, öteki ondan küçük “İzmir”dir. Eşit aralıklı `<h2>İzmir</h2>` satırı görünmez. Tarayıcı, örnek diye yazılan etiketi açılış sanır ve onu gerçek bir başlık yapar. Kapanışlar da karışabilir.

Doğru belgede işaretler karşılıklarıyla yazılır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kalan kod</title>
  </head>
  <body>
    <h1>Örnek olarak duran başlık</h1>
    <pre><code>&lt;h2&gt;İzmir&lt;/h2&gt;</code></pre>
  </body>
</html>
```

Tarayıcıda görünen:
Büyük başlık “Örnek olarak duran başlık”tır. Altında, eşit aralıklı bir satır olarak `<h2>İzmir</h2>` okunur. “İzmir” ikinci bir başlık gibi büyümez.

İkinci hata, kısa sözü normal tırnakla yazıp `<q>` sanmaktır. Ekranda tırnak yine görünür. Kaynak, sözün bir alıntı olduğunu söylemez. Tırnağı tarayıcı koysun diye söz `<q>` içine alınır. El ile bir tırnak daha eklenirse ekranda çift tırnak birikir.

Üçüncü hata, `datetime` içine “1 Ekim 2026” yazmaktır. Özellik, `2026-10-01` gibi sıralı bir değer ister. Okunan cümle, etiketin arasında kalır.

## Egzersizler

1. Bir uzun alıntı girintili, bir kısa söz tırnak içinde görünsün. Kaynak adı italik dursun. Uzun alıntının `cite` adresi ekranda yazı olarak belirmesin.
2. `van.html` dosya adı cümlenin içinde eşit aralıklı görünsün. Altında iki satırlık bir kod örneği, kaynakta yazıldığı gibi alt alta dursun. Örnekteki `<p>` gerçek paragraf açmasın. Ekranda etiket işaretleri görünsün.
3. Paragrafta “1 Ekim 2026” normal yazı olarak okunsun. Kaynakta aynı yerin `datetime` değeri `2026-10-01` olsun. Bu parça bir tarih kutusu gibi takvim açmasın.

[← Önceki gün](../20-semantic-layout/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../22-attributes/ders.md)
