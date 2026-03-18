---
description: >-
  W tej części strony znajdziesz odpowiedź na często zadawane pytania. (Każde
  pytanie dotyczy najnowszej wersji serwera)
icon: question
---

# Często zadawane pytania

## Whitelista

***

#### Jak włączyć whiteliste?

* Zrobisz to za pomocą komendy `/whitelist on`

#### Jak wyłączyć whiteliste?

* Zrobisz to za pomocą komendy `/whitelist off`

#### Jak dodać gracza do whitelisty?

* Zrobisz to za pomocą komendy `/whitelist add <gracz>`

#### Jak usunąć gracza z whitelisty?

* Zrobisz to za pomocą komendy `/whitelist remove <gracz>`

## Nether

***

#### Jak usunąć nether?

* Nether wyłączysz w konfiguracji papera.

{% code title="config/paper-global.yml" %}
```yml
misc:
  enable-nether: false
```
{% endcode %}

#### Jak zablokować wejście do netheru?

* Możesz to zrobić za pomocą komendy `/gamerule allow_entering_nether_using_portals false`

## End

***

#### Jak usunąć end?

* End wyłączasz w konfiguracji bukkita.

{% code title="bukkit.yml" %}
```yml
settings:
  allow-end: false
```
{% endcode %}

## Kolizje

***

#### Jak wyłączyć kolizje?

* Kolizje wyłączasz w konfiguracji papera.

{% code title="config/paper-global.yml" %}
```yml
collisions:
  enable-player-collisions: false
```
{% endcode %}

## Pusty świat

***

#### Jak zrobić pusty świat? (Void)

* Pusty świat ustawiasz w głównej konfiguracji  serwera.

{% code title="server.properties" %}
```yml
level-type=minecraft\:flat
generator-settings={"biome"\:"minecraft\:the_void","layers"\:[]}
```
{% endcode %}

***

#### Jak dodać ikone dla twojego serwera?

* Aby dodać ikone dla twojego serwera, stwórz logo o wymiarach maksymalnie 64x64 oraz nazwij go `server-icon.png`

Poniżej podsyłam stronę, która przekonwertuje twoje logo do prawidłowych rozmiarów

{% embed url="https://mcutils.com/server-icon-converter" %}
