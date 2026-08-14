---
description: >-
  Kompletny poradnik konfiguracji systemu, dzięki któremu gracze będą mogli
  odebrać nagrodę za subsrybcje na Twoim kanale youtube. Wykorzystamy do tego
  plugin Claimo oraz dodatek ClaimoYouTubeAddon.
hidden: true
icon: youtube
---

# Nagroda za subskrybcje na youtube

{% hint style="warning" %}
#### **Wersja serwera oraz klienta**

Poradnik jest tworzony na wersji 1.21.7+ dla serwera, oraz klienta, używanie niższej wersji jest nie zalecane!
{% endhint %}

***

{% stepper %}
{% step %}
## Pobranie wymaganych pluginów

* Pobierz najnowsze wersje pluginu **Claimo** oraz dodatku odpowiedzialnego za integrację z Discordem.

{% embed url="https://builtbybit.com/resources/claimo.115049/history" %}

{% embed url="https://modrinth.com/plugin/claimo/versions" %}

{% embed url="https://github.com/Naimadx123/ClaimoYouTubeAddon" %}

* Umieść oba pliki `.jar` w folderze `plugins`, a następnie wykonaj pełny restart serwera.

{% hint style="info" %}
#### **Pierwsze uruchomienie**

Po pierwszym uruchomieniu pluginy utworzą swoje foldery oraz pliki konfiguracyjne, na ten moment ich nie ruszaj, tylko przejdź do nastepnego kroku.
{% endhint %}
{% endstep %}

{% step %}
## Google Cloud Console

W kolejnym kroku utworzymy klucz API potrzebny do poprawnego działania ClaimoYouTubeAddon

{% stepper %}
{% step %}
### **Otwórz** Google Cloud Console

Przejdź na stronę Google Cloud Console i zaloguj się na swoje konto Google.

{% embed url="https://console.cloud.google.com" %}
{% endstep %}

{% step %}
{% stepper %}
{% step %}
### Utwórz nowy projekt

* Kliknij przycisk pokazany na zrzucie ekranu&#x20;

<figure><img src="../../../.gitbook/assets/obraz (23).png" alt=""><figcaption></figcaption></figure>

**Następnie**

* Rowiń przycisk **administracja**.
* Kliknij przycisk **Utwórz projekt.**

<figure><img src="../../../.gitbook/assets/obraz (24).png" alt=""><figcaption></figcaption></figure>

**Następnie**

* Nazwij swój projekt.
* Kliknij przycisk **Utwórz.**

<figure><img src="../../../.gitbook/assets/obraz (25).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie klucza API

{% stepper %}
{% step %}
### Pasek nawigacji

* Rozwiń ponownie pasek nawigacji
* Rozwiń przycisk **Interfejsy API i usługi.**
*   Kliknij przycisk **Biblioteka**.

    <figure><img src="../../../.gitbook/assets/obraz (26).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
### Wyszukaj i włącz Youtube Data API v3

* W wyszukiwarce wpsz **youtube data api v3**
* Wybierz zaznaczoną opcje.

<figure><img src="../../../.gitbook/assets/obraz (30).png" alt=""><figcaption></figcaption></figure>

* <mark style="color:green;">Włącz</mark> YouTube Data API v3

<figure><img src="../../../.gitbook/assets/obraz (29).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Utwórz dane logowania

* Kliknij przycisk **Utwórz dane logowania**

<figure><img src="../../../.gitbook/assets/obraz (31).png" alt=""><figcaption></figcaption></figure>

**Następnie**

* Wybierz w typie danych logowania, typ **Publiczne dane**
* Kliknij przycisk **dalej**

<figure><img src="../../../.gitbook/assets/obraz (32).png" alt=""><figcaption></figcaption></figure>

**Następnie**

* Skopiuj swój klucz API
* Kliknij przycisk **Gotowe**

<figure><img src="../../../.gitbook/assets/obraz (33).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
#### **Nie udostępniaj twojego klucza api!**

nie rob tego dzieki, gpt cos wymysli
{% endhint %}


{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}

{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Konfiguracja Claimo

{% stepper %}
{% step %}
### Konfiguracja Claimo w plikach

Skonfiguruj poniżej wymienione opcje, tak jak to jest podane niżej.

{% tabs %}
{% tab title="plugins:Claimo/config.yml" %}
```yaml
# Komenda z pluginu Claimo odpowiadająca za kody
command: kod

# Opcja odpowiadająza za gui z dostepnymi kodami, ja zalecam jej wyłaczenie,
# ale samo jej ustawienienie nie ma żadnego wpływu na działanie pluginu.
gui-list-enabled: false
```
{% endtab %}

{% tab title="plugins:ClaimoDiscordAddon/config.yml" %}
```yaml
# Komenda z pluginu odpowiadająca za zarządzanie swoim połączeniem z discordem.
command: nagrodadiscord

bot:
  # Twój token bota, który zapisałeś wcześniej.
  token: "MTUzNzg1ODgwMjI1NzM3MTMyMA.GjowV7.6yogdr8JxESuggeSOppO0yCo0PQORgctfiaJ0w"
  # ID twojego serwera discord.
  guild-id: "877884416066727946"
 # Dodatkowe uprawnienia określające, jakie informacje bot może odczytywać
 # z Twojego serwera Discord. Wyłączenie ich może sprawić, że niektóre wymagania,
 # np. sprawdzanie statusu użytkownika, jego ról lub boosta serwera, nie będą działać.
  intents:
    # Pozwala botowi sprawdzać statusy użytkowników.
    presences: true
    # Pozwala botowi sprawdzać członków serwera, ich role i ulepszenia serwera.
    members: true

discord:
  # Kanał na który ma być wysyłana wiadomość z przyciskiem do połączenia
  # konta discord z kontem minecraft.
  panel-channel-id: "1537892477753761862"
```

{% hint style="warning" %}
Nie udostępniaj publicznie pliku konfiguracyjnego, jeżeli znajduje się w nim token bota.
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Konfiguracja Claimo w Minecraft

{% stepper %}
{% step %}
### Wysłanie panelu z przyciskiem na discorda

* Wpisz komendę **/nagrodadiscord panel**

<figure><img src="../../../.gitbook/assets/obraz (21).png" alt=""><figcaption></figcaption></figure>

* Sprawdź, czy bot wysłał wiadomość na kanał

<figure><img src="../../../.gitbook/assets/obraz (22).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Konfiguracja nagrody

* Wpisz komendę **/claimo create**
* W polu **Code Name** wpisz **discord**
* W polu **Command,** wpisz komendę jaka ma zostać wykonana podczas odbierania nagrody
* Pozostaw opcję Run as console <mark style="color:green;">Włączoną</mark>
* Opcję **Hide from list** ustaw wedle swojego uznania (wyłączone nie będzie tabować tej nagrody pod komendą /kod discord)
* W polu Reedem **Command** wpisz **/odbierzdiscord**
* Ustaw ile razy chcesz by gracz mógł odebrać tą nagrodą pod opcją **Max Uses**

{% hint style="warning" %}
Czasem może pojawić się problem z wybraniem 1, jeżeli taki problem wystąpi możesz tą opcję zmienić w configu pluginu Claimo.

{% code title="plugins:Claimo/vouchers/discord.yml" %}
```yml
cmd: say UDAŁO CI SIĘ ODEBRAĆ NAGRODE %player_name%
redeem-command: odbierzdiscord
console: true
hide: true
limit:
  mode: per-player
  amount: 1
requirements:
- type: discord_linked
- type: discord_member
```
{% endcode %}
{% endhint %}

* <mark style="color:green;">Włącz</mark> opcję **Limit is per player**
* <mark style="color:green;">Włącz</mark> opcję discord\_linked
* <mark style="color:green;">Włącz</mark> opcję discord\_member

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FygQAWawEAObMdlBBqapM%2Fuploads%2Fdi0WV1yOfUDhjnqydTA6%2F2026-08-14%2021-34-07.mp4?alt=media&token=aba4076e-a6f4-44fc-a5e7-7d3ea96b4fc4" %}

{% hint style="info" %}
Możesz też dodać różne wymagania, np posiadanie boosta na discordzie, czy czas w którym się jest na discordzie/przegrany czas na serwerze, ale to już ustawiasz wedle swojego uznania.
{% endhint %}

* Zrestartuj serwer&#x20;

{% hint style="info" %}
Aby komenda **/odbierzdiscord** działała wymagany jest pełny restart serwera, bez restartu można użyć komendy **/kod discord**
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Sprawdź czy wszystko działa

* Wpisz komendę **/odbierzdiscord** i sprawdź czy plugin poinformuje ciebie o braku spełniania wymagań
* Wpisz komendę **/nagrodadiscord link**
* **Skopiuj kod** który otrzymałeś
* Przejdź do discorda, na kanał na którym został wysłany panel i wklej wcześniej otrzymany kod
* Odbierz nagrodę komendą **/odbierzdiscord**

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FygQAWawEAObMdlBBqapM%2Fuploads%2F0ekDrhfIklUD1bfUb2DZ%2F2026-08-14%2021-48-49.mp4?alt=media&token=0734215a-d872-4a5e-803f-2417ddaea95f" %}
{% endstep %}
{% endstepper %}
