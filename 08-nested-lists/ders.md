# 8. Gün — İç içe listeler (Nested Lists)

Bu gün, bir maddenin altına o maddeye ait alt maddeler açar. 6. ve 7. günlerde her liste düzdü. Bir durağın içindeki işler, o durağın maddesinin içinde ikinci bir liste olunca grup ekranda da kaynakta da belli olur.

## Alt liste, maddenin içinde durur

İç liste, iki madde arasında boşta durmaz. Ait olduğu `<li>` kapanmadan önce açılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durağın içi</title>
  </head>
  <body>
    <h1>İstanbul durağı</h1>
    <ul>
      <li>
        İstanbul
        <ul>
          <li>Galata Kulesi</li>
          <li>Kapalıçarşı</li>
        </ul>
      </li>
      <li>İzmir</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
Dış listede iki madde vardır. “İstanbul” bir daireyle başlar. Onun altında, daha içeriden, ikinci bir girintiyle “Galata Kulesi” ve “Kapalıçarşı” durur. Bu alt satırların işareti çoğu tarayıcıda içi boş dairedir. Böylece iç listenin dış listenin kopyası olmadığı görünür. “İzmir” yeniden dış girintiye döner ve dolu daire alır. “Kapalıçarşı” ile “İzmir” aynı hizada değildir. İzmir, Galata’nın kardeşi değil, İstanbul’un kardeşidir.

İç listedeki her satır yine `<li>` olmak zorundadır. Dış `<li>`, hem “İstanbul” kelimesini hem de içindeki `<ul>` etiketini taşır. Kelime, iç listeden önce yazılır. Böylece madde adı önce, ayrıntılar onun altında okunur.

## Numaralı durak, harfli hazırlık

Dış sıra bir yolculuk, iç sıra o durakta yapılacak işler olabilir. İki listenin türü aynı olmak zorunda değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durak ve hazırlık</title>
  </head>
  <body>
    <h1>İki durak</h1>
    <ol>
      <li>
        Trabzon
        <ol type="a">
          <li>Kıyıya in</li>
          <li>Çarşıyı geç</li>
        </ol>
      </li>
      <li>
        Van
        <ol type="a">
          <li>Göl kıyısına bak</li>
          <li>Kaleye çık</li>
        </ol>
      </li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Dış liste “1. Trabzon” ve “2. Van” diye numaralanır. Trabzon’un altında, daha içeride “a. Kıyıya in” ve “b. Çarşıyı geç” durur. Van’ın altındaki harfler yeniden “a.” ile başlar. “b. Çarşıyı geç” satırından sonra gelen harf “c.” olmaz. İç liste kendi sayımını yapar. Van’ın “a.” sı, Trabzon’un “a.” sı ile aynı sütunda, dış numaralardan daha sağdadır.

`<ol>` içine `<ul>` koymak da aynı girintiyi verir. Alt maddelerin sırası önemli değilse iç liste daire olur. Saat Kulesi ile Kordon arasında bir öncelik yoksa İzmir’in altı `<ul>` kalır. İskelede bilet sırası varsa iç liste `<ol>` olur.

## Üç kat, okunabilir derinlik

Üçüncü kat, bir alt maddenin de kendi ayrıntısı varsa açılır. Her kat, bir öncekinin içinde durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Üç kat</title>
  </head>
  <body>
    <h1>Van notunun içi</h1>
    <ul>
      <li>
        Van
        <ul>
          <li>
            Van Gölü
            <ul>
              <li>Kıyı</li>
              <li>Tekne saati</li>
            </ul>
          </li>
          <li>Van Kalesi</li>
        </ul>
      </li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” en soldaki dairededir. “Van Gölü” ve “Van Kalesi” bir kat içeridedir ve boş daire alır. “Kıyı” ile “Tekne saati” daha da içeridedir. Üçüncü katın işareti çoğu tarayıcıda dolu bir karedir. “Van Kalesi”, “Tekne saati” ile aynı hizada değildir. Kale, gölün kardeşidir ve ikinci kattadır. Kıyı, gölün altındadır. Dördüncü ve beşinci kat teknik olarak yazılabilir. Ekranda girinti o kadar artar ki satır pencerenin sağına yapışır. Kent notu üç katta durur.

İç listenin madde işareti tarayıcıya göre küçük farklarla değişebilir. Değişmeyen şey girintidir: her yeni liste bir öncekinden daha sağda başlar. İşaretin rengini ve biçimini seçmek ileride CSS konusudur.

## Sık yapılan hata

İç listeyi maddenin dışına, iki `<li>` arasına koymak, o listeyi üst listenin çocuğu yapar. Üst liste ise çocuk olarak yalnızca madde kabul eder.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış girinti</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <ul>
      <li>İzmir</li>
      <ul>
        <li>Saat Kulesi</li>
        <li>Kordon</li>
      </ul>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“Saat Kulesi” ve “Kordon” çoğu tarayıcıda yine içeride görünür. Görüntü bazen doğru listeye benzer ve hata gizlenir. Bazı tarayıcılar ise iç listeyi “İzmir” maddesiyle “Van” maddesi arasından çıkarıp ayrı bir blok gibi dizer. “Van”, kulelerin kardeşi gibi okunabilir. Kaynak, Saat Kulesi’nin İzmir maddesine ait olduğunu söylemez.

Doğru belge, iç listeyi İzmir maddesinin kapanışından önceye alır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Doğru girinti</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <ul>
      <li>
        İzmir
        <ul>
          <li>Saat Kulesi</li>
          <li>Kordon</li>
        </ul>
      </li>
      <li>Van</li>
    </ul>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” dıştadır. Kule ve Kordon onun altında, daha sağdadır. “Van” yeniden dış hizaya döner. Van’ın altında kule yoktur.

Kapanış sırasını karıştırmak da aynı hataya gider. İç `</ul>`, dış `</li>`’den sonra gelirse iç liste maddeye ait olmaktan çıkar. Önce iç liste kapanır, sonra madde kapanır, en sonda dış liste kapanır.

## Egzersizler

1. Numaralı bir dış liste kurun: 1 İstanbul, 2 Van. İstanbul’un altında daireli iki alt madde görünsün: Galata Kulesi ve Kapalıçarşı. Van’ın altında daireli iki alt madde görünsün: Van Gölü ve Van Kalesi. Van’ın alt maddeleri 3 ve 4 numarası almasın.
2. Trabzon maddesinin altına “a.” ve “b.” ile iki hazırlık yazın. İstanbul maddesinden bağımsız, kendi “a.” sı ile başlasın. Trabzon’un harfleri, İstanbul’un numarasıyla aynı hizada durmasın.
3. İç listeyi bilerek maddenin dışına koyup yenileyin. Sonra aynı listeyi maddenin içine alın. “Saat Kulesi” yalnızca İzmir’in altında, daha sağda dursun. İzmir’den sonraki kent, kule ile aynı girintide olmasın.

[← Önceki gün](../07-ordered-lists/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../09-links/ders.md)
