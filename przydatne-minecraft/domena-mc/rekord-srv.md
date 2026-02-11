---
description: >-
  Poniżej znajdziesz instrukcję, jak skonfigurować domenę poprzez rekord SRV,
  aby gracze mogli połączy się przez nią do twojego serwera. (poradnik dotyczy
  cloudflare).
---

# Gdy posiadasz serwer zarządzany z współdzielonym ip

{% stepper %}
{% step %}
### STREFA DNS

Przejdź do zakładki **Records** w kategorii **DNS**.

<figure><img src="../../.gitbook/assets/cloudflare-records (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie i konfiguracja rekordu SRV

Kolejnym krokiem jest utworzenie nowego rekordu **SRV**, który umożliwi poprawne przekierowanie domeny na serwer Minecraft.\
**Name**\
Wpisz: `_minecraft._tcp` \
**Priority**\
Ustaw Wartość: `1`\
**Weight**\
Ustaw Wartość: `1` \
**Port**\
Wpisz port twojego serwera. Port znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera, obok adresu IP. np: `pl06.icehost.pl:50038`

{% hint style="info" %}
&#x20;W moim przypadku portem jest `50038`
{% endhint %}
{% endstep %}

{% step %}
**Target**\
W tym polu wpisz ip twojego serwera. Ip znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera np. `pl06.icehost.pl`&#x20;

{% hint style="info" %}
W moim przypadku targetem jest: `pl06.icehost.pl`&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/cloudflare-create-rekord-srv (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Połącz się z twoim serwerem

Jeżeli wykonałeś wszystko poprawnie powinieneś móc połączyć się już z twoim serwerem.

{% hint style="warning" %}
Czasami podpięcie domeny może zająć dłuższy okres czasu (czasem nawet 48 godzin w najgorszych przypadkach). Jeżeli odrazu nie będziesz mógł się połączyć z serwerem nie panikuj, odczekaj chwile.
{% endhint %}
{% endstep %}
{% endstepper %}
