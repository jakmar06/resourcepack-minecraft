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

asdsad

















































## Nagroda za subskrypcję na YouTube

Kompletny poradnik konfiguracji systemu, dzięki któremu gracze będą mogli odebrać nagrodę za zasubskrybowanie wskazanego kanału YouTube. Wykorzystamy do tego plugin **Claimo** oraz dodatek **ClaimoYouTubeAddon**.

{% hint style="warning" %}
**Wersja serwera oraz klienta**

Poradnik został przygotowany dla wersji **1.21.7 lub nowszej**. Na starszych wersjach część funkcji, takich jak nowoczesne okna dialogowe, może być niedostępna.
{% endhint %}

***

{% stepper %}
{% step %}
### Pobranie wymaganych pluginów

Pobierz najnowszą wersję pluginu **Claimo** z jednego z poniższych źródeł:

Następnie pobierz dodatek odpowiedzialny za integrację z YouTube:

Umieść oba pliki `.jar` w folderze `plugins`, a następnie wykonaj pełny restart serwera.

{% hint style="info" %}
**Pierwsze uruchomienie**

Po pierwszym uruchomieniu pluginy utworzą swoje foldery oraz pliki konfiguracyjne. Na razie ich nie zmieniaj — najpierw utworzymy klucz YouTube Data API.
{% endhint %}
{% endstep %}

{% step %}
### Google Cloud Console

W tym kroku utworzymy klucz API potrzebny do automatycznego sprawdzania subskrypcji oraz komentarzy graczy.

{% stepper %}
{% step %}
#### **Otwórz Google Cloud Console**

Przejdź na stronę Google Cloud Console i zaloguj się na swoje konto Google.
{% endstep %}

{% step %}
#### Utwórz nowy projekt

Kliknij przycisk wyboru projektu zaznaczony na poniższym zrzucie ekranu.

Następnie:

* rozwiń sekcję **Administracja**,
* kliknij przycisk **Utwórz projekt**.

Wprowadź dowolną nazwę projektu, na przykład `Minecraft YouTube`, a następnie kliknij przycisk **Utwórz**.

{% hint style="info" %}
Po utworzeniu projektu upewnij się, że został on wybrany jako aktualnie używany projekt.
{% endhint %}
{% endstep %}

{% step %}
#### Tworzenie klucza API

{% stepper %}
{% step %}
#### Otwórz bibliotekę interfejsów API

Rozwiń pasek nawigacji znajdujący się w lewym górnym rogu strony.

Następnie:

* rozwiń sekcję **Interfejsy API i usługi**,
* wybierz opcję **Biblioteka**.
{% endstep %}

{% step %}
#### Włącz YouTube Data API v3

W wyszukiwarce wpisz `YouTube Data API v3`, a następnie wybierz wskazany interfejs API.

Kliknij przycisk <mark style="color:green;">**Włącz**</mark>.
{% endstep %}

{% step %}
#### Utwórz dane logowania

Po włączeniu YouTube Data API v3 kliknij przycisk **Utwórz dane logowania**.

Jako typ używanych danych wybierz **Dane publiczne**, a następnie kliknij przycisk **Dalej**.

Skopiuj wygenerowany klucz API i zachowaj go w bezpiecznym miejscu. Będzie potrzebny podczas konfiguracji dodatku.

Na końcu kliknij przycisk **Gotowe**.

{% hint style="danger" %}
**Nie udostępniaj nikomu klucza API!**

Klucz API pozwala korzystać z limitu zapytań przypisanego do Twojego projektu Google Cloud. Jeżeli trafi w niepowołane ręce, ktoś może wykorzystać cały dostępny limit, przez co sprawdzanie subskrypcji i komentarzy na serwerze przestanie działać.

Jeżeli klucz zostanie ujawniony, usuń go w Google Cloud Console i wygeneruj nowy.
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Konfiguracja pluginów

Po utworzeniu klucza API możemy przejść do konfiguracji **Claimo** oraz **ClaimoYouTubeAddon**.

{% stepper %}
{% step %}
#### Konfiguracja Claimo

Otwórz plik `plugins/Claimo/config.yml` i skonfiguruj poniższe opcje:

{% code title="plugins/Claimo/config.yml" %}
```yaml
# Główna komenda pluginu służąca do odbierania nagród.
command: kod

# Lista nagród dostępna w GUI.
# Jeżeli jej nie potrzebujesz, możesz ją wyłączyć.
gui-list-enabled: false
```
{% endcode %}

{% hint style="info" %}
Wyłączenie `gui-list-enabled` nie wpływa na działanie nagród. Gracze nadal mogą odbierać je za pomocą przypisanych komend.
{% endhint %}
{% endstep %}

{% step %}
#### Konfiguracja ClaimoYouTubeAddon

Otwórz plik `plugins/ClaimoYouTubeAddon/config.yml`.

Jeżeli korzystasz z jednego serwera, możesz pozostawić zapis danych w pliku YAML. W sekcji `verifier` ustaw weryfikację przez API i wklej wcześniej wygenerowany klucz.

{% code title="plugins/ClaimoYouTubeAddon/config.yml" %}
```yaml
# Miejsce zapisywania połączeń kont Minecraft z kanałami YouTube.
# Przy jednym serwerze możesz pozostawić typ yaml.
storage:
  type: yaml
  host: localhost
  port: 3306
  database: claimoyt
  username: root
  password: ""
  table-prefix: claimoyt_
  pool-size: 10

# Sposób sprawdzania aktywności graczy na YouTube.
verifier:
  # Weryfikacja za pomocą YouTube Data API v3.
  type: api

  # Wklej tutaj klucz utworzony w Google Cloud Console.
  api-key: "TWÓJ_KLUCZ_API"

  # Maksymalna liczba stron komentarzy sprawdzanych przez plugin.
  comment-max-pages: 5

  # Wymaga potwierdzenia, że kanał naprawdę należy do gracza.
  require-verified-ownership: true

  manual:
    # Gracz musi potwierdzić własność kanału kodem w jego opisie.
    auto-verify-ownership: false
```
{% endcode %}

{% hint style="info" %}
**Co plugin może sprawdzić automatycznie?**

* **Subskrypcję** — tylko jeśli gracz ma publiczną listę subskrypcji.
* **Komentarz** — plugin może znaleźć komentarz gracza pod wskazanym filmem.
* **Polubienie filmu** — YouTube nie udostępnia informacji o osobach, które polubiły film, dlatego polubienia zawsze wymagają ręcznego zatwierdzenia przez administrację.

Jeżeli wystąpi problem z API lub gracz ma prywatne subskrypcje, weryfikacja zostanie przekazana do ręcznego zatwierdzenia.
{% endhint %}

{% hint style="warning" %}
Nie udostępniaj publicznie pliku konfiguracyjnego, jeżeli znajduje się w nim Twój klucz API.
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Konfiguracja nagrody

Teraz utworzymy nagrodę, którą gracz będzie mógł odebrać po zasubskrybowaniu wskazanego kanału YouTube.

{% stepper %}
{% step %}
#### Utwórz nową nagrodę

Wpisz na serwerze komendę:

```
/claimo create
```

Następnie skonfiguruj nagrodę:

* w polu **Code Name** wpisz `youtube`,
* w polu **Command** podaj komendę wykonywaną po odebraniu nagrody,
* pozostaw opcję **Run as console** <mark style="color:green;">włączoną</mark>,
* opcję **Hide from list** ustaw według własnego uznania,
* w polu **Redeem Command** wpisz `odbierzyoutube`,
* w polu **Max Uses** ustaw `1`,
* <mark style="color:green;">włącz</mark> opcję **Limit is per player**.
{% endstep %}

{% step %}
#### Dodaj wymaganie subskrypcji

Dodaj do nagrody wymaganie:

```
youtube_subscribe
```

W polu `target` podaj kanał, który gracz ma zasubskrybować. Możesz użyć:

* pełnego adresu kanału,
* nazwy kanału rozpoczynającej się od `@`,
* identyfikatora kanału rozpoczynającego się od `UC`.

Przykładowy adres:

```
https://www.youtube.com/@twojkanal
```

{% hint style="info" %}
ClaimoYouTubeAddon udostępnia również wymagania `youtube_comment` oraz `youtube_like`. W ich przypadku jako `target` podaj adres odpowiedniego filmu.
{% endhint %}
{% endstep %}

{% step %}
#### Gotowy plik nagrody

Po zapisaniu nagrody jej plik powinien wyglądać podobnie do poniższego:

{% code title="plugins/Claimo/vouchers/youtube.yml" %}
```yaml
# Komenda wykonywana po odebraniu nagrody.
cmd: say %player_name% odebrał nagrodę za subskrypcję!

# Osobna komenda służąca do odebrania tej nagrody.
redeem-command: odbierzyoutube

# Wykonuje komendę jako konsola.
console: true

# Ukrywa nagrodę na liście dostępnych kodów.
hide: true

# Każdy gracz może odebrać nagrodę tylko jeden raz.
limit:
  mode: per-player
  amount: 1

# Gracz musi zasubskrybować wskazany kanał.
requirements:
  - type: youtube_subscribe
    target: "https://www.youtube.com/@twojkanal"
```
{% endcode %}

{% hint style="warning" %}
Jeżeli nie możesz ustawić jednego użycia za pomocą kreatora, zatrzymaj serwer i zmień wartość `amount` na `1` bezpośrednio w pliku nagrody.
{% endhint %}
{% endstep %}

{% step %}
#### Zrestartuj serwer

Po zapisaniu konfiguracji wykonaj pełny restart serwera.

{% hint style="info" %}
Pełny restart jest wymagany, aby plugin zarejestrował komendę `/odbierzyoutube`. Przed restartem nagrodę można nadal odebrać główną komendą `/kod youtube`.
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Połączenie kanału YouTube przez gracza

Każdy gracz musi połączyć swoje konto Minecraft z własnym kanałem YouTube.

{% stepper %}
{% step %}
#### Połącz kanał

Gracz powinien wpisać:

```
/youtube link @nazwa_kanalu
```

Zamiast `@nazwa_kanalu` może również wkleić pełny adres swojego kanału YouTube.

Plugin wygeneruje jednorazowy kod weryfikacyjny, na przykład:

```
YT-ABC123
```
{% endstep %}

{% step %}
#### Dodaj kod do opisu kanału

Skopiuj otrzymany kod i dodaj go do opisu swojego kanału YouTube.

Po zapisaniu zmian wróć na serwer i wpisz:

```
/youtube verify
```

Plugin sprawdzi opis kanału i potwierdzi, że należy on do gracza.

{% hint style="info" %}
Po poprawnym zweryfikowaniu kanału kod można usunąć z jego opisu.
{% endhint %}
{% endstep %}

{% step %}
#### Ustaw subskrypcje jako publiczne

Aby plugin mógł automatycznie sprawdzić subskrypcję, lista subskrybowanych kanałów gracza musi być publiczna.

Jeżeli subskrypcje są prywatne, plugin nie będzie mógł potwierdzić ich przez YouTube Data API i konieczne będzie ręczne zatwierdzenie przez administratora.
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Sprawdzenie działania nagrody

Na koniec sprawdź cały proces z konta gracza:

1. Wpisz `/youtube link @nazwa_kanalu`, aby połączyć kanał.
2. Dodaj otrzymany kod do opisu kanału.
3. Wpisz `/youtube verify`, aby potwierdzić własność kanału.
4. Zasubskrybuj kanał wskazany w konfiguracji nagrody.
5. Upewnij się, że lista subskrypcji jest publiczna.
6. Wpisz `/odbierzyoutube`.

Jeżeli wszystkie wymagania zostały spełnione, plugin wykona komendę przypisaną do nagrody.

{% hint style="warning" %}
YouTube może potrzebować chwili na zaktualizowanie informacji o subskrypcji. Jeżeli nagroda nie zostanie przyznana od razu, odczekaj chwilę i spróbuj ponownie.
{% endhint %}
{% endstep %}
{% endstepper %}

***
