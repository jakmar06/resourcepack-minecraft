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

Po stworzeniu rekordu typu A, musisz ustawić jego nazwę, zalecane jest ustawienie znaku "@ lub twojej domeny". Po ustawieniu jego nazwy musisz podać ip numeryczne twojego serwera. Korzystając z panelu hostingu zazwyczaj będzie one podane w zakładce z konsolą serwera.

<figure><img src="../.gitbook/assets/obraz (2).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Tworzenie i ustawienie rekordu SRV

Kolejnym krokiem będzie stworzenie nowego rekordu, tym razem to będzie rekord SRV.\
\
1\. W polu name ustawiamy wartość "\_minecraft.\_tcp." \
2\. W polu Priority ustawiamy wartość "1"\
3\. W polu Weight ustawiamy wartość  "1"\
4\. W polu port ustawiamy swój port serwera. Korzystając z panelu hostingu zazwyczaj będzie one podane w zakładce z konsolą serwera po ip twojego serwera m\[. 2137.420.69.67:25565 (twojeip:twojport).\
5\. W polu target ustawiamy nazwę rekordu a którą podaliśmy wcześniej, w moim przypadku jest to hypixel.net

<figure><img src="../.gitbook/assets/obraz (4).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Połącz się z twoim serwerem

Jeżeli wykonałeś wszystko poprawnie powinieneś móc połączyć się już z twoim serwerem.
{% endstep %}
{% endstepper %}

