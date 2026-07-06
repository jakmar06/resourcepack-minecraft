---
description: >-
  W tej sekcji, dowiesz się jak skonfigurować poprawnie LibreLoginProd na twoim
  serwerze proxy.
---

# LibreLoginProd (proxy)

{% stepper %}
{% step %}
### Pobranie pluginu LibreLoginProd

Pierwszym krokiem będzie pobranie pluginu LibreLoginProd.

{% embed url="https://modrinth.com/plugin/libreloginprod" %}

{% embed url="https://github.com/Navio1430/LibreLoginProd/releases" %}

{% hint style="info" %}
Powyżej podałem 2 linki, ponieważ plugin często na githubie ma jedną, czy kilka nowszych wersji niż na modrinthie.
{% endhint %}
{% endstep %}

{% step %}
### Instalacja, oraz konfiguracja PicoLimbo

* Umieść plugin `LibreLoginProd` w folderze `plugins`&#x20;
* Zrestartuj serwer
* Gdy plugin zainstaluje się na serwerze przejdź do konfguracji velocity, oraz konfiguracji pluginu i zmień poniżej wymienione opcje

{% tabs %}
{% tab title="plugins:pico_limbo_java_wrapper/server.toml" %}
{% code title="plugins:pico_limbo_java_wrapper/server.toml" fullWidth="false" %}
```yaml
## tutaj ustawiasz twój dodatkowy port dla serwera limbo
bind = "0.0.0.0:18000"
[forwarding]
method = "MODERN"
## alternatywnie możesz podać ## secret = "${FORWARDING_SECRET}" i sprawdzić czy działa.
secret = "twój forwarding.secret" 
```
{% endcode %}

{% hint style="info" %}
## Tworzenie dodatkowego portu na hostingu icehost.pl

<mark style="color:$danger;">Pamiętaj, podczas tworzenia portu musisz dla bezpieczeństwa twojego serwera podać port wewnętrzny!</mark>

![](<../../.gitbook/assets/obraz (6).png>)
{% endhint %}
{% endtab %}

{% tab title="velocity.toml" %}
{% code title="home:velocity.toml" fullWidth="false" %}
```yaml
## tutaj ustawiasz port dla twojego serwera
bind = "0.0.0.0:25565" 
## tutaj ustawiasz nowoczesny typ przesyłu danych "modern", który działa dla serwerów 1.13+ 
player-info-forwarding-mode = "modern"
## tutaj musisz wyłaczyć online mode, by gracze non premium mogli się łączyć z twoim serwerem
online-mode = false

## Tutaj, dodajesz twoje serwery do proxy
[servers]
limbo = "10.49.9.37:18000"
lobby = "10.49.9.37:30066"

## Tutaj podajesz serwery, na który mają się łączyć gracze po restarcie trybu, najlepiej w przypadku braku 
## kolejki dodać tutaj sam serwer lobby, ponieważ po restarcie gracze nie będą mogli ponownie wrócic na tryb.
try = [
    "lobby"
]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}
