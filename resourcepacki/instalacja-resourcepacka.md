---
description: >-
  W tej części strony, dowiesz się jak zainstalować na swoim serwerze
  resourcepack.
icon: instalod
---

# Instalacja resourcepacka

***

{% stepper %}
{% step %}
### Instalacja pluginu forcepack

Pierwszym krokiem będzie pbranie pluginu forcepack, pozwoli on na zarządzanie resourepackiem gdy serwer jest włączony. (Możesz również zainstalować go na serwerze proxy)

{% embed url="https://modrinth.com/plugin/forcepack" fullWidth="false" %}
{% endstep %}

{% step %}
### Wgranie resourcepacka na hosting

Drugim krokiem będzie wgranie twojego resourcepacka na hosting, w tym celu zalecam skorzystanie ze strony MCPacks, została ona stworzona specjalnie pod hosting resourcepacków dla serwerów Minecraft.

{% embed url="https://mc-packs.net/" %}

{% hint style="danger" %}
Pamiętaj, by twój resourcepack znajdował się w pliku `.zip`, oraz żeby zawierał w głównym katalogu poprawnie sfortmatowany plik `pack.mcmeta`.
{% endhint %}
{% endstep %}

{% step %}
### Instalacja resourcepacka na serwerze

* Umieść plugin `forcepack` w folderze `plugins`&#x20;
* Zrestartuj serwer
* Gdy plugin zainstaluje się na serwerze przejdź do jego konfiguacji i zmień niżej wymienione opcje.
* Przeładuj plugin komendą `/forcepack reload` (na proxy to będzie `/vforcepack reload`)

{% code title="plugins:forcepack/config.yml" fullWidth="false" %}
```yaml
Server:
  packs:
    all:
      ## Na stronie forcepack znajdziesz to pod opcja "Download URL:"
      urls: ["https://download.mc-packs.net/pack/abc67aed085220a347e8014d35a142703fed5271.zip"]
      generate-hash: false
      ## Na stronie forcepack znajdziesz to pod opcja "SHA-1 Hash:"
      hashes: ["abc67aed085220a347e8014d35a142703fed5271"]
```
{% endcode %}
{% endstep %}
{% endstepper %}
