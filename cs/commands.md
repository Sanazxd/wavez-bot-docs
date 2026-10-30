# Příkazy

🇬🇧 [English](../en/commands.md) · [← Zpět](README.md)

Prefix je `!`, pokud místnost nenastaví jiný. `<špičaté závorky>` jsou povinné, `[hranaté závorky]` volitelné a `a | b` znamená jednu nebo druhou možnost.

Alias funguje stejně jako název příkazu: `!whois` je totéž co `!user`.

**Kdo** udává nejnižší roli, která příkaz smí použít; viz [Role](roles.md). Příkazy bez role může použít kdokoli.

**Prodleva** se počítá každému zvlášť: každý příkaz čeká mezi použitími 3 sekundy. Stejný příkaz od stejné osoby dřív bot bez odpovědi ignoruje.

**Odpovědi** na příkazy se mažou po minutě; viz [Uklizený chat](features.md#uklizený-chat).

## Info

| Příkaz | Aliasy | Co dělá |
| --- | --- | --- |
| `!help [kategorie\|příkaz]` | `commands` | Samotný vypíše kategorie, které můžeš používat, s počtem příkazů a odkazem na tuto dokumentaci. `!help zábava` vypíše kategorii, `!help seen` vysvětlí příkaz. Kategorie fungují i pod anglickými názvy (`!help fun`) |
| `!users` | `active`, `pop` | Kolik lidí je v místnosti (bez bota) a kdo z nich je AFK |
| `!user <jméno>` | `whois`, `profile` | Profil na Wavez: platformní titul, level, fanoušci, vlajka země |
| `!seen <uživatel>` | `lastseen` | Kdy někdo naposledy psal a co naposledy pustil |
| `!afk [důvod]` | `away`, `brb` | Nastaví ti AFK. Viz [AFK](features.md#afk) |
| `!uptime` | | Jak dlouho bot běží |
| `!ping` | `pong` | Ověří, že bot žije, a ukáže odezvu serveru v ms |

## Zábava

| Příkaz | Aliasy | Co dělá |
| --- | --- | --- |
| `!8ball <dotaz>` | `eightball` | Zeptej se kouzelné koule |
| `!coin` | `flip`, `coinflip` | Panna nebo orel |
| `!choose a \| b \| c` | `pick`, `either` | Vybere jednu možnost. Odděluj je znakem `\|`, nebo čárkami, když `\|` chybí |
| `!roll [max]` / `!roll [min] [max]` | `dice`, `random` | Náhodné číslo, výchozí rozsah 1–6 |
| `!ruleta` | `raffle`, `wheel`, `spin` | Ruleta. Kolo otevírá **manager** příkazem `!ruleta`; viz [Ruleta](features.md#ruleta) |
| `!join` | | Vstup do otevřeného kola rulety |

## Fronta

| Příkaz | Aliasy | Co dělá |
| --- | --- | --- |
| `!escort [počet]` | `afterdj`, `escortme` | Odchod z fronty po další skladbě. `!escort 3` až po třech dalších (1–20), `!escort off` to zruší |
| `!bail` | `hop`, `leavequeue` | Okamžitý odchod z fronty; zruší i nastavený `!escort` |

## Moderace

Každý moderátorský příkaz bere na konci volitelný důvod. Odpověď ho zobrazí (`👢 Vyhazuji Bob · spam`) a pošle se i na Wavez, pokud ho server přijímá.

Zobrazovaná jména s mezerou dej do uvozovek: `!kick "Slow Poke" moc pomalé`.

Nikdo nemůže zasahovat proti botovi, proti někomu se stejnou rolí ani proti nikomu nad sebou.

| Příkaz | Aliasy | Kdo | Co dělá |
| --- | --- | --- | --- |
| `!skip [důvod]` | | bouncer | Přeskočí aktuální skladbu |
| `!kick <uživatel> [důvod]` | | bouncer | Vyhodí někoho z místnosti |
| `!mute <uživatel> [doba] [důvod]` | | bouncer | Ztlumí někoho, volitelně na `30m`, `2h` nebo `1d` |
| `!unmute <uživatel> [důvod]` | | bouncer | Zruší ztlumení |
| `!remove <uživatel> [důvod]` | `rm` | bouncer | Odebere někoho z fronty |
| `!move <uživatel> <pozice> [důvod]` | `mv` | bouncer | Přesune někoho ve frontě na pozici (1 je první; pozice za koncem znamená poslední místo). Ohlásí to, až to server provede |
| `!lock [důvod]` / `!unlock [důvod]` | | bouncer | Zamkne nebo odemkne frontu |
| `!clear` | | bouncer | Smaže zprávy bota, které jsou ještě v chatu (z posledních 100) |
| `!ban <uživatel> [doba] [důvod]` | | manager | Zabanuje někoho, volitelně na `30m`, `2h` nebo `1d` |
| `!unban <uživatel\|userId> [důvod]` | | manager | Zruší ban |

## Nastavení

| Příkaz | Aliasy | Kdo | Co dělá |
| --- | --- | --- | --- |
| `!cz` | `cs`, `czech`, `cesky` | manager | Přepne bota do češtiny |
| `!en` | `english` | manager | Přepne bota do angličtiny |

Potvrzení přijde už v novém jazyce. Volba se uloží a vydrží restart.
