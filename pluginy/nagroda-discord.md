---
description: >-
  W tej sekcji, dowiesz się jak za pomocą pluginu Claimo, stworzyć nagrodę za
  dołączenie na discorda.
hidden: true
icon: discord
---

# Nagroda discord

{% stepper %}
{% step %}
## Pobranie pluginów

Pierwszym krokiem będzie pobranie potrzebnych pluginów, w tym celu będziesz musiał pobrać plugin claimo, oraz Claimo Discord addon.

{% embed url="https://builtbybit.com/resources/claimo.115049/history" %}

{% embed url="https://github.com/Naimadx123/ClaimoDiscordAddon/releases" %}
{% endstep %}

{% step %}
## Discord Developers

Drugim krokiem będzie stworzenie bota na stronie discorda

{% stepper %}
{% step %}
#### Wejdź na strone dla developerów discorda

{% embed url="https://discord.com/developers/applications" %}
{% endstep %}

{% step %}
### Stwórz konto bota

{% stepper %}
{% step %}
#### Nowa aplikacja

Kliknij przycisk "nowa aplikacja"\
![](<../.gitbook/assets/obraz (10).png>)
{% endstep %}

{% step %}
#### Stwórz nową aplikacje

* Nazwij swojego bota
* Wybierz zespół w którym ma się znajdować, np "Minecraf wiki" (o ile taki zespół wcześniej utworzyłeś)
* Zaakceptuj zasady dotyczące aplikacji&#x20;
* Kliknij przycisk stwórz

<figure><img src="../.gitbook/assets/obraz (11).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
### Konfiguracja bota

{% stepper %}
{% step %}
#### Zakładka instalacja

* Zaznacz, by bot mógł być zainstalowany tylko na serwerach

<figure><img src="../.gitbook/assets/obraz (12).png" alt=""><figcaption></figcaption></figure>

* Wyłącz link do zaproszenia bota w jego profilu

<figure><img src="../.gitbook/assets/obraz (14).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
#### Zakładka bot&#x20;

* <mark style="color:red;">Wyłącz opcję</mark> "Publiczny bot"&#x20;
* <mark style="color:green;">Włącz opcję</mark> "Uprawnienie intent dot. obecności"
* <mark style="color:green;">Włącz opcję</mark> "Uprawnienie intent dot. członków serwera"
* <mark style="color:green;">Włącz opcję</mark> "Uprawnienie intent dot. treści wiadomości"

<figure><img src="../.gitbook/assets/obraz (15).png" alt=""><figcaption></figcaption></figure>

* Zresetuj token bota

<figure><img src="../.gitbook/assets/obraz (16).png" alt=""><figcaption></figcaption></figure>

* Skopiuj token bota i zachowaj go w bezpieczym miejscu na później

{% hint style="danger" %}
#### Nie udostępniaj nikomu tokenu bota!

Jeżeli token bota wycieknie, oraz dostanie go nieodpowiednia osoba otrzyma pełen dostęp do twojego serwera discord! Dla bezpieczeństwa zalecane jest ustawienie tylko niezbędnych uprawień w ustawieniach roli na discordzie.
{% endhint %}
{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}
{% endstep %}

{% step %}
## Konfiguracja pluginu


{% endstep %}
{% endstepper %}
