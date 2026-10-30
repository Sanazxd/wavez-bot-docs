# Seznam změn

🇬🇧 [English](../en/changelog.md) · [← Zpět](README.md)

Tento bot je fork projektu **[fluteds/wavez-bot](https://github.com/fluteds/wavez-bot)** od autora fluteds. Fork vychází z posledního commitu originálu, `f16e723` (26. 9. 2026, verze 1.1.0); vše níže přibylo až potom.

## Porovnání s originálem

| | Originál 1.1.0 | Tento fork 2.0.3 |
| --- | --- | --- |
| Jazyky | jen angličtina | čeština a angličtina, přepínané v chatu příkazy `!cz` / `!en` |
| Příkazy | 40 | 42: přibyly `!ruleta`/`!join`, `!clear`, `!en`, `!cz`; ubyly `!vibe` a `!theme`; `!rules` odkazuje na tuto dokumentaci |
| `!help` | všechny příkazy v jednom výpisu | kategorie s počty; `!help <kategorie>` a `!help <příkaz>`; jen to, co smíš použít; odkaz na tuto dokumentaci |
| Žebříček rolí | `user < resident_dj < bouncer < manager < cohost < host` | přibyla role `vip` mezi `user` a `resident_dj` |
| Platformní tituly | `admin` platí jako manager, `ambassador` jako bouncer | jako manager platí jen `admin`; ambasadoři mají roli, kterou jim dala místnost |
| Uvítání | jeden řádek, nejvýš jednou za 10 minut na osobu | vlastní náhodné řádky pro hosta, štáb, resident DJs a VIP; každý skutečný příchod; rozloučení |
| Přítomnost | věřil každému příchodu a odchodu, který Wavez nahlásil | sleduje, kdo je skutečně v místnosti: opakované příchody, štáb offline, zavřené karty, znovupřipojení, krátké výpadky spojení |
| AFK | příznak zmizel s další zprávou | přivítání po návratu s délkou nepřítomnosti a kdo se ptal; odpovědi na @zmínky; úklid oznámení |
| Automatika v místnosti | žádná | automatické přeskočení, vláček emotů, oslava 10 lidí, ruleta |
| Úklid chatu | žádný | mazání příkazů, mazání odpovědí po minutě a ostatních zpráv bota po hodině, `!clear` |
| Styl odpovědí | prostý text malými písmeny | jednotný styl: emoji na začátku, ` · ` mezi položkami, ukazatele a vlajky |

## 2.0.3 — 30. 10. 2026

### Změněno

- **`!rules` odkazuje na tuto dokumentaci** místo vypisování pravidel z nastavení bota. Napíše, že pravidla a dokumentace jsou na GitHubu, a přidá odkaz.
- **Oznámení o AFK začínají `:brb:`** místo 💤: oznámení o odchodu i odpovědi na @zmínky.
- **Hláška při startu se maže po minutě** místo po hodině.

### Odebráno

- **`!theme`** (`!genre`).
- **`!ruleta leave` a `!ruleta list`**, a s nimi i `!ruleta join`. Do kola se dá vstoupit jen přes `!join` a přihláška platí až do losování.

## 2.0.2 — 28. 10. 2026

### Změněno

- **Ruletu otevírají jen manageři.** Samotné `!ruleta` teď vyžaduje managera, ne bouncera. Přidat se přes `!join`, `!ruleta leave` a `!ruleta list` může dál každý.
- **Oslava plné místnosti nikoho neoznačuje.** Oslava při 10 lidech patří celé místnosti, takže už neoznačí toho, jehož příchod desítku dovršil.

## 2.0.1 — 16. 10. 2026

### Změněno

- **Odpovědi na příkazy** se mažou po minutě místo po hodině, včetně vlastních odpovědí. Oznámení `!afk` dál zůstává až do návratu a uvítání, rozloučení a oznámení rulety dál vydrží hodinu.
- **Ambasadoři už neplatí jako bounceři.** Mají roli, kterou jim dala místnost. `admin` dál platí jako manager.

### Opraveno

- **Krátké výpadky spojení** už nezpůsobí rozloučení a nové uvítání. Rozloučení přijde jen při skutečném odchodu, při odchodu ve vlastním záznamu Wavez, nebo po minutě mimo místnost.
- **Ambasadoři, kteří jsou v místnosti obyčejní uživatelé,** dostávali uvítání pro štáb a mohli používat příkazy managerů, protože je Wavez hlásí jako managery. Bot se teď řídí rolí, kterou přidělila místnost.
- **`!users`** započítával i bota a jako AFK vypisoval i lidi, kteří už odešli. Teď počítá jen lidi v místnosti a vypisuje jen jejich AFK.
- **Odchod z místnosti ukončí AFK**, potichu a bez přivítání po návratu. AFK lidí, kteří odešli, zatímco byl bot offline, se smaže při startu.

## 2.0.0 — 14. 10. 2026

### Přidáno

- **Ruleta.** Bouncer otevře kolo příkazem `!ruleta` a všichni dostanou oznámení přes `@everyone`. Do minuty se dá přidat příkazem `!join`, pak bot vylosuje vítěze a posune ho na #1 ve frontě, a když ve frontě není, nejdřív ho do ní přidá. Oznámení řekne, odkud se vítěz posunul. Padne-li los na právě hrajícího DJe, losuje se znovu.
- **Čeština.** Všechno, co bot říká, existuje česky i anglicky. Manageři přepínají příkazy `!cz` / `!en` a volba se ukládá. České řádky o konkrétní osobě jsou genderově neutrální.
- **Uvítání podle role.** Host, štáb, resident DJs i VIP mají vlastní seznam pozdravů, vybíraný náhodně a nikdy dvakrát po sobě stejně. Zvláštní pozdrav se opakuje až po hodině. Uvítání označuje osobu přes @.
- **Rozloučení.** Bot se rozloučí s každým, kdo odejde, a rozloučení smaže po hodině nebo při návratu. V chatu zůstává jen poslední uvítání či rozloučení pro každého.
- **Sledování přítomnosti.** Bot vítá jen skutečné příchody a pozná i zavřenou kartu nebo výpadek, také mezi dvěma seznamy místnosti. Každých 30 sekund kontroluje, kdo je v místnosti.
- **Přepracované AFK.**
  - Přivítání po návratu řekne, jak dlouhá byla nepřítomnost a kdo se ptal, a po 15 sekundách zmizí.
  - Kdo zmíní osobu s AFK, dostane odpověď s délkou nepřítomnosti a důvodem, nejvýš jednou za 5 minut.
  - Samotné `!afk` AFK ukončí a `!afk <důvod>` změní důvod.
  - Oznámení o AFK i odpovědi na zmínky po návratu zmizí.
- **Automatické přeskočení** skladby, jakmile meh tvoří aspoň polovinu všech hlasů, nikdy ne v prvních 30 sekundách.
- **Vláček emotů.** Pošlou-li 3 lidé do 2 minut `:kong:`, bot se přidá 5–15 kusy.
- **Oslava plné místnosti** při 10 lidech.
- **Úklid chatu.**
  - Zprávy s příkazy se po odpovědi mažou.
  - Zprávy bota se mažou po hodině, odpovědi na `!help` po minutě.
  - `!clear` umožní bouncerovi smazat zprávy bota.
- **Role VIP** na žebříčku, s vlastním uvítáním a bez moderátorských práv.
- **`!help` podle kategorií**, s `!help <kategorie>` (česky i anglicky) a odkazem na tuto dokumentaci.
- **Dvojjazyčná dokumentace** (tyto stránky).

### Změněno

- **Jednotný styl odpovědí** u všech příkazů: emoji na začátku, velké písmeno na začátku věty, ` · ` mezi položkami, `Název — Interpret` u skladeb.
- **`!score`** kreslí ukazatel (`▰▰▰▰▰▰▰▱▱▱ 72%`).
- **`!mods`** řadí štáb podle rolí.
- **`!user`** ukazuje vlajku země.
- **`!nowplaying`** ukazuje zbývající čas jako `2:41`.
- **Dlouhé odpovědi** se dělí mezi položkami místo uprostřed věty a jsou číslované `(1/3)`.

### Odebráno

- **`!vibe`** (`!mood`).
- **Limit uvítání jednou za 10 minut.** Místo něj každé nové uvítání nahradí předchozí, takže znovupřipojení chat nezahltí.

### Opraveno

- **Uvítání** dostanou jen skutečné příchody, ne opakovaná hlášení příchodu nebo štáb offline, a návrat po zavřené kartě se přivítá znovu.
- **Rozloučení** zazní i u odchodu bez řádného odhlášení (zavřená karta, ztracené spojení).
- **Zmínky osob s AFK** se poznávají z textu zprávy a bot v oznámeních o AFK nikdy neoznačí sám sebe.
- **`!join` nejde spamovat** a bez otevřeného kola se ignoruje.
- **Vítěz rulety** se správně posouvá na pozici 1 (pozice ve frontě se číslují od jedničky).
- **Oslava plné místnosti** se spustí přesně při 10 lidech.

## 1.1.0 a starší

Historie před forkem je v [původním repozitáři](https://github.com/fluteds/wavez-bot/commits/main):

- první vydání: bot na chat a moderaci
- `Accept-Language`, aby chyby serveru nechodily portugalsky
- dělení odpovědí přes limit zprávy
- odpovědi se zmínkou (@)
- neznámé role nedostanou žádná práva
