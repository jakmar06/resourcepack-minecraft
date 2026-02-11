---
description: >-
  Poniżej znajdziesz instrukcję, jak skonfigurować domenę poprzez rekord CNAME,
  aby gracze mogli połączy się przez nią do twojego serwera. (poradnik dotyczy
  cloudflare).
---

# Gdy posiadasz serwer zarządzany z dedykowanym ip

{% stepper %}
{% step %}
### STREFA DNS

Przejdź do zakładki **Records** w kategorii **DNS**.

<figure><img src="../../.gitbook/assets/cloudflare-records (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie rekordu

Stwórz nowy rekord typu **CNAME**

<figure><img src="../../.gitbook/assets/cloudflare-create-rekord-cname.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Ustawianie rekordu typu CNAME

Po utworzeniu rekordu typu **CNAME** należy poprawnie skonfigurować jego parametry.\
\
**Name**\
Jako nazwę rekordu zaleca się ustawić znak: `@` Lub wpisać pełną nazwę swojej domeny (np.`hypixel.net`)

{% hint style="info" %}
W moim przypadku name to jest `hypixel.net`
{% endhint %}

**Target**\
W tym polu wpisz **ip** twojego serwera. Ip znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera np. `pl06.icehost.pl`

{% hint style="info" %}
W moim przypadku targetem jest: `pl06.icehost.pl`&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/obraz (5).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Połącz się z twoim serwerem

Jeżeli wykonałeś wszystko poprawnie powinieneś móc połączyć się już z twoim serwerem.

{% hint style="danger" %}
Pamiętaj, że wymagane przy rekordzie typu CNAME jest to, żeby serwer miał domyślnie ustawiony port 25565, w innym wypadku nie uda ci się połączyć z serwerem.\
Przykładami hostingów na których otrzymujesz dedykowany adres ip są: [https://bloom.host/](https://bloom.host/) czy [https://pufferfish.host/](https://pufferfish.host/)
{% endhint %}

{% hint style="warning" %}
Czasami podpięcie domeny może zająć dłuższy okres czasu (czasem nawet 48 godzin w najgorszych przypadkach). Jeżeli odrazu nie będziesz mógł się połączyć z serwerem nie panikuj, odczekaj chwile.
{% endhint %}
{% endstep %}
{% endstepper %}

