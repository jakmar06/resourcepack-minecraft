---
description: >-
  Kompletny poradnik konfiguracji systemu, dzięki któremu gracze będą mogli
  odebrać nagrodę za dołączenie na Twój serwer Discord. Wykorzystamy do tego
  plugin Claimo oraz dodatek ClaimoDiscordAddon.
hidden: true
icon: discord
---

# Nagroda za dołączenie na Discorda

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

{% embed url="https://github.com/Naimadx123/ClaimoDiscordAddon/releases" %}

* Umieść oba pliki `.jar` w folderze `plugins`, a następnie wykonaj pełny restart serwera.

{% hint style="info" %}
#### **Pierwsze uruchomienie**

Po pierwszym uruchomieniu pluginy utworzą swoje foldery oraz pliki konfiguracyjne, na ten moment ich nie ruszaj, tylko przejdź do nastepnego kroku.
{% endhint %}
{% endstep %}

{% step %}
## Discord Developer Portal

W kolejnym kroku utworzymy aplikację oraz konto bota, z którego będzie korzystać **ClaimoDiscordAddon**.

{% stepper %}
{% step %}
### **Otwórz Discord Developer Portal**

Przejdź na stronę Discord Developer Portal i zaloguj się na swoje konto Discord.

{% embed url="https://discord.com/developers/applications" %}
{% endstep %}

{% step %}
{% stepper %}
{% step %}
### **Utwórz nową aplikację**

*   Kliknij przycisk **Nowa Aplikacja**.<br>

    <figure><img src="../.gitbook/assets/obraz (10).png" alt=""><figcaption></figcaption></figure>

**Następnie:**

* Wprowadź nazwę aplikacji, na przykład nazwę swojego serwera.
* Opcjonalnie wybierz zespół, do którego ma należeć aplikacja.
* Zaakceptuj regulamin Discorda.
* Kliknij przycisk **Stwórz**.

<figure><img src="../.gitbook/assets/obraz (11).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Konfiguracja Bota

{% stepper %}
{% step %}
### **Skonfiguruj instalację bota**

Po utworzeniu aplikacji przejdź do zakładki **Instalacja**.

* Ustaw możliwość instalowania bota wyłącznie na serwerach Discord.

<figure><img src="../.gitbook/assets/obraz (12).png" alt=""><figcaption></figcaption></figure>

* Następnie wyłącz publiczny link instalacyjny widoczny na profilu bota.

<figure><img src="../.gitbook/assets/obraz (14).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### **Skonfiguruj ustawienia bota**

Przejdź do zakładki **Bot** i ustaw następujące opcje:

* <mark style="color:red;">Wyłącz</mark> opcję **Publiczny bot.**
* <mark style="color:green;">Włącz</mark> opcję **Intent dot. obecności**.
* <mark style="color:green;">Włącz</mark> opcję **Intent dot. członków serwera.**
* <mark style="color:green;">Włącz</mark> opcję **Intent dot. treści wiadomości.**

<figure><img src="../.gitbook/assets/obraz (15).png" alt=""><figcaption></figcaption></figure>

#### **Wygeneruj token bota**

W zakładce **Bot** znajdź sekcję **Token**, a następnie kliknij przycisk **Reset Token**.

* Skopiuj wygenerowany token i zachowaj go w bezpiecznym miejscu. Będzie potrzebny podczas konfiguracji pluginu.

<figure><img src="../.gitbook/assets/obraz (16).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
#### **Nie udostępniaj nikomu tokenu bota!**

Jeżeli token bota wycieknie i otrzyma go niepowołana osoba, może ona przejąć kontrolę nad botem oraz wykorzystać wszystkie przypisane mu uprawnienia.

Jeżeli token zostanie ujawniony, natychmiast wygeneruj nowy za pomocą przycisku **Zresetuj Token**.
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Zaproszenie bota

{% stepper %}
{% step %}
### Stworzenie linku z zaproszeniem

W zakładce **OAuth2** znajdź sekcję **Generator adresu URL OAuth2,** a następnie kliknij okienko **BOT.**

<figure><img src="../.gitbook/assets/obraz (18).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
#### **Uprawnienia bota**

Możesz przypisać również tutaj uprawnienia, jakie bot będzie mial po dołączeniu na serwer według własnego uznanania, ja zalecam nie dodawania tutaj uprawnień administratora.
{% endhint %}
{% endstep %}

{% step %}
### Skopiuj poniżej wygenerowany link

<figure><img src="../.gitbook/assets/obraz (19).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Dodanie bota na serwer

Otwórz link w nowej karcie, oraz wybierz serwer na ktory ma zostać dodany bot

<figure><img src="../.gitbook/assets/obraz (20).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
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

<figure><img src="../.gitbook/assets/obraz (21).png" alt=""><figcaption></figcaption></figure>

* Sprawdź, czy bot wysłał wiadomość na kanał

<figure><img src="../.gitbook/assets/obraz (22).png" alt=""><figcaption></figcaption></figure>
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

[https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FygQAWawEAObMdlBBqapM%2Fuploads%2Fdi0WV1yOfUDhjnqydTA6%2F2026-08-14%2021-34-07.mp4?alt=media\&token=aba4076e-a6f4-44fc-a5e7-7d3ea96b4fc4](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FygQAWawEAObMdlBBqapM%2Fuploads%2Fdi0WV1yOfUDhjnqydTA6%2F2026-08-14%2021-34-07.mp4?alt=media\&token=aba4076e-a6f4-44fc-a5e7-7d3ea96b4fc4)

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
{% endstepper %}

