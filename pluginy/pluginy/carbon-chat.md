---
description: W tej sekcji poznasz komendy, permisje i konfiguracje pluginu carbon chat.
cover: ../../.gitbook/assets/carbonchat.png
coverY: 0
---

# Carbon Chat

## Konfiguracja pluginu

x

{% code title="plugins/CarbonChat/config.conf" %}
```yaml
# Pozwala developerowi określić poziom configu, dzięki czemu przy aktualizacji pluginu gdy 
# zostanie dodana nowa funkcja nie będzie to powodować problemów
config-version=1
# The default locale for plugin messages.
default-locale="en_US"
# The default channel that new players will be in when they join.
# If the channel is not found or the player cannot use the channel, they will speak in basic non-channel chat.
default-channel="carbon:global"
# Returns you to the default channel when you use a channel's command while you have that channel active.
return-to-default-channel=false
# The service that will be used to store and load player information.
# One of: JSON, H2, MYSQL, PSQL
# Note: If you choose MYSQL or PSQL make sure you configure the "database-settings" section of this file!
storage-type=JSON
# When "storage-type" is set to MYSQL or PSQL, this section configures the database connection.
# If JSON or H2 storage is used, this section can be ignored.
database-settings {
    # JDBC URL. Suggested defaults for each DB:
    # MySQL: jdbc:mysql://host:3306/DB
    # MariaDB: jdbc:mariadb://host:3306/DB
    # PostgreSQL: jdbc:postgresql://host:5432/database
    url="jdbc:mysql://localhost:3306/carbon"
    # The connection username.
    username=username
    # The connection password.
    password=password
    # Settings for the connection pool. This is an advanced configuration that most users won't need to touch.
    connection-pool {
        maximum-pool-size=8
        minimum-idle=8
        maximum-lifetime=1800000
        keepalive-time=0
        connection-timeout=30000
    }
}
# Settings for cross-server messaging
messaging-settings {
    # Whether cross-server messaging is enabled
    enabled=false
    # One of: RABBITMQ, NATS, REDIS
    broker-type=NONE
    url="127.0.0.1"
    port=5672
    # RabbitMQ VHost
    vhost="/"
    # NATS credentials file
    credentials-file=""
    # RabbitMQ username
    username=username
    # RabbitMQ and Redis password
    password=password
}
nickname-settings {
    # Whether Carbon's nickname management should be used. Disable this if you wish to have another plugin manage nicknames.
    use-carbon-nicknames=true
    # Paper only. Updates the player's display name in the tab list to match their nickname.
    update-tab-list=true
    # Minimum number of characters in nickname (excluding formatting).
    min-length=3
    # Maximum number of characters in nickname (excluding formatting).
    max-length=16
    black-list=[
        notch,
        admin
    ]
    # Regex pattern nicknames must match in order to be applied, can be bypassed with the permission 'carbon.nickname.filter'.
    filter="^[a-zA-Z0-9_]*$"
    # Format used when displaying nicknames.
    format="<hover:show_text:'<gray>@</gray><username>'><gray>~</gray><nickname></hover>"
    # Whether to skip applying 'format' when a nickname matches a players username, only differing in decoration.
    skip-format-when-name-matches=true
}
# Plugin-wide custom placeholders.
# These will be parsed in all messages rendered and sent by Carbon.
# This includes chat, command feedback, and others.
# Make sure to close your tags so they do not bleed into other formats.
# Only a single pass is done so custom placeholders will not work within each other.
custom-placeholders {}
# The suggestions shown when using the TAB key in chat.
custom-chat-suggestions=[]
# The placeholders replaced in chat messages, this WILL work with chat previews.
chat-placeholders {}
# Basic regex based chat filter.
chat-filter {}
# Player toggled chat filter. Useful for more mild profanity.
optional-chat-filter {}
# Various settings related to pinging players in channels.
ping-settings {
    # The color your name will be when another player mentions you.
    highlight-text-color=yellow
    prefix="@"
    play-sound=false
    name="minecraft:block.anvil.use"
    source=master
    volume=1
    pitch=1
}
party-chat {
    # Whether party chat is enabled
    enabled=true
    expire-invites-after-seconds=45
    play-sound=false
    # Sound for receiving a party message
    message-sound {
        name="minecraft:entity.experience_orb.pickup"
        source=master
        volume=1
        pitch=1
    }
}
# Sound for receiving a direct message
message-sound {
    name="minecraft:entity.experience_orb.pickup"
    source=master
    volume=1
    pitch=1
}
# Settings for the clear chat command
clear-chat-settings {
    # The message that will be sent to each player.
    message=""
    # The number of times the message will be sent to each player.
    iterations=50
    # The message to be sent after chat is cleared.
    broadcast="<gold>Chat has been cleared by </gold><green><display_name><green><gold>."
}
# Settings for integrations with other plugins/mods. Settings only apply when the relevant plugin/mod is present.
integrations {
    discordsrv {
        enabled=true
    }
    "essentialsx_discord" {
        enabled=true
    }
    factionsuuid {
        enabled=true
        faction-channel=true
        alliance-channel=true
        truce-channel=true
        faction-mod-channel=false
    }
    mcmmo {
        enabled=true
        # You will likely want to disable Carbon's built-in party system above when using mcMMO party chat.
        party-channel=true
    }
    plotsquared {
        enabled=true
        plot-channel=true
    }
    towny {
        enabled=true
        town-channel=true
        nation-channel=true
        alliance-channel=false
    }
}
# Whether Carbon should check for updates using the GitHub API on startup.
update-checker=true

```
{% endcode %}

## Komendy

<table><thead><tr><th>Komendy</th><th>Alliasy</th><th>Permisje</th><th width="205">Opis</th></tr></thead><tbody><tr><td>/clearchat</td><td><code>/cc</code>,<code>/chatclear</code></td><td>carbon.clearchat.clear</td><td>Czyści chat dla każdego gracza (wyjątkiem są osoby z permisją <code>carbon.chearchat.exempt)</code>.</td></tr><tr><td>/join &#x3C;kanał></td><td><code>Brak</code></td><td>carbon.join</td><td>Dołącza wybranego kanału</td></tr><tr><td>/leave &#x3C;kanał></td><td><code>Brak</code></td><td>carbon.leave</td><td>Wychodzi z obecnego kanału</td></tr><tr><td>/ignore &#x3C;gracz></td><td><code>/block</code></td><td>carbon.ignore</td><td>Ignoruje wiadomości od gracza</td></tr><tr><td>/unignore &#x3C;gracz></td><td><code>/unblock</code></td><td>carbon.ignore.unignore</td><td>Usuwa gracza z listy ignorowanych</td></tr><tr><td>/ignorelist &#x3C;strona></td><td><code>/listignores</code></td><td>carbon.ignore</td><td>Pokazuje liste ignorowanych graczy</td></tr><tr><td>/spy</td><td><code>Brak</code></td><td>carbon.spy</td><td>Pokazuje prywatne wiadomosci graczy</td></tr><tr><td>/mute &#x3C;gracz></td><td><code>Brak</code></td><td>carbon.mute</td><td>Wycisza gracza</td></tr><tr><td>/unmute &#x3C;gracz></td><td><code>Brak</code></td><td>carbon.mute.unmute</td><td>Odcisza gracza</td></tr><tr><td>/muteinfo &#x3C;gracz></td><td><code>/muted</code></td><td>carbon.mute.info</td><td>Pokazuje czy gracz jest wyciszony</td></tr><tr><td>/nickname &#x3C;gracz></td><td><code>/nick</code></td><td>carbon.nickname</td><td>Pozwala graczowi wyświetlić nick gracza</td></tr><tr><td>/nickname --player</td><td><code>/nick</code></td><td>carbon.nickname.others</td><td>Pozwala graczowi sprawdzać oraz ustawiać nick innych graczy</td></tr><tr><td>/nickname --nickname</td><td><code>/nick</code></td><td>carbon.nickname.set</td><td>Pozwala graczowi ustawiać nick swój lub innego gracza</td></tr><tr><td>/nickname --reset</td><td><code>/nick</code></td><td>carbon.nickname.set</td><td>Pozwala graczowi zresetować nick swój lub innego gracza</td></tr><tr><td>/updateusername</td><td><code>/updatename</code></td><td>carbon.updateusername</td><td>Pozwala graczowi zaktualizować nazwę użytkownika swoją lub innego gracza</td></tr><tr><td>/filter</td><td><code>Brak</code></td><td>carbon.filter</td><td>Przełacza definicje filtru chatu.</td></tr><tr><td>/reply</td><td><code>/r</code></td><td>carbon.whisper.reply</td><td>Wysyła wiadomość do ostatniego gracza z ktorym miałeś interakcje</td></tr><tr><td>/continue</td><td>/c</td><td>carbon.whisper.continue</td><td>Wysyła wiadomosc do ostatniego gracza do którego wysłałes wiadomosc</td></tr><tr><td>/whisper</td><td><code>/w</code>,<code>/message</code>,<code>/msg</code>,<br><code>/m</code>,<code>/tell</code></td><td>carbon.whisper</td><td>Wysyła wiadomosc prywatną do gracza</td></tr><tr><td>/togglemsg</td><td><code>/togglepm</code></td><td>carbon.togglemsg</td><td>Przełącza pokazywanie wiadomości prywatnych </td></tr><tr><td>/carbon reload</td><td><code>Brak</code></td><td>carbon.reload</td><td>Przeładowuje plugin</td></tr><tr><td>/carbondebug</td><td><code>/cdebug</code></td><td>carbon.debug</td><td>Umożliwia szybkie sprawdzenie głównych i pobocznych grup gracza</td></tr><tr><td>/carbon help</td><td><code>Brak</code></td><td>carbon.help</td><td>Pokazuje komendy pluginu</td></tr></tbody></table>

## Permisje

### Ogólne

<table><thead><tr><th>Permisja</th><th width="364">Opis</th></tr></thead><tbody><tr><td>carbon.channel</td><td>Pozwala na użycie komend <code>/channel</code>.</td></tr><tr><td>carbon.channel.<code>nazwa kanału</code></td><td>Pozwala na przełączenie kanału chatu komendą <code>/channelname</code>.</td></tr><tr><td>carbon.channel.<code>nazwa kanału</code>.see</td><td>Pozwala na wyświetlanie wiadomości z określonego kanału.</td></tr><tr><td>carbon.channel.<code>nazwa kanału</code>.speak</td><td>Pozwala na wysyłanie wiadomości na określonym kanale.</td></tr><tr><td>carbon.join</td><td>Pozwala graczowi dołączyć do kanału.</td></tr><tr><td>carbon.leave</td><td>Pozwala graczowi opuścić kanał.</td></tr><tr><td>carbon.clearchat.clear</td><td>Pozwala graczowi wyczyścić chat dla każdego gracza (wyjątkiem są osoby z permisją <code>carbon.chearchat.exempt)</code>.</td></tr><tr><td>carbon.clearchat.exempt</td><td>Bypass dla komendy <code>/clear</code>. Gdy moderator użyje tej komendy chat dla gracza z tą permisją nie zostanie wyczyszczony.</td></tr><tr><td>carbon.debug</td><td>Sprawdza grupy gracza.</td></tr><tr><td>carbon.help</td><td>Sprawdza komendy pluginu.</td></tr><tr><td>carbon.ignore</td><td>Pozwala graczowi ukryć prywatne wiadomości od innych graczy.</td></tr><tr><td>carbon.ignore.exempt</td><td>Pozwala ominąć ignorowanie prywatnych wiadomości.</td></tr><tr><td>carbon.ignore.unignore</td><td>Pozwala usunąć ignorowanie prywatnych wiadomości od innych graczy.</td></tr><tr><td>carbon.crossserver</td><td>Pozwala na odbieranie wiadomości z innych serwerów.</td></tr><tr><td>carbon.parties</td><td>Pozwala na korzystanie i tworzenie chatów grupowych.</td></tr><tr><td>carbon.mute</td><td>Pozwala na wyciszanie graczy.</td></tr><tr><td>carbon.mute.exempt</td><td>Pozwala ominąć wyciszenie.</td></tr><tr><td>carbon.mute.info</td><td>Informacje o wyciszeniu.</td></tr><tr><td>carbon.mute.notify</td><td>Powiadomienie o wyciszeniu gracza</td></tr><tr><td>carbon.mute.unmute</td><td>Pozwala odciszyć gracza.</td></tr><tr><td>carbon.nickname</td><td>Pozwala graczowi sprawdzić swój wyświetlany nick.</td></tr><tr><td>carbon.nickname.others</td><td>Pozwala graczowi sprawdzić oraz ustawiać wyświetlany nick innych graczy.</td></tr><tr><td>carbon.nickname.see</td><td>Pozwala graczowi sprawdzić wyświetlany nick swój oraz innych graczy.</td></tr><tr><td>carbon.nickname.self</td><td>Pozwala graczowi sprawdzić oraz ustawiać swój wyświetlany nick.</td></tr><tr><td>carbon.nickname.set</td><td>Pozwala graczowi ustawiać swój wyświetlany nick oraz innych graczy.</td></tr><tr><td>carbon.reload</td><td>Pozwala przeładować konfigurację, oraz tłumaczenie pluginu.</td></tr><tr><td>carbon.spy</td><td>Pozwala graczowi używać komendy <code>/spy</code> oraz wyświetlać prywatne wiadomości graczy, oraz wiadomości z innych kanałow.</td></tr><tr><td>carbon.updateusername</td><td>Pozwala graczowi używać komendy <code>/updateusername</code>.</td></tr><tr><td>carbon.whisper.message</td><td>Pozwala graczowi używać komendy <code>/msg</code></td></tr><tr><td>carbon.whisper.send</td><td>Pozwala graczowi wysyłać prywatne wiadomości.</td></tr><tr><td>carbon.whisper.receive</td><td>Pozwala graczowi otrzymywać prywatne wiadomości</td></tr><tr><td>carbon.whisper.continue</td><td>Pozwala graczowi wysłać wiadomość poprzez komende <code>/continue</code> do ostatniego gracza z którym pisał.</td></tr><tr><td>carbon.whisper.reply</td><td>Pozwala odpowiedzieć graczowi który ostatni do niego napisał przez komende <code>/r</code> </td></tr><tr><td>carbon.whisper.vanished</td><td>Pozwala pisać do graczy na vanishu</td></tr><tr><td>carbon.chatlinks</td><td>Pozwala graczowi na chacie wysyłać linki.</td></tr><tr><td>carbon.togglemsg</td><td>Pozwala graczowi włączać i wyłaczac prywatne wiadomosci pod komendą <code>/togglemsg</code></td></tr><tr><td>carbon.togglemsg.exempt</td><td>Wyłącza możliwość ukrywania wiadomosci danego gracza</td></tr><tr><td>carbon.filter</td><td>Pozwala wyłaczać i włączać filrty chatu ustawione w <code>config.conf</code>.</td></tr><tr><td>carbon.itemlink</td><td>Pozwala graczowi wysłać na chat informacje o swoim przedmiocie. Informacje: <a href="carbon-chat.md#itemlinks">[kliknij]</a></td></tr><tr><td>carbon.nickname.tags.<code>&#x3C;format></code></td><td>Pozwala graczowi ustawić formatowany nick. Permisja <code>carbon.messagetags.*</code> pozwala na używanie wszystkich formatów. Wiki dla formatu minimessage: <a href="https://docs.papermc.io/adventure/minimessage/format/">[kliknij]</a></td></tr><tr><td>carbon.parties.name.tags.<code>&#x3C;format></code></td><td>Pozwala graczowi ustawić formatowaną nazwę party. Permisja <code>carbon.messagetags.*</code> pozwala na używanie wszystkich formatów. <br>Wiki dla formatu minimessage: <a href="https://docs.papermc.io/adventure/minimessage/format/">[kliknij]</a></td></tr><tr><td>carbon.messagetags.<code>&#x3C;format></code></td><td>Pozwala graczowi wysyłać formatowane wiadomości w danym typie. Permisja <code>carbon.messagetags.*</code> pozwala na używanie wszystkich formatów. <br>Wiki dla formatu minimessage: <a href="https://docs.papermc.io/adventure/minimessage/format/">[kliknij]</a></td></tr><tr><td>carbon.chatplaceholders</td><td>Pozwala graczowi używać placeholderów na chacie.</td></tr></tbody></table>

### Formatowane wiadomości

| Permisja                         | Opis                                                                                                                                                                                                            |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| carbon.messagetags.color         | Pozwala graczowi wysyłać wiadomości w [vanilla kolorze](https://docs.papermc.io/adventure/minimessage/format/#color) lub [wybranym hexie.](https://docs.papermc.io/adventure/minimessage/format/#color-verbose) |
| carbon.messagetags.gradient      | Pozwala graczowi wysyłać wiadomości w [gradiencie](https://docs.papermc.io/adventure/minimessage/format/#gradient).                                                                                             |
| carbon.messagetags.rainbow       | Pozwala graczowi wysyłać wiadomości w [kolorze tęczy.](https://docs.papermc.io/adventure/minimessage/format/#rainbow)                                                                                           |
| carbon.messagetags.decorations   | Pozwala graczowi [pogrubiać, podkreślać, przekreślać, przechylać, oraz szyfrować wiadomości](https://docs.papermc.io/adventure/minimessage/format/#decoration).                                                 |
| carbon.messagetags.bold          | Pozwala graczowi wysyłać [pogrubione ](https://docs.papermc.io/adventure/minimessage/format/#decoration)wiadomości.                                                                                             |
| carbon.messagetags.italic        | Pozwala graczowi wysyłać [pochylone ](https://docs.papermc.io/adventure/minimessage/format/#decoration)wiadomości.                                                                                              |
| carbon.messagetags.underlined    | Pozwala graczowi wysyłać [podkreśline ](https://docs.papermc.io/adventure/minimessage/format/#decoration)wiadomości                                                                                             |
| carbon.messagetags.strikethrough | Pozwala graczowi wysyłać [przekreślone ](https://docs.papermc.io/adventure/minimessage/format/#decoration)wiadomości.                                                                                           |
| carbon.messagetags.obfuscated    | Pozwala graczowi wysyłać [zaszyfrowane ](https://docs.papermc.io/adventure/minimessage/format/#decoration)wiadomości.                                                                                           |
| carbon.messagetags.hover         | Pozwala graczowi wysyłać wiadomości w [hoverze](https://docs.papermc.io/adventure/minimessage/format/#hover). (Gdy się najedzie na wiadomość pojawi się tekst)                                                  |
| carbon.messagetags.click         | Pozwala graczowi wysyłać [klikalne](https://docs.papermc.io/adventure/minimessage/format/#click) wiadomości.                                                                                                    |
| carbon.messagetags.translatable  | Pozwala graczowi wysyłać wiadomości w [danym języku](https://docs.papermc.io/adventure/minimessage/format/#translatable). (tylko wiadomości z minecrafta)                                                       |
| carbon.messagetags.keybind       | Pokazuje graczowi wysyłać wiadomość z  [jego bindem do danej aktywności](https://docs.papermc.io/adventure/minimessage/format/#keybind).                                                                        |
| carbon.messagetags.insertion     | Pozwala graczowi na [podpowiedzenie tekstu po kliknięciu w niego z shiftem](https://docs.papermc.io/adventure/minimessage/format/#insertion).                                                                   |
| carbon.messagetags.font          | Pozwala na wysyłanie wiadomości w [danym foncie](https://docs.papermc.io/adventure/minimessage/format/#font).                                                                                                   |
| carbon.messagetags.reset         | Pozwala graczowi na [reset całego formatu](https://docs.papermc.io/adventure/minimessage/format/#reset).                                                                                                        |
| carbon.messagetags.newline       | Pozwala graczowi na wysyłanie wiadomości w [nowej lini.](https://docs.papermc.io/adventure/minimessage/format/#newline)                                                                                         |
| carbon.messagetags.pride         | Pozwala graczowi wysyłać wiadomości w kolorach [flag pride](https://docs.papermc.io/adventure/minimessage/format/#pride).                                                                                       |
| carbon.messagetags.shadow\_color | Pozwala graczowi zmieniać [kolor cieni ](https://docs.papermc.io/adventure/minimessage/format/#shadow-color)w wiadomości.                                                                                       |
| carbon.messagetags.transition    | Pozwala graczowi wysyłać wiadomości z tekst[ przejściem kolorów](https://docs.papermc.io/adventure/minimessage/format/#transition).                                                                             |

## ItemLinks

<table><thead><tr><th width="133">Slot</th><th width="188">Alliasy</th><th width="261">Opis</th></tr></thead><tbody><tr><td>Hełm</td><td><code>&#x3C;helm></code>, <code>&#x3C;helmet></code>, <code>&#x3C;hat></code>, <code>&#x3C;head></code></td><td>Pozwala graczowi wysłać na chat informacje o przedmiocie z swojego slotu na głowie.</td></tr><tr><td>Napierśnik</td><td><code>&#x3C;chest></code>, <code>&#x3C;chestplate></code></td><td>Pozwala graczowi wysłać na chat informacje o przedmiocie z swojego slotu na napierśnik.</td></tr><tr><td>Nogawice</td><td><code>&#x3C;legs></code>, <code>&#x3C;leggings></code></td><td>Pozwala graczowi wysłać na chat informacje o przedmiocie z swojego slotu na nogawice.</td></tr><tr><td>Buty</td><td><code>&#x3C;boots></code>, <code>&#x3C;feet></code></td><td>Pozwala graczowi wysłać na chat informacje i przedmiocie z z swojego slotu na buty.</td></tr><tr><td>Główna ręka</td><td><code>&#x3C;main_hand></code>, <code>&#x3C;hand></code>, <code>&#x3C;item></code></td><td>Pozwala graczowi wysłać na chat informacje o przedmiocie z swojej drugiej głównej ręki</td></tr><tr><td>Druga ręka</td><td><code>&#x3C;off_hand</code></td><td>Pozwala graczowi wysłać na chat informacje z swojej drugiej ręki</td></tr></tbody></table>

{% hint style="danger" %}
Gdy plugin jest pobrany na proxy wysyłanie informacji o przedmiotach jest niedostepne.
{% endhint %}

## Placeholdery ([PlaceholderAPI](https://modrinth.com/plugin/placeholderapi/versions))

|         Placeholder        |                           Opis                           |
| :------------------------: | :------------------------------------------------------: |
|     %carbonchat\_party%    |               Zwraca czy gracz jest w party              |
|   %carbonchat\_nickname%   |                    Zwraca nick gracza                    |
|  %carbonchat\_displayname% | [Zwraca wyświetalny nick gracza](#user-content-fn-1)[^1] |
| %carbonchat\_channel\_key% |            Zwraca aktualny kanał chatu gracza            |

## Placeholdery ([miniplaceholders](https://modrinth.com/plugin/miniplaceholders))

|         Placeholder         |                Opis                |
| :-------------------------: | :--------------------------------: |
|     \<carbonchat\_party>    |    Zwraca czy gracz jest w party   |
|   \<carbonchat\_nickname>   |         Zwraca nick gracza         |
|  \<carbonchat\_displayname> |   Zwraca wyświetalny nick gracza   |
| \<carbonchat\_channel\_key> | Zwraca aktualny kanał chatu gracza |

## Placeholdery referencyjne

|   Placeholder  |                      Opis                      |
| :------------: | :--------------------------------------------: |
|   \<username>  |               Zwraca nick gracza               |
| \<displayname> |         Zwraca wyświetalny nick gracza         |
|   \<channel>   | Zwraca z jakiego kanału gracz wysłał wiadomość |
|   \<message>   |           Zwraca zawartość wiadomości          |

## Porównanie funkcji

<table><thead><tr><th>Funkcje</th><th align="center">CarbonChat</th><th align="center">Essentials Chat</th><th align="center" valign="middle">LPC</th></tr></thead><tbody><tr><td>Wspierane platformy</td><td align="center">paper, folia, fabric, velocity</td><td align="center">spigot, paper</td><td align="center" valign="middle">spigot, paper</td></tr><tr><td>Wspierane wersje</td><td align="center">1.21.4+</td><td align="center">1.8.9+</td><td align="center" valign="middle">1.7.10+</td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">Cross Server </a></td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">💰</td></tr><tr><td>Kanały Chatu</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">💰</td></tr><tr><td><a data-footnote-ref href="#user-content-fn-3">Multi-language</a></td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td><a data-footnote-ref href="#user-content-fn-4">Chat Radius</a></td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td>Party chat</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td>Custom Kanały</td><td align="center">Towny,FactionsUUID, mcMMO</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td>QuickPrefix</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">💰</td></tr><tr><td>ItemLinking</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td>Group Format</td><td align="center">✅</td><td align="center">✅</td><td align="center" valign="middle">✅</td></tr><tr><td>Placeholderapi support</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">✅</td></tr><tr><td>Miniplaceholders support</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">❌</td></tr><tr><td>Placeholdery</td><td align="center"><a href="carbon-chat.md#placeholdery-placeholderapi">zobacz liste</a></td><td align="center"><a href="https://essentialsx.net/wiki/keywords">zobacz liste</a></td><td align="center" valign="middle">✅</td></tr><tr><td><a data-footnote-ref href="#user-content-fn-5">Placeholdery referecyjne</a></td><td align="center"><a href="carbon-chat.md#placeholdery-referencyjne">zobacz liste</a></td><td align="center"><a href="https://essentialsx.net/wiki/keywords">zobacz liste</a></td><td align="center" valign="middle">✅</td></tr><tr><td>DiscordSRV support</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">💰</td></tr><tr><td>EssentialsXDiscord</td><td align="center">✅</td><td align="center">✅</td><td align="center" valign="middle">❌</td></tr><tr><td>Wspierane formaty</td><td align="center"><a href="https://docs.papermc.io/adventure/minimessage/format/">minimessage</a></td><td align="center">hex colors, legacy</td><td align="center" valign="middle">hex colors, legacy, <a href="https://docs.papermc.io/adventure/minimessage/format/"><mark style="color:$warning;">minimessage</mark></a></td></tr><tr><td>Pingi @gracz</td><td align="center">✅</td><td align="center">❌</td><td align="center" valign="middle">💰</td></tr><tr><td>Format za permisją</td><td align="center">✅</td><td align="center">🟧</td><td align="center" valign="middle">💰</td></tr></tbody></table>

***

{% embed url="https://github.com/Hexaoxide/Carbon/wiki" %}
Oficjalna Dokumentacja pluginu (Po angielsku, bardziej szczegółowa)
{% endembed %}

[^1]: 

[^2]: Synchronizacja między paroma serwerami

[^3]: Możliwość ustawienia danego formatu dla danego języka, np. dla osób z językiem polskim ranga własciciel będzie czerwona, a dla osób z językiem angielskim niebieska.

[^4]: Możliwość ustawienia w jakim odstępne mają być widoczne wiadomości, np gracz 5 kratek od ciebie widzi twoje wiadomości, a gracz 10 kratek od ciebie ich nie widzi.

[^5]: Wbudowane w plugin, które można użyć tylko na chacie.
