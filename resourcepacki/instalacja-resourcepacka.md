---
description: >-
  W tej części strony, dowiesz się jak zainstalować na swoim serwerze
  resourcepack.
icon: instalod
---

# Instalacja resourcepacka

***

## Paper (Bez proxy)

{% stepper %}
{% step %}
### Instalacja pluginu forcepack.

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

{% code title="plugins:forcepack/config.yml" fullWidth="false" %}
```yaml
test
```
{% endcode %}
{% endstep %}
{% endstepper %}
