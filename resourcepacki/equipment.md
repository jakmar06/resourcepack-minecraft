---
description: >-
  W tej części poradnika dowiesz się, jak tworzyć własne modele dla layeru zbroi
  i elytry dla gracza oraz jak implementować niestandardowe zbroje dla mobów.
icon: helmet-battle
cover: ../.gitbook/assets/equipment.png
coverY: 0
---

# Equipment

{% hint style="warning" %}
Poradnik dotyczy jedynie wersji 1.21.2 +, na niższych wersjach gracze nie będą widzieć modelu zbroi.

Zalecane również jest włączenie wymogu pobrania resourcepacka, ponieważ gracze bez pobranego resourepacka będą wiedzieć pusty model bez żadnej textury, tak jakby nie nosili zbroi.
{% endhint %}



***

## Zbroja

### 1. Przygotuj tekstury zbroi

Na początek musisz stworzyć **teksturę/model zbroi**. Najlepiej zrobić to w programie **Blockbench**.

Poniżej znajduje się film pokazujący, jak:

* stworzyć model zbroji,
* zapisać jego texture



{% embed url="https://youtu.be/QDLNrleSITQ" %}

***

### 2. Dodaj tekstury do Resource Packa

Gotową teksturę umieść **dokładnie w poniższej ścieżce**:

```yaml
📁twój_resourcepack
└── 📁assets
    └── 📁twoj_namespace
        └── 📁textures
            └── 📁entity
                └── 📁equipment
                    └── 📁humanoid/humanoid_leggings
                        └── 🧮przykladowa_nazwa.png
```

📌 `twoj_namespace` to namespace Twojego resource packa 📌 `przykladowa_nazwa.png` to tekstura Twojej zbroi

***

### 3. Zdefiniuj zbroje

W tym kroku tworzysz **plik definicji**, który łączy teksturę z itemem.

#### 1. Przejdź do ścieżki i utwórz plik:

```yaml
📁twój_resourcepack
└── 📁assets
    └── 📁twoj_namespace
        └── 📁equipment
            └── 📑przykladowa_nazwa.json
```

***

#### 2. Wklej poniższą zawartość:

```json
{
  "layers": {
    "humanoid": [
      {
        "texture": "twoj_namespace:przykladowa_nazwa"
      }
    ],
    "humanoid_leggings": [
      {
        "texture": "twoj_namespace:przykladowa_nazwa"
      }
    ]
  }
}
```

📌 Ten plik definiuje, jak tekstura ma być używana:

* `humanoid` → hełm, klata, buty
* `humanoid_leggings` → nogawice

***

### 4. Nadaj graczowi zbroje

#### 1. Bez ItemEdit (czyste komendy Minecraft)

Każdy element zbroi nadajesz osobną komendą:

```yaml
1.1 Hełm:
/minecraft:give <nick> minecraft:item[equippable={asset_id: "twoj_namespace:przykladowa_nazwa", slot: "head"}]

1.2 Napierśnik:
/minecraft:give <nick> minecraft:item[equippable={asset_id: "twoj_namespace:przykladowa_nazwa", slot: "chest"}]

1.3 Nogawice:
/minecraft:give <nick> minecraft:item[equippable={asset_id: "twoj_namespace:przykladowa_nazwa", slot: "legs"}]

1.4 Buty:
/minecraft:give <nick> minecraft:item[equippable={asset_id: "twoj_namespace:przykladowa_nazwa", slot: "feet"}]
```

#### 2. Z itemedit

```yaml
1.1 Hełm:
/ie equipment model twoj_namespace:przykladowa_nazwa
/ie equipment slot head

1.2 Napierśnik:
/ie equipment model twoj_namespace:przykladowa_nazwa
/ie equipment slot chest

1.3 Nogawice: 
/ie equipment model twoj_namespace:przykladowa_nazwa
/ie equipment slot legs

1.4 Buty:
/ie equipment model twoj_namespace:przykladowa_nazwa
/ie equipment slot feet
```

📌 `asset_id` musi **idealnie** zgadzać się z nazwą pliku `.json`

***

## Elytra

Proces jest **niemal identyczny** jak przy zbroi. Również:

* bez OptiFine,
* bez pluginów,
* tylko **Minecraft 1.21.2+**.

***

### 1. Przygotuj texture elytry

Ponownie zalecany jest **Blockbench**. Poniższy film pokazuje tworzenie i zapis modelu elytry:

{% embed url="https://youtu.be/jj_5h_ZOC-M" %}

***

### 2. Dodaj teksturę elytry do Resource Packa

Teksturę umieść w dokładnie tej lokalizacji:

```yaml
📁twój_resourcepack
└── 📁assets
    └── 📁twoj_namespace
        └── 📁textures
            └── 📁entity
                └── 📁equipment
                    └── 📁wings
                        └── 🧮przykladowa_nazwa_elytra.png
```

***

### 3. Zdefiniuj elytre

#### 1. Przejdź do ścieżki i utwórz plik:

```yaml
📁twój_resourcepack
└── 📁assets
    └── 📁twoj_namespace
        └── 📁equipment
            └── 📑przykladowa_nazwa_elytra.json
```

***

#### 2. Wklej poniższą zawartość:

```json
{
    "layers": {
        "wings": [
            {
                "texture": "twoj_namespace:przykladowa_nazwa_elytra"
            }
        ]
    }
}
```

📌 `wings` odpowiada wyłącznie za model elytry

***

### 4. Nadaj graczowi elytre

#### 1. Bez ItemEdit (komenda Minecraft):

```yaml
/minecraft:give <nick> minecraft:elytra[equippable={asset_id: "twoj_namespace:przykladowa_nazwa_elytra", slot: "chest"}]
```

#### 2. Z itemedit

```yaml
/ie equipment model twoj_namespace:przykladowa_nazwa_elytra
/ie equipment slot chest
```

## Inne Informacje

1. Dla layera elytry można również dodać layer zbroi, co pozwoli na połączenie elytry z np netherite napierśnikiem :)
2. Inne możliwe compomenty:

2.1 Zbroja dla happy ghasta: `happy_ghast_body`

2.2 Zbroja dla łodzika: `nautilus_body`

2.3 Zbroja dla wilka: `wolf_body`

2.4 Zbroja dla konia: `horse_body`

2.5 Zbroja dla lamy: `llama_body`

2.6 Siodło dla świni: `pig_saddle`

2.7 Siodło dla stridera: `strider_saddle`

2.8 Siodło dla wielbłąda: `camel_saddle`

2.9 Siodło dla konia: `horse_saddle`

2.10 Siodło dla osła: `donkey_saddle`

2.11 Siodło dla muła: `mule_saddle`

2.12 Siodło dla konia szkieleta: `skeleton_horse_saddle`

2.13 Siodło dla konia zombie: `zombie_horse_saddle`

2.14 Siodło dla łodzika: `nautilus_saddle`

2.15 Siodło dla zombie wielbłąda: `camel_husk_saddle`

{% embed url="https://github.com/jakmar06/resourcepack-minecraft/releases/tag/v.1.0.0_Layer" %}
Paczka gotowych assetów
{% endembed %}

