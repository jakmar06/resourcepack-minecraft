---
description: >-
  W tej części poradnika dowiesz się, jak tworzyć własne customowe gui, prefixy
  oraz emotki za pomocą resourepacka
icon: icons
cover: ../.gitbook/assets/glyphs.png
coverY: 0
---

# Glyphs

***

## &#x20;Custom Prefixy

{% stepper %}
{% step %}
### Przygotowanie prefixów

Przygotuj tekstury twoich prefixów w dowolnym programie graficznym, poniżej masz kilka przykładów:

* Photoshop
* Photopea
* Paint.NET
* Gimp
* Blockbench (zalecane)
* Libresprite/asperite (zalecane)

Możesz również kupić/pobrać gotowe prefixy lub użyć prostego generatora prefixów np:

{% embed url="https://www.artillex-studios.com/prefix-generator" %}

{% hint style="warning" %}
Pamiętaj, że maksymalne wymiary **pojedynczej tekstury** custom glypha wynoszą **256×256**, oraz **muszą** być w formacie **.png**
{% endhint %}
{% endstep %}

{% step %}
### Umieść Tekstury w odpowiednim folderze

Gotowe tekstury umieść w niżej wymienionej śćieżce

```yaml
📁twój_resourcepack
└── 📁assets
    └── 📁twoj_namespace
        └── 📁textures
            └── 📁twoja_nazwa
                └── 🧮 twoja_tekstura/twoje_tekstury.png
```

{% hint style="info" %}
* `twoj_namespace` to główny folder twoje resourcepacka, w podstawowym resourcepacku nazywa się to `minecraft`.
{% endhint %}
{% endstep %}

{% step %}
### Zdefiniuj custom znaki

W tym kroku tworzysz **plik definicji**, który łączy teksturę z custom fontem. Aby to zrobić musisz trzymać się niżej wymienionego formatu oraz użyć custom znaków.

{% embed url="https://jrgraphix.net/r/Unicode/E000-F8FF" %}
Strona z przykładowymi znakami
{% endembed %}

{% code title="assets:twoj_namespace/font:twoja_nazwa.json" %}
```json
    "providers": [
        {
            "type": "bitmap",
            "file": "twoj_namespace:twoja_nazwa/root.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜀ"]
        },
        {
            "type": "bitmap",
            "file": "twoj_namespace:twoja_nazwa/moderator.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜁ"]
        },
        {
            "type": "bitmap",
            "file": "twoj_namespace:twoja_nazwa/vip.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜂ"]
        },
        {
            "type": "bitmap",
            "file": "twoj_namespace:twoja_nazwa/gracz.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜃ"]
        }
    ]
}
```
{% endcode %}

{% hint style="info" %}
* Gdy umieścisz plik definicji w innym folderze niż `minecraft` może to być problematyczne gdy twój plugin nie ma wsparcia formatowania wiadomości [**minimessage**](https://docs.papermc.io/adventure/minimessage/format/#font), ponieważ nie będą one działać do momentu póki nie zdefinujesz ścieżki.&#x20;
* `twoja_nazwa.json` W tym pliku przydzielasz custom teksture dla znaku, pamiętaj że jak w przypadku namespace nie znajduje się on w folderze `minecraft` oraz nie jest nazwany `default.json` to będziesz musiał zdefiniować śćieżkę używająć formatu [**minimessage**](https://docs.papermc.io/adventure/minimessage/format/#font)**.**
* `twoja_nazwa` to dodatkowy folder w folderze `textures`, gdy go nie posiadasz podajesz po prostu `twoj_namespace:twoja_tekstura`
{% endhint %}

#### Znaczenie parametrów

* **`ascent`** – Odpowiada za położenie textury (w pionie)
* **`height`** – Odpowiada za wielkość textury
* **`file`** - Odpowiada za ścieżkę do textury
* **`chars`** - Odpowiada za custom znak który ma być wykorzystany do zmiany textury

**Zalecane wartości:**

* **`ascent`** - 7
* **`height`** - 8
{% endstep %}

{% step %}
### Instalacja resourcepacka

Skorzystaj z niżej wymienionego poradnika by zainstalować poprawnie resourcepack:

{% embed url="https://jakmar.gitbook.io/minecraft-wiki/resourcepacki/instalacja-resourcepacka" %}
{% endstep %}

{% step %}
### Ustawienie prefixów za pomocą luckperms

Ustaw twoje prefixy za pomocą komendy `/lp group <ranga> meta setprefix <waga> "<white>custom_znak"`

Poniżej przedstawiam tabelke z przykładami, oraz gotowego resourepacka na którym można się wzorować.

| Ranga          | Wymiary Textury | Custom Znak | Textura Prefixu                                                                           |
| -------------- | --------------- | ----------- | ----------------------------------------------------------------------------------------- |
| **Właściciel** | 91×16           | ᜀ           | ![obraz](https://github.com/user-attachments/assets/806ef04f-92a1-4480-a0c1-245ee7724185) |
| **Moderator**  | 79×16           | ᜁ           | ![obraz](https://github.com/user-attachments/assets/5cf5a056-3ecd-4968-b1eb-dae54fc78554) |
| **VIP**        | 75×16           | ᜂ           | ![obraz](https://github.com/user-attachments/assets/80da3696-c153-411e-95df-e80ead225abf) |
| **Gracz**      | 87×16           | ᜃ           | ![obraz](https://github.com/user-attachments/assets/4fdb46a1-31b1-4de5-b3c9-3719414fda27) |

{% embed url="https://github.com/jakmar06/resourcepack-minecraft/releases/tag/v.1.0.0_Prefix" %}
Link do gotowych assetów
{% endembed %}
{% endstep %}

{% step %}
### Możliwe problemy oraz przydatne informacje.

#### 1. Tekstura zamiast koloru białego będzie miała inny np. różowy

![358780847-d445d342-a27d-4fa4-a08f-412c91809e8f](https://github.com/user-attachments/assets/e3a5a2e3-d217-4c3c-8d6a-664aa33a13cf)

{% hint style="info" %}
Aby uniknąć tego problemu, kolor twojego prefixu musi być biały. Przed twoim custom znakiem podczas ustawiania prefixu możesz umieśćić: `<white>/<reset>/&f/&r/§f/§r`
{% endhint %}

#### 2. Gracze odkryją twój custom znak.

{% hint style="info" %}
Jeżeli gracze odkryją twój custom znak, będą mogli go wysłać na chat co by mogło zniszczyć jego czytelność.&#x20;

* Aby rozwiązać ten problem możesz pobrać dowolny plugin na blokadę znaków/słów, np. [carbonchat](https://modrinth.com/plugin/carbon). Sprawdź [carbonchatu](https://github.com/Hexaoxide/Carbon/wiki/Basic-Configuration#chat-filter)
* Możesz również użyć innego namespace jak pisałem powyżej w punkcie 3.


{% endhint %}

#### **3. Ikonka mimo prawidłowej ścieżki się nie pojawia**

{% hint style="info" %}
**Aby rozwiązać ten problem, sprawdź czy każda z poniższych opcji jest prawidłowo ustawiona:**

* Tekstura nie posiada w nazwie spacji
* Tekstura jest w formacie .png
* Tekstura w nazwie nie posiada polskich znaków
* Tekstura w nazwie nie posiada dużych znaków
* Tekstura ma rozmiar nie większy niż 256x256
* Podajesz prawidłową ścieżke do tekstury
* W przypadku użycia innej nazwy/namespace dla pliku font zdefiniowałeś go za pomocą formatu minimessage.
{% endhint %}
{% endstep %}
{% endstepper %}

## Poradnik do tworzenia custom gui

{% hint style="warning" %}
Poradnik dotyczy jedynie wersji 1.19.4 +, na niższych wersjach gracze zobaczą nie przesunięty znak "ベ"
{% endhint %}

{% stepper %}
{% step %}
### Jak cofnąć w lewo twoje gui?

W twoim pliku z fontami musisz umieścić poniższy fragment, on pozwoli tobie na przesunięcie gui 8 pixeli w lewo.<br>

```json
        {
            "type": "space",
            "advances": {
                "ベ": -8
            }
        },
```
{% endstep %}

{% step %}
### Przygotuj strukture pod twoje gui

Bardzo dużo osób przygotowuje texture gui w inny sposób, dlatego uważam, że zrobienie tego poradnika tak by każdemu dopasować nie ma sensu, bo musiałbym to każdemu tłumaczyć w inny sposób, najlepiej jest sugerować się poradnikiem pod custom prefixy i odpowiednio dostosować wartości **ascent**, oraz **height**. Jak ktoś zrozumiał poradnik na tworzenie prefixów to i zrozumie to, w razie problemów będe w stanie pomóc indywidualnie na discordzie.<br>
{% endstep %}
{% endstepper %}
