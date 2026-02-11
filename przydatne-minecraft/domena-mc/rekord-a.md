---
description: >-
  Poniżej znajdziesz instrukcję, jak skonfigurować domenę poprzez rekord A, aby
  gracze mogli połączy się przez nią do twojego serwera. (poradnik dotyczy
  cloudflare)
---

# Gdy posiadasz VPS/DEDYKA

{% stepper %}
{% step %}
### Strefa DNS

Przejdź do zakładki **Records** w kategorii **DNS**.

<figure><img src="../../.gitbook/assets/cloudflare-records.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie rekordu

Stwórz nowy rekord typu A

<figure><img src="../../.gitbook/assets/obraz (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Ustawianie rekordu typu A

Po utworzeniu rekordu typu **A** należy poprawnie skonfigurować jego parametry.\
\
**Name**\
Jako nazwę rekordu zaleca się ustawić znak: `@` Lub wpisać pełną nazwę swojej domeny (np.`hypixel.net`)\
**IPv4 Address**\
W tym polu wpisz **ip numeryczne** twojego serwera. Ip znajdziesz w panelu hostingu, zazwyczaj w zakładce z konsolą serwera np. `2137.420.69.67`

<figure><img src="../../.gitbook/assets/obraz.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Połącz się z twoim serwerem

Jeżeli wykonałeś wszystko poprawnie powinieneś móc połączyć się już z twoim serwerem.

{% hint style="danger" %}
Pamiętaj, że wymagane przy rekordzie typu A jest to, żeby serwer miał domyślnie ustawiony port 25565, w innym wypadku nie uda ci się połączyć z serwerem.
{% endhint %}

{% hint style="warning" %}
Czasami podpięcie domeny może zająć dłuższy okres czasu (czasem nawet 48 godzin w najgorszych przypadkach). Jeżeli odrazu nie będziesz mógł się połączyć z serwerem nie panikuj, odczekaj chwile.
{% endhint %}
{% endstep %}
{% endstepper %}
