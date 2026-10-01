# 19. Gün — Düğme ve etiket (Button and Label)

Bu gün, formdaki düğmenin ne iş yaptığını ve kutunun adının kutuya bağlanmasını ayırır. 15. günden beri “Gönder” diye bir düğme vardı. Onun yanı sıra formu temizleyen ve hiçbir şey yapmayan düğmeler de vardır. Kutunun üstündeki “Kent” yazısı ise henüz kutunun kendisiyle bağlı değildi. Yazıya tıklanınca kutu seçilmiyordu.

## Düğmenin üç işi

`<button>`, üzerinde yazı duran bir düğmedir. `type` özelliği işi seçer. `submit` formu gönderir. `reset` alanları başlangıca döndürür. `button` ise JavaScript olmadığı sürece bir iş yapmaz. Bu rehber JavaScript’e girmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Üç düğme</title>
  </head>
  <body>
    <h1>İzmir formu</h1>
    <form action="uc-dugme.html" method="get">
      <p>
        Kent
        <input type="text" name="kent" value="İzmir" />
      </p>
      <p>
        <button type="submit">Gönder</button>
        <button type="reset">Temizle</button>
        <button type="button">Beklet</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Kutuda “İzmir” yazar. Altında üç düğme yan yana durur: “Gönder”, “Temizle”, “Beklet”. Üçü de düğme biçimindedir. Yazıları farklıdır. “Temizle” tıklanınca kutu, sayfa ilk açıldığındaki “İzmir” değerine döner. Ziyaretçi kutuyu “Van” yapmışsa “Temizle” onu siler ve yeniden “İzmir” yazar. Adres çubuğu değişmez. “Beklet” tıklanınca kutu değişmez, sayfa yenilenmez, adres de değişmez. “Gönder” tıklanınca sayfa yenilenir ve adres `kent=` ile kutuda o anda duran kelimeyi taşır.

`type` yazılmazsa düğme, bir formun içindeyken çoğu tarayıcıda gönder düğmesi sayılır. “Temizle” gibi görünen ama türü unutulmuş bir düğme, kutuyu silmez. Formu yollar. Her düğmenin türü açık yazılır.

`<input type="submit" value="Gönder" />` da aynı gönder işini yapan eski biçimdir. Düğmenin yazısı `value` içindedir. İçine başka etiket konamaz. `<button>` içindeyse yazı, etiketin arasındadır. İleride düğmenin içine bir görsel konacaksa `<button>` o yüzden kullanılır. Bugün ikisi de “Gönder” yazar ve aynı sonucu üretir. Bu rehberde düğme `<button>` olarak kalır.

## Etiket, kutunun adıdır

`<label>`, bir alanın adını o alana bağlar. Bağ, ya etiketin `for` özelliği ile alanın `id` özelliği aynı yapılarak kurulur ya da alan, etiketin içine konur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı etiket</title>
  </head>
  <body>
    <h1>Trabzon formu</h1>
    <form action="etiket.html" method="get">
      <p>
        <label for="kent">Kent</label>
        <input id="kent" type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” yazısı ile boş kutu yan yana durur. Yazı mavi değildir, altı çizili değildir. Bir başlık kadar büyük de değildir. Normal bir kelimedir. “Kent” kelimesine tıklanınca imleç, kutunun içine geçer. Kutunun çevresinde tarayıcının odak çizgisi belirir. Kelimeye değil kutuya tıklanınca da aynı odak gelir. `for` ve `id` ekranda yazı olarak görünmez. İkisi de `kent` olduğu için tarayıcı bağı kurar.

`id` ile `name` aynı kelime olabilir ama aynı işi yapmaz. `id` etiketi bu alana bağlar. `name` gönderimde paketin adını verir. Bağ kurmak için `for="kent"` yazıp `name="kent"` yazmak yetmez. `id` yoksa yazıya tıklamak kutuyu seçmez.

Etiket, alanı sararak da bağlanır. `for` ve `id` o zaman gerekmez:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Saran etiket</title>
  </head>
  <body>
    <h1>Onay</h1>
    <form action="saran.html" method="get">
      <p>
        <label>
          <input type="checkbox" name="durak" value="van" />
          Van
        </label>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Küçük bir kare ve sağında “Van” vardır. “Van” kelimesine tıklanınca kare dolar veya boşalır. Yalnızca karenin kendisine değil, kelimeye de basmak işe yarar. Kare küçüktür. Kelime daha geniş bir hedeftir. İşaretli kareyle gönderilince adres `durak=van` olur.

Radyo düğmelerinde de her satır kendi `<label>` çiftinin içinde durur. “E-posta” yazısına tıklamak, yalnızca küçük dairenin tıklanmasıyla aynı sonucu verir.

## Gönder düğmesi formun dışındaysa

Bir düğme, `form` kapanışından sonra duruyorsa o formu kendiliğinden göndermez. `form` özelliği, düğmeye hangi formun adını vereceğini söyler. Özellik, formun `id` değeriyle eşleşir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dışarıdaki düğme</title>
  </head>
  <body>
    <h1>Van formu</h1>
    <form id="gol" action="disari.html" method="get">
      <p>
        <label for="not">Not</label>
        <input id="not" type="text" name="not" />
      </p>
    </form>
    <p>
      <button type="submit" form="gol">Gönder</button>
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Kutu üstte, “Gönder” düğmesi bir paragraf aşağıda durur. Düğme formun dışında görünür. Kutuya `göl` yazılıp düğmeye basılınca sayfa yine yenilenir. Adres `not=göl` ya da Türkçe harfin koduyla biter. `form="gol"`, düğmeyi `id="gol"` olan forma bağlar. Bu satır silinirse düğme tıklanınca kutu yerinde kalır, adres değişmez. 15. gündeki hata burada bilinçli bir bağ ile çözülür. Yeni bir sayfa düzeni, düğmeyi kutudan aşağı almak isteyebilir. Bağ koparılmaz.

## Sık yapılan hata

Etiketin `for` değeri ile kutunun `id` değeri farklıysa yazı, kutuyu seçmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kopuk etiket</title>
  </head>
  <body>
    <h1>Kopuk</h1>
    <form action="kopuk.html" method="get">
      <p>
        <label for="sehir">Kent</label>
        <input id="kent" type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” ile kutu yine yan yanadır. Kelimeye tıklanınca imleç kutuya geçmez. Kutu boş kalır, odak çizgisi gelmez. Ekranda bağ varmış gibi durur. `for="sehir"` hiçbir alanın `id` değeriyle eşleşmez. Kutunun kimliği `kent`tir.

Doğru belgede iki taraf aynı kelimedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı</title>
  </head>
  <body>
    <h1>Bağlı</h1>
    <form action="bagli.html" method="get">
      <p>
        <label for="kent">Kent</label>
        <input id="kent" type="text" name="kent" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” kelimesine tıklanınca imleç kutudadır. Gönder düğmesi formu yollar. Temizle düğmesi gerekirse türü `reset` olur ve bu kutuyu boşaltır. `value` yoksa başlangıç da boştur.

İkinci hata, düğmenin türünü unutup “Temizle” yazmaktır. Tıklama, kutuyu eski hâline getirmek yerine `?kent=` sorgusu üretir. Tür yazılınca “Temizle” yalnızca kutuyu döndürür.

Üçüncü hata, `<button>` kapanışını unutmaktır. Sonraki paragraf düğmenin yazısına karışır. Ekranda uzun, içine cümle kaçmış bir düğme belirir. Kapanış, düğmenin görünen adından hemen sonra konur.

## Egzersizler

1. Üç düğme kurun. “Gönder” adrese `kent` değerini yazsın. “Temizle”, kutuyu başlangıçtaki “Trabzon” değerine döndürsün ve adresi değiştirmesin. “Beklet” ne kutuyu ne adresi değiştirsin.
2. “Van” yazısına tıklanınca onay karesi dolsun veya boşalsın. Tıklamak için karenin kendisi gerekmesin. İşaretliyken gönderince `durak=van` görünsün.
3. Etiketin `for` değerini kutunun `id` değerinden farklı yazın. Yazıya tıklayınca imleç kutuya gitmesin. İki değeri yeniden eşitleyin. Yazıya tıklamak, kutuya tıklamakla aynı sonucu versin.

[← Önceki gün](../18-number-date-file/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../20-semantic-layout/ders.md)
