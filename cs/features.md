# Funkce

🇬🇧 [English](../en/features.md) · [← Zpět](README.md)

Co bot dělá sám od sebe, aniž by někdo psal příkaz.

## Uvítání

Když někdo přijde, bot příchozí osobu pozdraví se zmínkou (@). Vlastní, větší pozdrav mají:

- host místnosti
- štáb: bounceři, manageři a co-hosti
- resident DJs
- VIP

Všichni ostatní dostanou obyčejný pozdrav.

- Každý zvláštní pozdrav má několik řádků. Bot vybere jeden náhodně a nikdy nezopakuje ten, který použil naposledy.
- Zvláštní pozdrav se opakuje až po hodině. Návrat do hodiny dostane obyčejný pozdrav.
- Počítá se jen role v místnosti. Platformní admini a ambasadoři dostanou obyčejný pozdrav.
- Boty bot nevítá nikdy.
- Pozdrav dostane každý skutečný příchod, i návrat po zavření karty nebo výpadku spojení.
- Lidi, kteří v místnosti už jsou, bot nevítá. Wavez jim někdy pošle příchod znovu nebo vypíše štáb, který je offline.

## Rozloučení

Když někdo z místnosti odejde, i kvůli kicku nebo banu, bot se rozloučí.

- Rozloučení zmizí po hodině, nebo hned, jakmile se dotyčná osoba vrátí.
- V chatu zůstává jen poslední uvítání nebo rozloučení pro každého. Nové o někom smaže to předchozí, takže nestabilní připojení chat nezahltí.
- Zavření karty žádný signál o odchodu nepošle. Bot si všimne chybějícího jména v seznamu místnosti a rozloučí se až tehdy. Kdo je v místnosti, kontroluje každých 30 sekund.

## AFK

`!afk` ti nastaví stav AFK a `!afk <důvod>` přidá důvod (nejvýš 80 znaků).

- **Zmínky během AFK:** kdo tě zmíní přes @, dozví se, jak dlouho jsi pryč a proč. Každý tuhle odpověď dostane nejvýš jednou za 5 minut.
- **Návrat:** jakmile znovu napíšeš do chatu, AFK končí. Bot tě přivítá zpátky, napíše, jak dlouhá byla nepřítomnost a kdo se po tobě ptal. Ta zpráva zmizí po 15 sekundách.
- **Příkazy během AFK:** samotné `!afk` AFK ukončí a `!afk <nový důvod>` změní důvod.
- **Úklid:** po tvém návratu bot smaže oznámení o AFK i odpovědi na zmínky. Změna důvodu smaže staré oznámení hned.
- **Přehled:** `!users` ukáže, kdo je AFK.

## Ruleta

Losování, ve kterém se vítězná osoba posune na začátek fronty.

1. **Bouncer** napíše `!ruleta`. Bot ohlásí kolo všem (`@everyone`) a otevře minutu na přihlášení.
2. Kdokoli se přidá příkazem `!join`. Kdo už je v ruletě, dostane jednou připomínku; další `!join` už nic neudělá, takže se nedá spamovat. `!join`, když žádné kolo neběží, také nic neudělá.
3. Po minutě bot náhodně vylosuje vítěze a oznámí výsledek.
4. Vítěz se přidá do fronty, pokud v ní není, a pak se posune na pozici 1. Oznámení řekne odkud, např. „Posun z #5 na #1“.

- **Vítězí DJ:** pokud los padne na toho, kdo zrovna hraje, bot to oznámí a losuje znovu ze zbytku. Je-li DJ v ruletě sám, nevyhrává nikdo.
- **Nikdo se nepřidal:** bot to oznámí.
- **Vítěz odešel:** pokud vítěze nejde zařadit do fronty (třeba kvůli odchodu), vítězství se oznámí, ale nikdo se neposouvá.

## Automatické přeskočení

Bot přeskočí skladbu, která se místnosti zjevně nelíbí: jakmile meh tvoří aspoň polovinu všech woot a meh dohromady (4 meh na 4 woot, nebo 1 meh na žádný woot). Grab se nepočítá.

- Nikdy nepřeskakuje v prvních 30 sekundách skladby a u jedné skladby zasáhne nejvýš jednou.
- Při přeskočení napíše výsledek hlasování: `⏭️ Automaticky přeskakuji · 👍 4 · 👎 4`.

## Vláček emotů

Když 3 různí lidé pošlou stejný emote (výchozí `:kong:`) do 2 minut po sobě, bot se přidá dávkou 5 až 15 kusů.

- Pak počítá znovu od nuly.
- Mezi dávkami čeká aspoň 15 sekund.
- Příkazy a boti se nepočítají.

## Oslava plné místnosti

Když se místnost příchodem někoho naplní na 10 lidí (boti se nepočítají), bot to oslaví náhodným řádkem a označí toho, kdo desítku dovršil.

Znovu slaví až poté, co místnost klesne na 8 nebo méně a uplynou 3 hodiny. Místnost, ve které je 10 lidí už při startu bota, neoslavuje.

## Uklizený chat

- **Příkazy se mažou**, jakmile na ně bot odpoví. Týká se všeho, co začíná `!`, včetně překlepů a neznámých příkazů.
- **Zprávy bota se mažou** po hodině. Odpovědi na `!help` zmizí po minutě, potvrzení `!clear` po 10 sekundách a přivítání po AFK po 15 sekundách.
- **`!clear`** umožní bouncerovi smazat vše, co má bot ještě v chatu.
- **Dlouhé odpovědi** se dělí až na čtyři očíslované zprávy (`(1/3)`), protože Wavez odmítá zprávy delší než 300 znaků.

## Hláška při startu

Když se bot připojí a je připravený odpovídat, napíše krátký řádek, ve výchozím stavu s odkazem na `!help`.

## Styl odpovědí

Všechny odpovědi mají stejnou podobu, aby se v nich místnost rychle vyznala:

- jeden emoji na začátku podle druhu odpovědi (`🎵` skladba, `🎧` fronta, `📊` hlasy, `⚠️` chyba nebo nápověda k použití)
- ` · ` mezi položkami, `, ` mezi jmény
- `Název — Interpret` u skladby

```
🎵 Blue Veins — Ash Walker · zbývá 2:41
📊 ▰▰▰▰▰▰▰▱▱▱ 72% · 18/25 · líbí se
🛡️ Host: Ann · Bouncer: Bo, Cy
```

## Co si bot pamatuje přes restart

Tohle si bot pamatuje i přes restart:

- stav AFK
- kdo naposledy psal a co naposledy pustil
- nastavené `!escort`
- posledních 20 skladeb
- vlastní odpovědi
- zvolený jazyk
- účastníky rulety

Hlasy se neukládají. `!score` a `!votes` jsou po restartu prázdné až do dalšího hlasu.
