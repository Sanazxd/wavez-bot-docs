# Role

🇬🇧 [English](../en/roles.md) · [← Zpět](README.md)

## Žebříček

Od nejnižší po nejvyšší:

```
user < vip < resident_dj < bouncer < manager < cohost < host
```

Příkaz pro nějakou roli může použít tato role a všechny vyšší. „Bouncer“ tedy znamená bouncery, managery, co-hosty i hosta.

| Role | Co jí bot zpřístupní |
| --- | --- |
| user | všechny příkazy z kategorií info, zábava a fronta |
| vip | vlastní uvítání; žádná další práva |
| resident_dj | vlastní uvítání; žádná další práva |
| bouncer | skip, kick, mute, unmute, remove, move, lock a unlock, `!clear`, otevření kola rulety |
| manager | ban, unban, `!addcmd`, `!delcmd`, `!en`, `!cz` |
| cohost, host | všechno výše |

## Kdo smí zasahovat proti komu

Kromě role, kterou příkaz vyžaduje, platí:

- bota nemůže nikdo vyhodit, zabanovat, ztlumit, přesunout ani odebrat
- nikdo nemůže zasahovat proti někomu se stejnou rolí
- nikdo nemůže zasahovat proti nikomu nad sebou

Bouncer tedy nevyhodí jiného bouncera ani managera, ale VIP nebo resident DJ ano.

## Neznámé role

Pokud Wavez u člověka nahlásí roli, kterou bot nezná (třeba po přejmenování na straně Wavez), tato osoba nedostane žádná práva a přes bota ji nikdo nemůže vyhodit, zabanovat ani ztlumit. Přejmenovaná role se tak nikdy nestane bezpečnostní dírou.

## Platformní tituly

Wavez má i tituly platné pro celou platformu, jako `admin` a `ambassador`. Samy o sobě v místnosti nic neznamenají: ambasador bez role v místnosti je tu `user`.

Bot počítá dva z nich jako role v místnosti:

| Platformní titul | Platí jako |
| --- | --- |
| `admin` | manager |
| `ambassador` | bouncer |

- Platí vyšší z obou rolí, takže nikoho to nedegraduje: ambasador, který je zároveň host, zůstává hostem.
- Titul i chrání: obyčejný bouncer nevyhodí ambasadora.
- Ostatní tituly, třeba `subscriber`, pro bota nic neznamenají.
- Titul nemění uvítání. Ambasador dostane obyčejné uvítání, ne to pro štáb.

`!user <jméno>` ukáže tituly daného účtu.
