# Příkazy

🇬🇧 [English](../en/commands.md) · [← Zpět](README.md)

Prefix je `!`, pokud místnost nenastaví jiný. `<špičaté závorky>` jsou povinné, `[hranaté závorky]` volitelné a `a | b` znamená jednu nebo druhou možnost.

Alias funguje stejně jako název příkazu: `!np` je totéž co `!nowplaying`.

**Kdo** udává nejnižší roli, která příkaz smí použít; viz [Role](roles.md). Příkazy bez role může použít kdokoli.

**Prodleva** se počítá každému zvlášť. Moderátorské příkazy, vlastní odpovědi, nastavení, `!ping` a `!ruleta` čekají mezi použitími 5 sekund, `!clear` 10 sekund a všechny ostatní příkazy 3 sekundy.

**Odpovědi** na příkazy se mažou po minutě; viz [Uklizený chat](features.md#uklizený-chat).

## Info

| Příkaz | Aliasy | Co dělá |
| --- | --- | --- |
| `!help [kategorie\|příkaz]` | `commands` | Samotný vypíše kategorie, které můžeš používat, s počtem příkazů a odkazem na tuto dokumentaci. `!help zábava` vypíše kategorii, `!help np` vysvětlí příkaz. Kategorie fungují i pod anglickými názvy (`!help fun`) |
| `!nowplaying` | `np`, `song` | Název, interpret a zbývající čas, např. `🎵 Blue Veins — Ash Walker · zbývá 2:41` |
| `!time` | `elapsed`, `left` | Kolik ze skladby už uběhlo, jako `1:23 / 4:56` |
| `!score` | `rating` | Podíl woots v procentech, ukazatel a hodnocení |
| `!votes` | `woots` | Počty woot, grab a meh |
| `!dj` | | Kdo právě hraje |
| `!next` | `upnext` | Další tři ve frontě |
| `!djs` | `lineup`, `booth` | Celá fronta popořadě, prvních osm |
| `!queue` | `q`, `wait` | Délka fronty, jestli je zamčená, kdo hraje |
| `!position [uživatel]` | `pos`, `waittime` | Místo ve frontě a odhad čekání; tvoje, pokud nikoho neuvedeš. Jména s mezerou dej do uvozovek: `!position "Slow Poke"` |
| `!users` | `active`, `pop` | Kolik lidí je v místnosti (bez bota) a kdo z nich je AFK |
| `!user <jméno>` | `whois`, `profile` | Profil na Wavez: platformní titul, level, fanoušci, vlajka země |
| `!mods` | `staff` | Štáb, kterého si bot nedávno všiml, podle rolí |
| `!seen <uživatel>` | `lastseen` | Kdy někdo naposledy psal a co naposledy pustil |
| `!history [počet]` | `last`, `recent` | Posledních pár dohraných skladeb, nejnovější první, nejvýš pět |
| `!dupe` | `again`, `heardit` | Jestli aktuální skladba hrála mezi posledními 20 a kdo ji pustil |
| `!top` | `best` | Nejlépe přijatá skladba z posledních 20 (woots minus mehs) |
| `!rules` | `etiquette` | Pravidla místnosti |
| `!theme` | `genre` | Dnešní téma, pokud nějaké je |
| `!afk [důvod]` | `away`, `brb` | Nastaví ti AFK. Viz [AFK](features.md#afk) |
| `!uptime` | | Jak dlouho bot běží |
| `!ping` | `pong` | Ověří, že bot žije |

## Zábava

| Příkaz | Aliasy | Co dělá |
| --- | --- | --- |
| `!8ball <dotaz>` | `eightball` | Zeptej se kouzelné koule |
| `!coin` | `flip`, `coinflip` | Panna nebo orel |
| `!choose a \| b \| c` | `pick`, `either` | Vybere jednu možnost. Odděluj je znakem `\|`, nebo čárkami, když `\|` chybí |
| `!roll [max]` / `!roll [min] [max]` | `dice`, `random` | Náhodné číslo, výchozí rozsah 1–6 |
| `!ruleta` | `raffle`, `wheel`, `spin` | Ruleta. Kolo otevírá **bouncer** příkazem `!ruleta`; viz [Ruleta](features.md#ruleta) |
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
| `!move <uživatel> <pozice> [důvod]` | `mv` | bouncer | Přesune někoho na pozici ve frontě (1 je první) |
| `!lock [důvod]` / `!unlock [důvod]` | | bouncer | Zamkne nebo odemkne frontu |
| `!clear` | | bouncer | Smaže zprávy bota, které jsou ještě v chatu (z posledních 100) |
| `!ban <uživatel> [doba] [důvod]` | | manager | Zabanuje někoho, volitelně na `30m`, `2h` nebo `1d` |
| `!unban <uživatel\|userId> [důvod]` | | manager | Zruší ban |

## Vlastní odpovědi

Manageři můžou bota přímo v chatu naučit krátké textové odpovědi. Ukládají se, takže vydrží restart.

| Příkaz | Aliasy | Kdo | Co dělá |
| --- | --- | --- | --- |
| `!addcmd <spouštěč> <text> [role]` | `addcommand`, `learn` | manager | Přidá nebo přepíše vlastní odpověď |
| `!delcmd <spouštěč>` | `delcommand`, `forget` | manager | Smaže ji |

```
!addcmd discord Přidej se na discord.gg/example
!addcmd porada "Porada v 8" bouncer
```

- V textu se `{name}` nahradí jménem toho, kdo spouštěč napsal, a `{prefix}` prefixem.
- Název role na konci omezí odpověď na tuto roli a vyšší. Bez něj ji může použít kdokoli.
- Uvozovky kolem textu jsou nepovinné a odstraní se. Hodí se, když text sám končí názvem role: `!addcmd shout "the host"` uloží `the host` pro všechny, kdežto `!addcmd bare the host` uloží `the` jen pro hosta.
- Nejvýš 50 odpovědí, každá nejvýš 300 znaků. Odpověď nesmí mít stejný název jako vestavěný příkaz.
- Mají společnou prodlevu 3 sekundy na osobu.
- `!help` je počítá pod **Odpovědi** a `!help odpovědi` je vypíše. Každý vidí jen ty, které smí použít.
- Nepřekládají se: říkají přesně to, co napsal jejich autor.

## Nastavení

| Příkaz | Aliasy | Kdo | Co dělá |
| --- | --- | --- | --- |
| `!cz` | `cs`, `czech`, `cesky` | manager | Přepne bota do češtiny |
| `!en` | `english` | manager | Přepne bota do angličtiny |

Potvrzení přijde už v novém jazyce. Volba se uloží a vydrží restart.
