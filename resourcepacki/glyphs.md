---
description: >-
  W tej części poradnika dowiesz się, jak tworzyć własne customowe gui, prefixy
  oraz emotki za pomocą resourepacka
icon: icons
---

# Glyphs

***

### 1. Stwórz własne tekstury prefixów

Możesz je przygotować w dowolnym programie graficznym (np. Photoshop, GIMP, Paint.NET, libresprite, asperite, blockbench).\
Maksymalny wymiar: **256x256**

Dla przykładu zrobiłem 4 proste prefixy:

| Ranga          | Wymiary Textury | Custom Znak | Textura Prefixu                                                                           |
| -------------- | --------------- | ----------- | ----------------------------------------------------------------------------------------- |
| **Właściciel** | 91×16           | ᜀ           | ![obraz](https://github.com/user-attachments/assets/806ef04f-92a1-4480-a0c1-245ee7724185) |
| **Moderator**  | 79×16           | ᜁ           | ![obraz](https://github.com/user-attachments/assets/5cf5a056-3ecd-4968-b1eb-dae54fc78554) |
| **VIP**        | 75×16           | ᜂ           | ![obraz](https://github.com/user-attachments/assets/80da3696-c153-411e-95df-e80ead225abf) |
| **Gracz**      | 87×16           | ᜃ           | ![obraz](https://github.com/user-attachments/assets/4fdb46a1-31b1-4de5-b3c9-3719414fda27) |

***

### 2. Dodaj tekstury do Resource Packa

1. Pobierz gotowego Resource Packa: https://github.com/jakmar06/resourcepack-minecraft/releases/tag/v1.0.0.
2. Otwórz go i przejdź do:\
   &#xNAN;**`assets/jakubprefix/textures/prefix`**
3. Wgraj tam swoje textury (w formacie **.png**).

***

### 3. Skonfiguruj `default.json`

[Lista przykładowych znaków do użycia](https://jrgraphix.net/r/Unicode/E000-F8FF)

Dodaj swoje prefixy, trzymając się tego formatu:

{% tabs %}
{% tab title="assets:minecraft:font/default" %}
```json
{
    "providers": [
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/root.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜀ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/moderator.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜁ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/vip.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜂ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/gracz.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜃ"]
        }
    ]
}
```
{% endtab %}
{% endtabs %}

***

⚙️ Znaczenie parametrów `ascent`, `height`, `file` i `chars`

* **`ascent`** – Odpowiada za położenie textury (w pionie)
* **`height`** – Odpowiada za wielkość textury
* **`file`** - Odpowiada za ścieżkę do textury
* **`chars`** - Odpowiada za custom znak który ma być wykorzystany do zmiany textury

🔧 Zalecane wartości:

* **`ascent`** - 7
* **`height`** - 8

Gotowy efekt na chacie:\
![358780551-aaa07922-7122-47e5-ab4b-0e9342c1fcec](https://github.com/user-attachments/assets/2700c185-3226-4386-aa04-143de6838b41)

> ⚠️ **Uwaga:** nie ustawiaj zbyt dużych wartości – zbyt wysokie wartości mogą spowodować nieprawidłowe załadowanie textury

***

### 4. Wgraj Resource Pack na hosting

Najprościej skorzystać z [mc-packs.net](https://mc-packs.net/).\
Upewnij się, że resourcepack jest zapakowany w formacie **.zip**.

***

### 5. Konfiguracja serwera

1. Otwórz plik `server.properties`
2. Znajdź i zmodyfikuj poniższe linie:

```properties
require-resource-pack=true
resource-pack=https://download.mc-packs.net/pack/baf77fd7bbc3b735975db419368851796885370a.zip
resource-pack-sha1=baf77fd7bbc3b735975db419368851796885370a 
```

* Pierwsza linia wymusza pobranie resourcepacka. ( true wymusza, false nie wymusza)
* Druga linia to link do paczki.
* Trzecia linia to hash SHA-1. (Przydatne, gdy używasz tego samego resourcepacka na paru instancjach, wtedy gracze przechodząc z trybu na tryb nie będą go ponownie ładować)

***

## Możliwe błędy/problemy/przydatne informacje

**1. Textura zostanie zabarwiona (np po kolorze nicku, czy chatu)**

![358780847-d445d342-a27d-4fa4-a08f-412c91809e8f](https://github.com/user-attachments/assets/e3a5a2e3-d217-4c3c-8d6a-664aa33a13cf)

`Aby uniknąć tego problemu kolor prefixu musi zostać zresetowany (&f/&r/§f/§r)`

**2. Gracze odnajdą twój znak**

Jeżeli gracze znajdą twój znak będą mogli nim zaspamić chat, co by mogło zniszczyć jego czytelność.

`Aby rozwiązać problem, należy pobrać dowolny plugin na blokadę słów/znaków, przykładowo` [carbonchat](https://modrinth.com/plugin/carbon) Wiki dla: [carbonchatu](https://github.com/Hexaoxide/Carbon/wiki/Basic-Configuration#chat-filter)

**3. Ikonka mimo prawidłowej ścieżki się nie pojawia**

`Aby rozwiązać ten problem, sprawdź czy textura w nazwie nie ma spacji, jest w formacie .png, nie zawiera polskich znaków, nie zawiera dużych znaków, oraz ma rozmiar mniejszy niż 256`

**4. Ładowanie resourcepacka po dołączeniu na serwer proxy**

Jeżeli chcesz, aby gracze ładowali texturepack już z poziomu serwera proxy to zainstaluj plugin [forcepack](https://github.com/SamB440/ForcePack/releases). Pozwoli to między innymi na jednoczesne przeładowanie resourcepacka dla każdego gracza na sieci, a nie tylko na konkretnym serwerze.

## Poradnik do tworzenia custom gui

1. Jak cofnąć w lewo twoje gui?

`Wklej ten fragment do twojego pliku z niestandardowymi fontami i ustaw "ベ" przed znakiem od gui`

```json
        {
            "type": "space",
            "advances": {
                "ベ": -8
            }
        },
```

{% embed url="https://github.com/jakmar06/resourcepack-minecraft/releases/tag/v.1.0.0_Prefix" %}
Link do gotowych assetów
{% endembed %}

