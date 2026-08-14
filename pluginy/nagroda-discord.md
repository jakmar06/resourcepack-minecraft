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
{% endstepper %}
{% endstep %}

{% step %}
### Konfiguracja pluginów

Po utworzeniu i skonfigurowaniu bota możesz przejść do konfiguracji **ClaimoDiscordAddon**.

Otwórz folder pluginu utworzony po pierwszym uruchomieniu serwera, a następnie przejdź do jego pliku konfiguracyjnego.

W konfiguracji należy:

1. wkleić wcześniej skopiowany token bota,
2. podać identyfikator serwera Discord,
3. skonfigurować wymaganą rolę lub kanał,
4. ustawić nagrodę przyznawaną graczowi,
5. zapisać zmiany i wykonać pełny restart serwera.

{% hint style="warning" %}
Nie udostępniaj publicznie pliku konfiguracyjnego, jeżeli znajduje się w nim token bota.
{% endhint %}
{% endstep %}
{% endstepper %}

