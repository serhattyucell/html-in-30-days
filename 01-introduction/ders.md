# 1. Gün — Giriş

Bu gün, HTML’in ne işe yaradığını ve ilk sayfanın nasıl açıldığını kurar. Henüz başlık düzeyleri, listeler veya formlar yoktur. Amaç, bir dosyayı kaydedip tarayıcıda görmek ve etiketlerin ekranda yazı olarak durmadığını ayırt etmektir.

## İşaretler ekranda gizlenir

HTML, tarayıcıya “bu parça başlıktır, şu parça paragraftır” demek için kullanılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Serhat'ın notu</title>
  </head>
  <body>
    <h1>İlk sayfa</h1>
    <p>Bu satır, tarayıcının etiketleri gizleyip yalnızca yazıyı gösterdiği ilk denemedir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmenin üzerinde “Serhat'ın notu” yazar. Sayfada, sayfanın geri kalanından büyük ve kalın bir satır olarak “İlk sayfa” durur. Onun altında, arada bir boşluk bırakılmış normal bir cümle vardır: “Bu satır, tarayıcının etiketleri gizleyip yalnızca yazıyı gösterdiği ilk denemedir.” `<h1>`, `<p>`, `<title>` gibi işaretler ekranda metin olarak görünmez. Kenar çizgisi, renkli kutu ve sütun da yoktur. Çerçeve ileride CSS konusudur.

Bir etiket, küçüktür-büyüktür işaretlerinin içine yazılmış addır. `<h1>` açılıştır, `</h1>` kapanıştır. İkisinin arasında duran yazı, o etiketin içeriğidir. `<title>` sekmenin adını taşır ve sayfa gövdesinde görünmez. `<h1>` sayfadaki ana başlıktır. `<p>` bir paragraf başlatır. Bu üç öğenin ayrıntısı sonraki günlerde açılır; bugün onları çalışır bir sayfanın parçası olarak görmek yeter.

## Dosyayı kaydetmek

Kaydedilen dosyanın adı, tarayıcının onu sayfa olarak tanımasını sağlar.

Metin düzenleyicide yeni bir dosya açılır, yukarıdaki belgenin tamamı yapıştırılır ve dosya `ilk-sayfa.html` adıyla kaydedilir. Uzantı `.html` olmalıdır. Adın içinde boşluk olmaz. Düzenleyici “düz metin” ve “UTF-8” seçenekleri sunuyorsa ikisi de seçilir. UTF-8, İ, ş, ğ, ü, ö, ç harflerinin dosyada bozulmadan durmasını sağlar. Karakterlerin ayrıntısı 2. gündedir.

Dosya masaüstünde, belgeler klasöründe ya da bu dersin yanında durabilir. Nerede durduğu, sonraki gün iki dosya birbirine bağlanana kadar sonucu değiştirmez.

Kayıttan sonra dosya simgesine çift tıklanır. Açılmazsa dosya tarayıcı penceresinin üzerine sürüklenir. Üçüncü yol, tarayıcıda Dosya menüsünden Aç komutunu kullanmaktır. Adres çubuğunda `https://` ile başlayan bir site adresi değil, `file:///` ile başlayan bir dosya yolu görünür. Bu, sayfanın internette yayınlanmadığı, yalnızca bu bilgisayarda açıldığı anlamına gelir.

## Kaynak ile ekran aynı şey değildir

Tarayıcıda görünen sayfa, kaynaktaki satırların birebir kopyası değildir.

Aynı `ilk-sayfa.html` dosyası açıkken tarayıcının menüsünden “Sayfa kaynağını görüntüle” (İngilizce arayüzde View Page Source) seçilir. Kaynakta tüm etiketler, girintiler ve satır sonları durur. Sekmeye dönünce etiketler kaybolmuş, başlık büyümüş, paragraf alta inmiştir. Kaynak düzenlenip kaydedildikten sonra tarayıcıda sayfa yenilenir. Yenileme yapılmazsa ekranda eski hâli kalır.

Başka bir deneme, gövdedeki cümleyi değiştirmektir. Kaynak şöyle yazılır, dosya yeniden kaydedilir ve sayfa yenilenir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Van notu</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Bu klasördeki ilk sayfa Van için açıldı.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmenin yazısı “Van notu” olur. Sayfada büyük başlık “Van” yazar. Altında tek bir cümle durur: “Bu klasördeki ilk sayfa Van için açıldı.” Eski “İlk sayfa” yazısı, dosya kaydedilip sayfa yenilendiyse artık görünmez.

## Sık yapılan hata

Etiketler ekranda olduğu gibi yazıyla duruyorsa dosya yanlış türde kaydedilmiştir.

Hatalı kayıt, uzantıyı gizleyip dosyayı `ilk-sayfa.html.txt` yapmak ya da belgeyi Word belgesi olarak saklamaktır. Düz metin gibi açıldığında tarayıcı etiketleri yorumlamaz. Şu içerik bir `.txt` dosyasına konup tarayıcıda açılırsa işaretler komut olmaktan çıkar:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bozuk kayıt</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <p>Bu dosyanın uzantısı html değilse etiketler de yazı olarak kalır.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfada “İzmir” büyük bir başlık olarak durmaz. `<h1>`, `<p>` ve diğer işaretler de cümlelerin yanında, olduğu gibi yazı olarak okunur. Sekmede dosyanın adı görünebilir; `<title>` içindeki “Bozuk kayıt” sekme adı olmaz.

Doğrusu, aynı içeriği uzantısı gerçekten `.html` olan bir dosyaya kaydetmektir. Tarayıcı yeniden açıldığında “İzmir” başlık olur, etiketler gizlenir, alttaki cümle paragraf olarak durur.

İkinci hata, dosyayı yine metin düzenleyicide açıp oradaki sonucu tarayıcı sanmaktır. Düzenleyici kodu gösterir. Sayfayı gösteren program tarayıcıdır.

## Egzersizler

1. `trabzon.html` adlı bir dosya kurun. Sekmede “Trabzon notu” yazsın. Sayfada büyük başlık “Trabzon”, altında “Karadeniz kıyısındaki not bu dosyada.” cümlesi görünsün. Etiketler ekranda yazı olarak durmasın.
2. Aynı dosyada başlığı “İstanbul” yapıp kaydedin ve tarayıcıyı yenileyin. Ekranda “Trabzon” kalksın, büyük başlık “İstanbul” olsun. Sekmenin yazısını da “İstanbul notu” yapın.
3. Dosyayı bilerek `.txt` uzantısıyla kaydedip tarayıcıda açın. Etiketlerin yazı olarak göründüğünü doğrulayın. Ardından uzantıyı `.html` yapıp aynı dosyayı yeniden açın. “İstanbul” yine başlık olarak büyüsün.

[İçindekiler](../README.md) · [Sonraki gün →](../02-document/ders.md)
