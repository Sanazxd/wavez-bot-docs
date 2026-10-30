# Wavez Bot

🇬🇧 [English](../en/README.md)

Wavez Bot odpovídá na příkazy v chatu místnosti na [Wavez.fm](https://wavez.fm), vítá příchozí, pořádá ruletu a dává štábu nástroje na moderaci. Mluví česky a anglicky.

Jde o fork původního projektu [fluteds/wavez-bot](https://github.com/fluteds/wavez-bot) od autora fluteds. Co je jinak, popisuje [seznam změn](changelog.md).

## V místnosti

Napiš do chatu `!help`. Bot vypíše kategorie příkazů, které můžeš používat, a kolik příkazů v každé je. Odtud:

- `!help zábava` vypíše příkazy jedné kategorie
- `!help seen` vysvětlí jeden příkaz: jak se používá a kdo ho smí použít

Vidíš jen to, co ti dovoluje tvoje role, takže běžní uživatelé moderátorské příkazy neuvidí.

Napsané příkazy bot po odpovědi smaže, jeho odpovědi zmizí po minutě a ostatní zprávy po hodině, takže chat zůstává přehledný.

Samotné `!help` navíc odkazuje na tuto dokumentaci.

## Stránky

| Stránka | Co v ní je |
| --- | --- |
| [Příkazy](commands.md) | všechny příkazy s aliasy, použitím a nejnižší rolí |
| [Funkce](features.md) | co bot dělá sám od sebe: uvítání, AFK, ruleta, automatické přeskočení, vláček emotů |
| [Role](roles.md) | žebříček rolí, VIP, platformní tituly, kdo smí zasahovat proti komu |
| [Seznam změn](changelog.md) | tento fork v porovnání s originálem |

## Jazyk

Bot mluví česky nebo anglicky. Manager nebo výš ho přepne příkazem `!cz` nebo `!en`. Volba vydrží i restart.
