---
description: >-
  W tej sekcji, dowiesz się jak skonfigurować poprawnie LibreLoginProd na twoim
  serwerze proxy.
---

# LibreLoginProd (proxy)



{% stepper %}
{% step %}
### Pobranie pluginu LibreLoginProd

Pierwszym krokiem będzie pobranie pluginu LibreLoginProd.

{% embed url="https://modrinth.com/plugin/libreloginprod" %}

{% embed url="https://github.com/Navio1430/LibreLoginProd/releases" %}

{% hint style="info" %}
Powyżej podałem 2 linki, ponieważ plugin często na githubie ma jedną, czy kilka nowszych wersji niż na modrinthie.
{% endhint %}
{% endstep %}

{% step %}
### Instalacja, oraz konfiguracja LibreLoginProd

* Umieść plugin `LibreLoginProd` w folderze `plugins`&#x20;
* Zrestartuj serwer
* Gdy plugin zainstaluje się na serwerze przejdź do konfguracji velocity, oraz konfiguracji pluginu i zmień poniżej wymienione opcje.

{% tabs %}
{% tab title="plugins:librelogin/config.conf" %}
{% code title="plugins:forcepack/config.yml" fullWidth="false" %}
```yaml
Server:
  packs:
    all:
      ## Na stronie MCPacks znajdziesz to pod opcja "Download URL:" 
      urls: ["https://download.mc-packs.net/pack/abc67aed085220a347e8014d35a142703fed5271.zip"] 
      # Zalecane ustawienie na true, gdy masz ta opcje wlaczona, nie musisz recznie podawac hashu
      generate-hash: true 
      ## Na stronie MCPacks znajdziesz to pod opcja "SHA-1 Hash:"
      hashes: ["abc67aed085220a347e8014d35a142703fed5271"]
  ## Jezeli pozostawisz ta opcje wlaczana, podczas wejscia na serwer z 
  ## uprawnieniami .np operatorem czy * nie zaladujesz resourcepacka.
  ## (domyslnie ustawione jest na true) 
  bypass-permission: false

```
{% endcode %}
{% endtab %}

{% tab title="velocity.toml" %}
{% code title="plugins:forcepack/config.yml" fullWidth="false" %}
```yaml
Server:
  packs:
    all:
      ## Na stronie MCPacks znajdziesz to pod opcja "Download URL:" 
      urls: ["https://download.mc-packs.net/pack/abc67aed085220a347e8014d35a142703fed5271.zip"] 
      # Zalecane ustawienie na true, gdy masz ta opcje wlaczona, nie musisz recznie podawac hashu
      generate-hash: true 
      ## Na stronie MCPacks znajdziesz to pod opcja "SHA-1 Hash:"
      hashes: ["abc67aed085220a347e8014d35a142703fed5271"]
  ## Jezeli pozostawisz ta opcje wlaczana, podczas wejscia na serwer z 
  ## uprawnieniami .np operatorem czy * nie zaladujesz resourcepacka.
  ## (domyslnie ustawione jest na true) 
  bypass-permission: false

```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}
