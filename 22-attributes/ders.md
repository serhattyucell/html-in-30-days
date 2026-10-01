# 22. Gün — Yorum, özellik, boolean özellik (Attributes)

Bu gün, tarayıcının göstermediği notu, etikete eklenen bilgiyi ve varlığı yeterli olan özelliği toplar. 2. günden beri `lang`, `href`, `src`, `alt` gibi özellikler tek tek kullanıldı. Bugün onların ortak kuralı görülür. Sonraki günler yeni etiket yığmaz. Bu kurallar, o sayfalarda aynı etiketlerin doğru yazılması içindir.

## Yorum, ekrana çıkmaz

Yorum, kaynakta duran ve sayfada görünmeyen bir nottur. `<!--` ile açılır, `-->` ile kapanır. Etiket değildir. İçine etiket yazılsa da tarayıcı onu işlemez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Gizli not</title>
  </head>
  <body>
    <h1>İstanbul</h1>
    <!-- Boğaz paragrafı, Avrupa yakası ile Anadolu yakasını aynı notta tutar. -->
    <p>Boğaz kenti iki yakaya ayırır.</p>
    <!-- <p>Bu paragraf yazılmış ama yayından çekilmiştir.</p> -->
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Gizli not”, sayfada “İstanbul” başlığı ve “Boğaz kenti iki yakaya ayırır.” paragrafı vardır. Yorumun içindeki uzun cümle görünmez. Yoruma alınmış ikinci paragraf da görünmez. Sayfa kaynağı açılırsa iki yorum da oradadır. Ziyaretçi kaynağa bakarsa notu okuyabilir. Yorum, parola veya gizli tutulması gereken bir cümle için değildir. Kaynak, sayfayla birlikte gelir. Yorum, “bu paragraf neden duruyor” sorusuna kendi kendine bırakılan cevaptır.

Yorumun içinde `--` dizisi kullanılmaz. Kapanış erken gelir ve sonraki kelimeler sayfaya taşabilir. Kapanış unutulursa belgenin geri kalanı da yoruma düşer. Alt bilgi, form ve bir sonraki başlık ekrandan kaybolur. Kapanış, notun bittiği satırda durur.

## Özellik, etiketin içindeki bilgidir

Özellik, açılış etiketinin içinde, adından sonra yazılır. Değeri tırnak içindedir. Bir etiketin birden fazla özelliği yan yana durabilir. Özellik, yeni bir etiket açmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Özellikler</title>
  </head>
  <body>
    <h1 id="bas" class="not" title="Sayfanın ana adı" lang="tr">Van</h1>
    <p title="Fare bu cümlenin üzerinde bekleyince bu cümle çıkar.">
      Van Gölü geniştir.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” büyük bir başlık, altında “Van Gölü geniştir.” paragrafı vardır. `id`, `class` ve `lang` ekranda yazı olarak durmaz. `class="not"` bir renk de vermez. Sınıf adı, ileride CSS konusunun kullanacağı bir etikettir. Bu belgede görünüşü değiştirmez. `id="bas"` ise 10. gündeki gibi, `#bas` adresinin varacağı yerdir. Aynı `id` sayfada bir kez durur. Aynı `class` birçok etikete yazılabilir. İki başlık da `class="not"` olabilir. İkisi de `id="bas"` olamaz.

`title`, fare ile kelimenin üzerine gelinip kısa bir süre beklenince çıkan küçük ipucudur. Paragrafın üzerinde “Fare bu cümlenin üzerinde bekleyince bu cümle çıkar.” belirir. Fare çekilince ipucu kaybolur. Dokunmatik ekranda bu ipucu çoğu zaman hiç açılmaz. Bu yüzden asıl cümle `title` içine saklanmaz. Asıl cümle paragrafta durur. İpucu, kısa bir ek bilgidir. Başlıktaki `title="Sayfanın ana adı"` da yalnız üzerine gelinince görünür. Sayfa ilk açıldığında orada değildir.

`lang`, 2. gündeki belgenin dilinden ayrı olarak tek bir parçanın dilini de söyleyebilir. Bütün sayfa Türkçeyse `lang` belgenin `<html>` etiketinde durur. Tek kelime başka dildeyse o kelimenin etiketi kendi `lang` değerini alır. Bu örnekte başlık yine Türkçedir.

Özelliğin değeri çift tırnak içindedir. Değerin kendisinde çift tırnak varsa dışarıya tek tırnak konabilir. Bu rehberde değerler kısa tutulur ve çift tırnak kullanılır. Eşittir işaretinin çevresindeki boşluk tarayıcıyı şaşırtabilir. `title = "Van"` yerine `title="Van"` yazılır.

## Boolean özellikte varlık yeter

Boolean özellik, değeri “evet veya hayır” olan özelliktir. Adı yazıldıysa anlamı açıktır. Değeri yazmak zorunlu değildir. `disabled`, `checked`, `required`, `readonly`, `multiple` ve `hidden` bu türdendir. Bir kısmı form günlerinde işin içinde kullanıldı. Bugün ortak kural görülür: ad duruyorsa özellik açıktır. `disabled="false"` yazmak özelliği kapatmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Açık ve kapalı</title>
  </head>
  <body>
    <h1>Formun durumu</h1>
    <form action="boolean.html" method="get">
      <p>
        <label for="kent">Kent</label>
        <input id="kent" type="text" name="kent" value="Van" required />
      </p>
      <p>
        <label for="plaka">Plaka</label>
        <input id="plaka" type="text" name="plaka" value="65" readonly />
      </p>
      <p>
        <label>
          <input type="checkbox" name="göl" value="var" checked />
          Göl bu notta var
        </label>
      </p>
      <p hidden>
        Bu paragraf kaynakta durur, sayfada yoktur.
      </p>
      <p>
        <button type="submit">Gönder</button>
        <button type="submit" disabled>Kapalı düğme</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” kutusu boş değildir, içinde “Van” yazar. Kutu boşaltılıp gönderilirse tarayıcı uyarı verir. `required` adı satırda durduğu için kutu zorunludur. “Plaka” kutusunda “65” durur ve değiştirilemez. Yanında “Göl bu notta var” karesi doludur. “Bu paragraf kaynakta durur, sayfada yoktur.” cümlesi ekranda yoktur. `hidden`, o paragrafı sayfadan çıkarır. Yerinde boş bir delik bırakmaz. Alttaki “Gönder” tıklanabilir. “Kapalı düğme” soluk durur. Tıklanınca form gitmez. `disabled` düğmeyi kullanılamaz yapar.

Kent doluysa adres `kent=Van&plaka=65&göl=var` benzeri bir sorguyla biter. `readonly` alan gönderilir. `disabled` bir kutu olsaydı o kutu pakete girmezdi. Kapalı düğme zaten bir alan değildir. `hidden` paragraf da form alanı olmadığı için adreste yer almaz. Gizlenen şey bir kutuysa ve `disabled` değilse, kutu ekranda yokken de gönderilebilir. Görünmez diye sızdırılmaması gereken bir kelime kutuya konmaz.

`required`, `required="required"` ve `required=""` aynı anlama gelir. Üçü de zorunlu kılar. `disabled="false"` ise düğmeyi açmaz. Özelliğin varlığı yeter. Değer olarak yazılan `false` kelimesi yok sayılır. Düğme yine kapalıdır. Kapatmak için özellik satırdan silinir. `true` yazmaya da gerek yoktur.

`multiple`, 18. gündeki dosya alanında birden çok dosya seçtirir. Adı yazıldıysa çoklu seçim açıktır. `checked` ve `selected` de aynı mantıktadır. Sayfa açıldığında seçili olan kutu, bu ad taşır.

## Sık yapılan hata

Boolean özelliğe `false` demek, onu kapatmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış kapanış</title>
  </head>
  <body>
    <h1>Kapalı sandığı düğme</h1>
    <form action="yanlis.html" method="get">
      <p>
        <button type="submit" disabled="false">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Gönder” soluktur. Tıklanınca sayfa yenilenmez, adres değişmez. `false` yazılmış olsa da düğme kapalıdır. Kaynak, düğmenin açık olduğunu söylemez.

Doğru belgede açık düğmenin satırında `disabled` yoktur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Açık düğme</title>
  </head>
  <body>
    <h1>Açık düğme</h1>
    <form action="acik.html" method="get">
      <p>
        <label for="kent">Kent</label>
        <input id="kent" type="text" name="kent" value="Trabzon" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Gönder” soluk değildir. Tıklanınca adres `kent=Trabzon` ile biter.

İkinci hata, yorumu kapatmamaktır. `<!--` satırından sonraki başlık, paragraf ve düğme ekrandan silinir. Sayfa boş kalabilir. Kapanış eklenince alttaki “Trabzon” paragrafı geri gelir.

Üçüncü hata, `id` değerini iki etikete birden yazmaktır. `#bas` bağlantısı her zaman birincisinde durur. İkinci başlık hedef olmaz. Sınıf tekrarı serbesttir. Kimlik tekrarı serbest değildir.

## Egzersizler

1. Bir paragraftan önce, ekranda görünmeyen bir cümle yazın. Sayfada yalnızca İstanbul başlığı ve bir paragraf dursun. Sayfa kaynağında yorum okunsun. Yoruma alınmış ikinci bir paragraf da ekranda yer kaplamasın.
2. Bir başlığa `id` ve `title` verin. Fare başlığın üzerinde bekleyince “Sayfanın ana adı” görünsün. Fare çekilince ipucu kalsın değil, kaybolsun. Sayfa ilk açıldığında bu cümle görünmesin. Aynı `class` adını iki paragrafta kullanın. İkisinin rengi değişmesin.
3. `disabled="false"` yazılmış bir düğme kurun. Düğmenin yine soluk ve tıklanamaz olduğunu görün. Özelliği silin. “Gönder” tıklanınca kent kutusu adrese geçsin.

[← Önceki gün](../21-quote-code-time/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../23-accessibility/ders.md)
