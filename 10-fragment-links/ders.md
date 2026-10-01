# 10. Gün — Sayfa içi bağlantı (Fragment Links)

Bu gün, uzun bir sayfanın içinde bir başlığa atlar. 9. gündeki bağlantı başka bir dosyayı açıyordu. Bugünkü bağlantı aynı dosyanın bir yerine gider. Uzun not, en üste bir içindekiler listesi koyunca okuyan kişi aradığı başlığa iner.

## Kimlik, varılacak yerin adıdır

`id` özelliği, sayfadaki bir etikete tek bir ad verir. Bağlantının adresi `#` ile o adı gösterirse tarayıcı o etiketin bulunduğu yere kayar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notunun içi</title>
  </head>
  <body>
    <h1>Dört kent</h1>
    <ul>
      <li><a href="#istanbul">İstanbul bölümüne in</a></li>
      <li><a href="#van">Van bölümüne in</a></li>
    </ul>
    <h2 id="istanbul">İstanbul</h2>
    <p>Boğaz, kenti iki yakaya böler. Galata Kulesi bir yakada yükselir. Bu paragraf, atlanan yeri ekranda tutmak için uzundur. İçindekiler yukarıda kaldı.</p>
    <p>Karşı kıyı aynı kentin parçasıdır. Sayfa kaydırılınca bu satırlar görünür.</p>
    <h2 id="van">Van</h2>
    <p>Van Gölü geniştir. Kale, gölün kıyısındaki kente bakar.</p>
    <p><a href="#istanbul">İstanbul bölümüne dön</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa açılınca en üstte “Dört kent” başlığı ve iki bağlantı vardır: “İstanbul bölümüne in” ve “Van bölümüne in”. İkisi de mavi ve altı çizilidir. “İstanbul” ve “Van” başlıkları da sayfanın aşağısında, kendi paragraflarıyla durur. `id` değerleri ekranda yazı olarak görünmez. Başlığın yanında “#istanbul” yazmaz.

“Van bölümüne in” tıklanınca sayfa aşağı kayar. “Van” başlığı pencerenin üst tarafına gelir. “Dört kent” başlığı görünmez olabilir. Adres çubuğunun sonunda `#van` belirir. “İstanbul bölümüne dön” tıklanınca sayfa yeniden yukarı, “İstanbul” başlığına kayar. Adresin sonu `#istanbul` olur. Dosya değişmez. Sekmede hâlâ “Kent notunun içi” yazar.

Pencere çok uzunsa ve bütün sayfa zaten sığıyorsa kaydırma fark edilmeyebilir. O zaman pencere daraltılır veya örnek paragraflar uzatılır. Amaç, tıklanınca hedefin yukarı taşınmasıdır.

Kimlik kısa, küçük harfli ve boşluksuz yazılır. Türkçe harf yerine `istanbul`, `izmir`, `trabzon`, `van` gibi sade adlar seçilir. Aynı `id` sayfada ikinci kez kullanılmaz. Tarayıcı, kopya bir ad görürse ilkine gider. İkincisi hiç yokmuş gibi kalır.

## Başka dosyanın bir yerine inmek

Dosya adı ile `#` birleşince hem sayfa değişir hem de o sayfanın bir başlığına inilir.

`duraklar.html` şöyle kaydedilir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Duraklar</title>
  </head>
  <body>
    <h1>Duraklar</h1>
    <h2 id="izmir">İzmir</h2>
    <p>Saat Kulesi ve Kordon bu bölümde toplanır.</p>
    <h2 id="trabzon">Trabzon</h2>
    <p>Karadeniz kıyısı bu bölümde toplanır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
`duraklar.html` doğrudan açıldığında sayfa en üstten başlar. Büyük başlık “Duraklar”dır. Altında “İzmir”, sonra onun paragrafı, sonra “Trabzon” ve onun paragrafı alt alta durur. Kimlikler ekranda yazı olarak görünmez. Sayfa henüz bir yere kaymaz çünkü adresin sonunda `#` yoktur.

Çağıran dosya, aynı klasörde `baslangic.html` adıyla durur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başlangıç</title>
  </head>
  <body>
    <h1>Başlangıç</h1>
    <p><a href="duraklar.html#trabzon">Trabzon durağına git</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
`baslangic.html` açıldığında yalnızca “Başlangıç” başlığı ve bir bağlantı vardır. Bağlantı tıklanınca sekme `duraklar.html` dosyasına geçer. Adresin sonunda `#trabzon` durur. Pencere, “Trabzon” başlığını üste alacak biçimde açılır. “İzmir” bölümü, sayfanın kaydırma çubuğu yukarı alınmazsa görünmeyebilir. “Duraklar” ana başlığı hedefin üstünde kaldığı için küçük bir pencerede ekranın dışında kalabilir.

Yalnızca `duraklar.html` yazılırsa dosya en üstten, “Duraklar” başlığından açılır. `#` ve ad, inilecek yeri ekler. Ad, hedef dosyada `id` olarak yoksa dosya yine açılır ama kaydırma olmaz. Tarayıcı en üstte kalır.

## Sayfanın en üstüne dönmek

Belgenin en üstü için özel bir parçacık vardır. Adres yalnız `#` olursa tarayıcı sayfayı en başa alır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başa dön</title>
  </head>
  <body>
    <h1 id="bas">Van notu</h1>
    <p>Göl geniştir. Bu satırlar, alta inildiğinde başın görünmemesi için sayfayı uzatır.</p>
    <h2 id="kale">Van Kalesi</h2>
    <p>Kale tepeden bakar.</p>
    <p><a href="#bas">Notun başına dön</a></p>
    <p><a href="#">Sayfanın en üstü</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa uzunsa alta inince “Van Kalesi” görünür, “Van notu” kaybolur. “Notun başına dön” tıklanınca `id="bas"` konmuş başlık üste gelir. “Sayfanın en üstü” tıklanınca da belge en başa kayar. İkisi bu kısa örnekte aynı yere gidebilir. Başlığın üstünde başka bir şey yoksa fark görünmez. Bir içindekiler listesi `<h1>` satırından önce duruyorsa `#` listenin de üstüne çıkar. `#bas` ise doğrudan başlıkta durur.

## Sık yapılan hata

`#` işaretini unutmak, tarayıcıyı aynı sayfanın bir yerine değil, o adı taşıyan bir dosyaya yollar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İşaretsiz adres</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p><a href="kordon">Kordon bölümü</a></p>
    <h2 id="kordon">Kordon</h2>
    <p>Kıyı boyunca yürünür.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Kordon bölümü” mavi ve çizilidir. Tıklanınca sayfa “Kordon” başlığına kaymaz. Tarayıcı, klasörde `kordon` adlı bir dosya arar. Dosya yoksa “bulunamadı” sayfası gelir. `id="kordon"` kaynakta durduğu hâlde hedef olmamıştır.

Doğru adres `#kordon` biçimindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İşaretli adres</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p><a href="#kordon">Kordon bölümü</a></p>
    <h2 id="kordon">Kordon</h2>
    <p>Kıyı boyunca yürünür.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Tıklanınca sayfa “Kordon” başlığına kayar. Adres çubuğunun sonunda `#kordon` vardır. Dosya adı değişmez.

İkinci hata, iki başlığa aynı `id` değerini vermektir. İkisi de `id="kent"` ise bağlantı her zaman birincisinde durur. İkinci başlık, kendi sözü tıklansa bile üste gelmez. Her hedefe ayrı ad verilir: `istanbul`, `izmir`, `trabzon`, `van`.

Üçüncü hata, `id` içine boşluk yazmaktır. `id="van golu"` geçersiz bir addır. Ad `van-golu` gibi tireyle yazılır. Bağlantı da aynı tireyi kullanır.

## Egzersizler

1. Tek sayfada üç `<h2>` kurun: İstanbul, Trabzon, Van. En üstte üç bağlantı olsun. Her bağlantı kendi başlığına indirsin. Van tıklanınca adres çubuğunun sonunda `#van` görünsün. Başlıklar ekranda hizalansın, `id` değerleri yazı olarak görünmesin.
2. `notlar.html` ve `giris.html` adlı iki dosya kurun. Girişteki bağlantı, notlar dosyasındaki Trabzon başlığını üste getirsin. Dosya değişsin ve sayfa en üstteki ana başlıkta değil, Trabzon bölümünde açılsın.
3. `#` işaretini kaldırıp tıklayın. Tarayıcı bir dosya arasın ve başlığa kaymasın. İşareti geri koyun. Aynı tıklama, sayfa değişmeden ilgili başlığı üste alsın.

[← Önceki gün](../09-links/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../11-images/ders.md)
