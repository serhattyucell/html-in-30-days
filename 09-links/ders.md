# 9. Gün — Bağlantılar (Links)

Bu gün, bir yazıyı başka bir adrese bağlar. 8. güne kadar bütün belge tek sayfaydı. Bağlantı, o sayfadan çıkıp başka bir dosyaya, başka bir siteye veya bir posta programına giden yolu metnin içine koyar.

## Başka bir sayfaya giden yazı

`<a>` etiketi, bir metni tıklanabilir yapar. `href` özelliği, tıklanınca açılacak adresi taşır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dış bağlantı</title>
  </head>
  <body>
    <h1>İstanbul notu</h1>
    <p>
      Adres örneklerinin durduğu site
      <a href="https://example.com">Example Domain</a>
      sayfasındadır.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul notu” büyük başlıktır. Paragraf normal puntoda akar. “Example Domain” sözü, cümlenin içinde, çoğu tarayıcıda mavi ve altı çizili durur. Diğer kelimeler siyah ve çizgisizdir. Fare bu sözün üzerine gelince işaret parmağa dönüşür. Tıklanınca bu dosya kapanır ya da aynı sekmede değişir. Açılan sayfada “Example Domain” başlığı ve bu adresin örnekler için ayrıldığını söyleyen kısa bir İngilizce paragraf vardır. Adres çubuğunda `https://example.com` yazar. Mavi ve alt çizgi, ziyaret edilmemiş bağlantının tarayıcıdaki varsayılan görünüşüdür. Daha önce açılmış bir bağlantı mora dönebilir. Rengi seçmek ileride CSS konusudur.

Bağlantının görünen sözü, varılacak yeri söyler. “tıkla”, “buraya” veya “link” yazılmaz. “Example Domain” okununca gidilecek sayfanın adı bellidir. `href` içindeki adres tamdır. `https://` ile başlar. Bu parçayı silip yalnızca `example.com` yazılırsa tarayıcı onu başka bir sitenin adresi değil, aynı klasördeki bir dosyanın adı sanır.

## Aynı klasördeki dosya

İki HTML dosyası aynı klasördeyse adres, dosyanın adıdır. Site adı yazılmaz.

Birinci dosya `istanbul.html` adıyla kaydedilir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İstanbul</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <p>Boğaz bu sayfadadır. Karşı not ayrı dosyadadır.</p>
    <p><a href="izmir.html">İzmir sayfasına geç</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
`istanbul.html` tek başına açıldığında sekmede “İstanbul” yazar. Sayfada büyük başlık “İstanbul”, altında “Boğaz bu sayfadadır. Karşı not ayrı dosyadadır.” cümlesi ve mavi, altı çizili “İzmir sayfasına geç” vardır. `izmir.html` henüz yoksa bu bağlantı tıklanınca tarayıcı dosyayı bulamaz.

İkinci dosya, aynı klasöre `izmir.html` adıyla kaydedilir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İzmir</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Saat Kulesi bu sayfadadır.</p>
    <p><a href="istanbul.html">İstanbul sayfasına dön</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
`istanbul.html` açıldığında büyük başlık “İstanbul”, altında bir paragraf ve altı çizili “İzmir sayfasına geç” yazar. Bu söz tıklanınca sekme değişir. Büyük başlık “İzmir” olur. Altında “Saat Kulesi bu sayfadadır.” cümlesi ve “İstanbul sayfasına dön” bağlantısı durur. Dönüş tıklanınca yeniden İstanbul sayfası gelir. Adres çubuğunda, dosya yolunun sonunda bir sefer `istanbul.html`, bir sefer `izmir.html` okunur.

İki dosya ayrı klasörlere konursa yalnızca ad yetmez. Tarayıcı, bağlantının bulunduğu dosyanın klasörüne bakar. Hedef bir üst klasördeyse adres `../izmir.html` gibi yazılır. Bu derslerin altındaki önceki gün bağlantısı da aynı biçimde çalışır. Bugünün denemesinde iki dosya aynı klasörde tutulur. Böylece adres yalnızca dosya adıdır.

## Posta ve yeni sekme

`mailto:` ile başlayan bir adres, tarayıcıyı başka bir siteye götürmez. Bilgisayarda tanımlı bir posta programını açmaya çalışır. `target="_blank"` ise bir web sayfasını yeni sekmede açar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yazışma ve yeni sekme</title>
  </head>
  <body>
    <h1>Serhat'ın notu</h1>
    <p>
      Örnek bir yazışma adresi:
      <a href="mailto:serhat@example.com">serhat@example.com</a>
    </p>
    <p>
      Örnek siteyi açık notun yanında tutmak için
      <a href="https://example.com" target="_blank" rel="noopener">Example Domain yeni sekmede</a>
      açılır.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
İki altı çizili bağlantı vardır. Birincisi “serhat@example.com” diye okunur. Tıklanınca kent sayfası değişmez. Bilgisayarda bir posta programı varsa yeni bir ileti penceresi açılır ve alıcı kısmında `serhat@example.com` durur. Posta programı yoksa tarayıcı hiçbir sayfa açmayabilir veya kısacık bir uyarı gösterebilir. Bu adres gerçek bir posta kutusu değildir. `example.com`, örnekler için ayrılmış bir alan adıdır. İleti gönderilmez.

İkinci bağlantının yazısı “Example Domain yeni sekmede”dir. Tıklanınca İstanbul veya not sayfası yerinde kalır. Yanında yeni bir sekme açılır ve o sekmede Example Domain sayfası durur. `rel="noopener"` ekranda bir kelime olarak görünmez. Yeni sekmedeki sayfanın, geride kalan nota komut geçirmesini engelleyen bir güvenlik bağıdır. Yeni sekme istenmiyorsa `target` ve `rel` satırdan çıkarılır. Bağlantı o zaman aynı sekmede açılır.

`tel:` ile başlayan bir adres de benzer biçimde telefon uygulamasını açmaya çalışır. Bu rehber gerçek bir numara kullanmaz. Uygulama açılınca örnek bir numara çevrilmez.

## Sık yapılan hata

`href` olmadan yazılmış bir `<a>`, sıradan metindir. Tıklanmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Adresi yok</title>
  </head>
  <body>
    <h1>Van</h1>
    <p><a>Van Gölü sayfası</a> bu hâliyle bir bağlantı değildir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü sayfası” mavi de değildir, altı çizili de değildir. Fare şekil değiştirmez. Tıklamak sayfayı değiştirmez. Etiket boş bir kutu olarak durur.

Doğru belgede adres vardır ve görünen söz yerini anlatır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Adresi var</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Ayrı dosya: <a href="van.html">Van Gölü sayfası</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van Gölü sayfası” altı çizili ve mavidir. `van.html` aynı klasörde yoksa tıklama, tarayıcının “dosya bulunamadı” sayfasını açar. Dosya bulununca o dosyanın başlığı görünür. Hata, `href="Van.html"` ile `van.html` adlı dosyanın harflerini karıştırmaktır. Birçok sistemde dosya adı büyük-küçük harfe duyarlıdır. Adres, kayıttaki adın aynısı olur.

İkinci hata, adresin içine boşluk koymaktır. `href="izmir notu.html"` tek bir adres olarak okunmaz. Dosya adı boşluksuz seçilir.

Üçüncü hata, bağlantının sözünü “buraya tıkla” yapmaktır. Söz mavi ve çizili görünür ama nereye gittiği cümle okununca anlaşılmaz. Sözün kendisi hedefi söyler.

## Egzersizler

1. Aynı klasöre `trabzon.html` ve `van.html` koyun. Trabzon sayfasında altı çizili “Van sayfasına geç” görünsün. Tıklanınca büyük başlık “Van” olsun. Van sayfasındaki bağlantı yeniden Trabzon sayfasını açsın.
2. Bir paragrafta “Example Domain” sözü aynı sekmede `https://example.com` adresini açsın. İkinci bir bağlantı aynı adresi yeni sekmede açsın. Birinci tıklamada notun sekmesi değişsin, ikinci tıklamada notun sekmesi yerinde kalsın.
3. `href` özelliğini silip sayfayı yenileyin. Metnin mavi ve çizili olmadığını, tıklamanın hiçbir dosya açmadığını görün. Özelliği geri koyun. Metin yine bağlantı gibi dursun.

[← Önceki gün](../08-nested-lists/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../10-fragment-links/ders.md)
