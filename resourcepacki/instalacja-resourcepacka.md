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
### Instalacja pluginu forcepack&#x20;

Pierwszym krokiem będzie pobranie pluginu forcepack, pozwoli on na zarządzanie resourepackiem gdy serwer jest włączony. (Możesz również zainstalować go na serwerze proxy)

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
Server:
  packs:
    all:
      ## Na stronie MCPacksznajdziesz to pod opcja "Download URL:"
      urls: ["https://download.mc-packs.net/pack/abc67aed085220a347e8014d35a142703fed5271.zip"]
      generate-hash: false
      ## Na stronie MCPacks znajdziesz to pod opcja "SHA-1 Hash:"
      hashes: ["abc67aed085220a347e8014d35a142703fed5271"]
  ## Jezeli pozostawisz ta opcje wlaczana, podczas wejscia na serwer z 
  ## uprawnieniami .np operatorem czy * nie zaladujesz resourcepacka.
  ## (domyslnie ustawione jest na true) 
  bypass-permission: false

```
{% endcode %}

* Przeładuj plugin komendą `/forcepack reload` (na proxy to będzie `/vforcepack reload`)

#### Opcjonalne, zalecane opcje do przełączenia

* forcepack, w podstawowej konfiguracji wykonuje mase komend podczas pobierania resourcepacka, oraz jego ładowania, wyłącz je za pomocą opcji wymienionych poniżej.&#x20;

{% code title="plugins:forcepack/config.yml" %}
```yaml
  Actions:
    ##  Opcje: DOWNLOADED, FAILED_RELOAD, DISCARDED dzialaja jedynie dla klientow
    ##  na wersji 1.20.3 +, jezeli chcesz z nich skorzystac zalecam wylaczyc 
    ##  wchodzenie z klienta minecrafta 1.20.2 -, przejdz do konfiguracji viaversion.
    ACCEPTED:
      kick: false
      Commands: []
    DOWNLOADED:
      kick: true
      Commands: []   
    SUCCESSFULLY_LOADED:
      kick: false
      Commands: []
    DECLINED:
      kick: true
      Commands: []
    FAILED_DOWNLOAD:
      kick: true
      Commands: []
    FAILED_RELOAD:
      kick: true
      Commands: []
    DISCARDED:
      kick: true
      Commands: []

```
{% endcode %}
{% endstep %}
{% endstepper %}
