---
description: >-
  W tej sekcji, dowiesz się jak skonfigurować poprawnie LibreLoginProd na twoim
  serwerze proxy.
---

# LibreLoginProd (proxy)

{% stepper %}
{% step %}
## LibreLoginProd (Proxy)

Kompletny poradnik konfiguracji bezpiecznej autoryzacji przy użyciu silnika/pluginu **PicoLimbo** oraz **LibreLoginProd** na proxy Velocity.

***

{% stepper %}
{% step %}
#### 1. Pobranie PicoLimbo

Wybierz i pobierz odpowiednią wersję PicoLimbo dla swojego serwera.

{% embed url="https://modrinth.com/plugin/picolimbo-java-wrapper/versions" %}
Wersja jako plugin Java (Wrapper)
{% endembed %}

{% embed url="https://github.com/Quozul/PicoLimbo/releases" %}
Wersja samodzielna (silnik w Rust lub standalone Java)
{% endembed %}

{% hint style="info" %}
**Wskazówka:** PicoLimbo możesz uruchomić na dwa sposoby: jako plugin `.jar` za pomocą Java Wrappera w folderze serwera proxy lub jako całkowicie osobny, niezależny silnik (np. napisany w Rust).
{% endhint %}
{% endstep %}

{% step %}
#### 2. Instalacja i konfiguracja PicoLimbo

1. Umieść plik `picolimbo` w folderze `plugins` (lub uruchom go jako osobny proces/silnik).
2. Zrestartuj serwer proxy, aby wygenerować niezbędne pliki konfiguracyjne.
3. Dostosuj ustawienia w poniższych plikach konfiguracyjnych (przełącz zakładki):

{% tabs %}
{% tab title="plugins:pico_limbo_java_wrapper/server.toml" %}
```yaml
# Twój dodatkowy port dla serwera limbo (musi być wewnętrzny!)
bind = "0.0.0.0:18000"

[forwarding]
method = "MODERN"
# Alternatywnie możesz użyć: secret = "${FORWARDING_SECRET}"
secret = "twój_forwarding_secret_z_velocity" 
```
{% endtab %}

{% tab title="velocity.toml" %}
```yaml
# Główny port serwera proxy, na który łączą się gracze
bind = "0.0.0.0:25565" 

# Nowoczesny tryb przesyłania danych (wymagany dla wersji 1.13+)
player-info-forwarding-mode = "modern"

# Wyłączenie online-mode, aby wpuścić na serwer graczy Non-Premium
online-mode = false

[servers]
# PAMIĘTAJ: Dla bezpieczeństwa zawsze używaj portów wewnętrznych!
limbo = "10.49.9.37:18000"
lobby = "10.49.9.37:30066"

# Serwer, na który gracz jest kierowany w pierwszej kolejności
try = [
    "lobby"
]
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
#### ⚠️ Ważne bezpieczeństwo (IceHost.pl i inne hostingi)

Podczas tworzenia dodatkowego portu w panelu hostingu, **zawsze wybieraj port wewnętrzny!** Uniemożliwi to intruzom bezpośrednie łączenie się z Twoim serwerem Limbo/Lobby z pominięciem zabezpieczeń serwera proxy.
{% endhint %}

{% hint style="warning" %}
Jeśli decydujesz się na uruchomienie PicoLimbo jako samodzielnego silnika na osobnym serwerze, konfiguracja wygląda identycznie – musisz jedynie pamiętać o przypisaniu odpowiedniego adresu IP i wewnętrznego portu.
{% endhint %}
{% endstep %}

{% step %}
#### 3. Pobranie LibreLoginProd

Pobierz najnowszą wersję wtyczki odpowiedzialnej za obsługę uwierzytelniania.

{% embed url="https://modrinth.com/plugin/libreloginprod" %}
Oficjalna strona na Modrinth
{% endembed %}

{% embed url="https://github.com/Navio1430/LibreLoginProd/releases" %}
GitHub Releases (często zawiera nowsze, testowe wersje rozwojowe)
{% endembed %}

{% hint style="info" %}
Warto sprawdzać zakładkę _Releases_ na GitHubie autora, ponieważ tam świeże poprawki i wersje testowe pojawiają się znacznie szybciej niż na platformie Modrinth.
{% endhint %}
{% endstep %}

{% step %}
#### 4. Instalacja i konfiguracja LibreLoginProd

1. Wrzuć pobrany plik `LibreLoginProd` do folderu `plugins` na swoim serwerze proxy.
2. Wykonaj restart proxy.
3. Skonfiguruj plik `config.conf` zgodnie z poniższym wzorem:

{% tabs %}
{% tab title="plugins:librelogin/config.conf" %}
```hocon
# Nazwa serwera Limbo zdefiniowana wcześniej w velocity.toml
limbo=[
    "limbo"
]

# Główny serwer lobby (punkt startowy)
lobby {
    root=[
        "lobby"
    ]
}

# Uwierzytelnianie hybrydowe (Premium ma UUID z Mojang, Non-Premium generowane lokalnie)
new-uuid-creator=MOJANG

# Automatyczne logowanie i rejestracja dla graczy posiadających oryginalną grę
auto-register=true

# Czy po restarcie przenosić graczy na fallback (domyślnie false - zostają na lobby)
fallback=false 
```
{% endtab %}
{% endtabs %}

***

#### Krok końcowy

Upewnij się, że nazwy serwerów oraz porty w `velocity.toml` pokrywają się z plikiem `config.conf`, a następnie **wykonaj pełny restart serwera proxy**.
{% endstep %}
{% endstepper %}

***

#### Gotowa polska konfiguracja

Jeżeli nie chcesz konfigurować wszystkiego ręcznie od zera, możesz skorzystać z mojego autorskiego spolszczenia i gotowego szablonu:

{% embed url="https://builtbybit.com/resources/libreloginprod-polish-configuration.86717/" %}
Moja publiczna, gotowa konfiguracja dla LibreLoginProd (BuiltByBit)
{% endembed %}
{% endstep %}
{% endstepper %}
