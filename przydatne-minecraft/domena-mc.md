---
description: >-
  Poniżej znajdziesz instrukcję, jak skonfigurować domenę, aby kierowała ruch do
  twojego serwera Minecraft. (cloudflare)
icon: star-exclamation
---

# Podłączanie domeny do serwera Minecraft

{% stepper %}
{% step %}
### Strefa DNS

Przejdź do zakładki **Records** w kategorii **DNS**.

<figure><img src="../.gitbook/assets/obraz.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie rekordu

Stwórz nowy rekord typu A

<figure><img src="../.gitbook/assets/obraz (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Ustawianie rekordu typu A

Po utworzeniu rekordu typu **A** należy poprawnie skonfigurować jego podstawowe parametry.\
\
**Name**\
Jako nazwę rekordu zaleca się ustawić znak: `@` Lub wpisać pełną nazwę swojej domeny (np.`hypixel.net`)\
**IPv4 Address**\
W tym polu wpisz **ip numeryczne** twojego serwera. Ip znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera np. `2137.420.69.67`

<figure><img src="../.gitbook/assets/obraz (2).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
{% hint style="warning" %}
Niektóre hostingi oferują subdomeny, w takim przypadku zalecane jest pominięcie tworzenia rekordu A. Wystarczy jedynie w rekordzie SRV w zakładce "target" ustawić twoją subdomene.
{% endhint %}

### Tworzenie i konfiguracja rekordu SRV

Kolejnym krokiem jest utworzenie nowego rekordu **SRV**, który umożliwi poprawne przekierowanie domeny na serwer Minecraft.\
\
**Name**\
Wpisz: `_minecraft._tcp` \
**Priority**\
Ustaw Wartość: `1`\
**Weight**\
Ustaw Wartość: `1` \
**Port**\
Wpisz port twojego serwera. Port znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera, obok adresu IP. np: `2137.420.69.67:25565`

{% hint style="info" %}
&#x20;W tym przypadku portem jest `25565`
{% endhint %}

**Target**\
Wpisz nazwę rekordu A, który został utworzony wcześniej.

{% hint style="info" %}
W moim przypadku targetem jest: `hypixel.net`&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/obraz (4).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Połącz się z twoim serwerem

Jeżeli wykonałeś wszystko poprawnie powinieneś móc połączyć się już z twoim serwerem.

{% hint style="warning" %}
Czasami podpięcie domeny może zająć dłuższy okres czasu (czasem nawet 48 godzin w najgorszych przypadkach). Jeżeli odrazu nie będziesz mógł się połączyć z serwerem nie panikuj, odczekaj chwile.
{% endhint %}
{% endstep %}
{% endstepper %}
