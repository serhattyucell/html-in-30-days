# 20. Gün — Anlamlı bölgeler (Semantic Layout)

Bu gün, sayfayı üst baş, gezinti, asıl konu, yan not ve alt bilgi diye böler. 3. günden beri başlıklar konunun düzeyini söylüyordu. Bölge etiketleri, o başlığın sayfanın neresinde durduğunu söyler. Tarayıcı bu bölgeleri renkle boyamaz. Çerçeve ileride CSS konusudur. Ekranda görünen, blokların yukarıdan aşağı sırasıdır. Anlam, etiket adındadır.

## Üst, gezinti, asıl konu, alt

`<header>` sayfanın veya bir bölümün baş kısmıdır. `<nav>` bağlantıların listesidir. `<main>` sayfanın biricik asıl konusudur. `<footer>` alt bilgidir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört kent</title>
  </head>
  <body>
    <header>
      <h1>Serhat'ın kent notları</h1>
      <p>İstanbul, İzmir, Trabzon ve Van.</p>
    </header>
    <nav>
      <ul>
        <li><a href="#istanbul">İstanbul</a></li>
        <li><a href="#izmir">İzmir</a></li>
        <li><a href="#trabzon">Trabzon</a></li>
        <li><a href="#van">Van</a></li>
      </ul>
    </nav>
    <main>
      <h2 id="istanbul">İstanbul</h2>
      <p>Boğaz kenti iki yakaya ayırır.</p>
      <h2 id="izmir">İzmir</h2>
      <p>Saat Kulesi meydandadır.</p>
      <h2 id="trabzon">Trabzon</h2>
      <p>Kent Karadeniz kıyısındadır.</p>
      <h2 id="van">Van</h2>
      <p>Van Gölü geniştir.</p>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte büyük “Serhat'ın kent notları” ve hemen altında kısa bir paragraf vardır. Sonra dört bağlantı, madde işaretleriyle alt alta durur. Bağlantılar mavi ve altı çizilidir. Ardından dört bölüm gelir. Her birinin orta boy başlığı ve bir paragrafı vardır. “İstanbul” bağlantısına tıklanınca sayfa o başlığa kayar. 10. gündeki sayfa içi bağlantı burada gezintinin içindedir. En altta, normal puntoda “Notu yazan: Serhat” yazar. Üst kısım renkli bir şerit, gezinti yatay bir çubuk, alt bilgi ise koyu bir kuşak değildir. Hepsi art arda, beyaz sayfada, başlıktan paragrafa doğru dizilir. `<header>`, `<nav>`, `<main>` ve `<footer>` ekranda etiket adı olarak çıkmaz.

Bir sayfada bir `<main>` olur. Asıl konu odur. Üstteki ad ve alttaki “notu yazan” satırı asıl konunun parçası değildir. Onlar her sayfada tekrar edilebilecek çerçevedir. Çerçeve kelimesi burada renkli kutu anlamına gelmez. Anlamı, konunun çevresindeki sabit parçalardır.

## Bölüm ve bağımsız yazı

`<section>`, sayfanın bir konusunu toplar. Bir başlığı olması beklenir. `<article>`, sayfadan çıkarılıp tek başına da durabilen bir yazıdır. Bir kent notu, başka bir sayfada da aynı hâliyle okunabiliyorsa yazı bu etikete girer.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Van yazısı</title>
  </head>
  <body>
    <header>
      <h1>Serhat'ın kent notları</h1>
    </header>
    <main>
      <article>
        <header>
          <h2>Van</h2>
          <p>Gölün kıyısından bakılan not.</p>
        </header>
        <section>
          <h3>Van Gölü</h3>
          <p>Göl geniştir ve kent kıyıdan ona bakar.</p>
        </section>
        <section>
          <h3>Van Kalesi</h3>
          <p>Kale tepeden gölü görür.</p>
        </section>
        <footer>
          <p>Bu yazı tek başına da okunur.</p>
        </footer>
      </article>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfa başlığı “Serhat'ın kent notları” en büyüktür. Altında “Van” biraz daha küçüktür. Onun altında kısa bir paragraf, sonra “Van Gölü” ve “Van Kalesi” daha küçük iki başlık olarak durur. Her birinin bir paragrafı vardır. En altta “Bu yazı tek başına da okunur.” cümlesi vardır. İki bölüm arasında renkli bir kart yoktur. Ayrımı başlık düzeyleri yapar. Van’ın içindeki `<header>` ve `<footer>`, sayfanın üstü ve altı değildir. Yalnızca bu yazının başı ve sonudur. Sayfanın `<h1>` değeri ile yazının `<h2>` değeri karışmaz. Sayfada bir ana ad, yazının içinde de kendi adı vardır.

`<section>` başlıksız bırakılırsa div gibi sıradan bir kutu olur. Bu rehber kutu için etiket yığmaz. Bölüm, bir başlık taşıyorsa açılır. Taşımıyorsa paragraflar art arda durur.

## Yan not

`<aside>`, asıl konunun yanında duran, ama o konunun içinden çıkınca da anlamını yitirmeyen bir nottur. Kısa bir plaka hatırlatması, Van yazısının gövdesine gömülmek zorunda değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yan not</title>
  </head>
  <body>
    <header>
      <h1>Serhat'ın kent notları</h1>
    </header>
    <main>
      <article>
        <h2>İzmir</h2>
        <p>Saat Kulesi, Konak meydanının ortasında durur.</p>
      </article>
      <aside>
        <h2>Plaka</h2>
        <p>İzmir’in plakası 35’tir.</p>
      </aside>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” bölümü üstte, “Plaka” bölümü onun altında durur. İkisi yan yana iki sütun olmaz. Sütun ileride CSS konusudur. “Plaka” yine de gövde metninin bir cümlesi gibi “Saat Kulesi…” ile aynı paragrafta kaynaşmaz. Kendi başlığı vardır. Okuma sırası yukarıdan aşağıdır: ana ad, İzmir notu, plaka hatırlatması, en altta “Notu yazan: Serhat”. Plaka notu silinse İzmir paragrafı eksilmez. Bu yüzden not, `<aside>` içindedir. İzmir’i anlatan cümle ise `<article>` içindedir.

## Sık yapılan hata

Sayfada iki `<main>` açmak, asıl konuyu ikiye böler. Tarayıcı ikisini de sıradan blok gibi alt alta çizebilir. Hata ekranda bağırmadan durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki asıl konu</title>
  </head>
  <body>
    <main>
      <h1>İstanbul</h1>
      <p>Boğaz bu sayfadadır.</p>
    </main>
    <main>
      <h1>Van</h1>
      <p>Göl bu sayfada ikinci bir asıl konu olmuştur.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
İki büyük başlık alt alta durur. İkisi de aynı büyüklüktedir. Sayfada iki ana ad vardır ve iki `<main>` bölgesi vardır. Hangi bloğun sayfanın konusu olduğu seçilemez. 3. gündeki tek `<h1>` kuralı burada da bozulmuştur.

Doğru belgede bir ana ad, bir asıl bölge ve iki alt konu vardır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek asıl konu</title>
  </head>
  <body>
    <header>
      <h1>İki kent</h1>
    </header>
    <main>
      <h2>İstanbul</h2>
      <p>Boğaz bu bölümde durur.</p>
      <h2>Van</h2>
      <p>Göl bu bölümde durur.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte tek büyük başlık “İki kent” vardır. İstanbul ve Van ondan küçüktür. İkisi de aynı asıl bölgenin içindedir. Alt alta, aynı sayfanın iki bölümü olarak okunur.

İkinci hata, her paragrafı `<section>` yapmaktır. Sayfa, içi boş anlamlar taşır. Başlıksız bölümler ekranda yine boşluk bırakır ama belgeye konu eklemez. Bölüm, yeni bir alt başlık varsa açılır.

Üçüncü hata, gezinti bağlantılarını `<nav>` dışında, alt bilginin içine ve asıl konunun içine üçüncü bir kez daha kopyalamaktır. Bir menü yeter. Alt bilgideki “Notu yazan: Serhat” satırı menünün kopyası olmaz.

## Egzersizler

1. Sayfayı üst baş, dört bağlantılık bir gezinti, asıl konu ve alt bilgi olarak kurun. Gezinti mavi bağlantılarla alt alta dursun. Renkli bir şerit görünmesin. “Van” bağlantısı tıklanınca sayfa Van başlığına insin.
2. Van’ı, içinden çıkarılınca da okunan bir yazı yapın. Yazının içinde “Van Gölü” ve “Van Kalesi” diye iki bölüm, her birinin kendi başlığı ve paragrafı olsun. İki bölüm kart gibi yan yana durmasın. Alt alta, başlık sırasıyla dursun.
3. İkinci bir `<main>` ekleyip sayfayı yenileyin. İki büyük blok göründükten sonra tek asıl bölgeye dönün. İstanbul ve Van, tek büyük başlığın altında iki alt başlık olsun.

[← Önceki gün](../19-button-label/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../21-quote-code-time/ders.md)
