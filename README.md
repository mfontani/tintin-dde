# tintin-dde

Un set di scripts/"UI" per Dei delle Ere, un MUD italiano.

```bash
tt++ ./dde.tt++
```

# Features

La UI e' composta da:

    [ canali comunicazione      ][ tab RHS ]
    [ testo mud                 ][         ]
    [        ...                ][         ]
    [           ....            ][         ]
    [ prompt su 3 linee         ][         ]
    [input                                 ]

Il tutto viene popolato dai dati "GMCP" inviati dal MUD:

- messaggi inviati in canali pubblici e privati compaiono nella parte superiore della interfaccia. Usare rotellina del mouse per scroll.
- log su `.log.txt`, che viene poi ri-mostrato alla disconnessione
- il testo inviato dal MUD appare nella parte centrale
- il prompt compare nella parte inferiore, su tre linee:
  - info sul gruppo
  - magie
  - stato del personaggio
- i tabs a destra (RHS) contengono informazioni utili:
  - corrente equipaggiamento, senza espansione contenuto
  - inventario, "espanso" con i contenuti
  - magie, proprieta', cooldown, etc.
  - se in gruppo, info sui componenti del gruppo:
    - nome, hp, mana, move
    - incantesimi
  - informazioni sulle memorizzazioni da stregone

# Setup

## Configura le tue credenziali

Crea un `.creds.tt++` dove metti il tuo nome account e password. Il file e' in `.gitignore` e non verra' tracciato da Git.

```
#variable {DDE_ACCOUNT_NAME} {...};
#variable {DDE_ACCOUNT_PASSWORD} {...};
```

Se vuoi fare auto-login con UN personaggio, metti pure:

```
#action {^Cosa vuoi fare oggi?} {NomePG};
```

Se vuoi auto-entrare nel MUD, senza cambiare opzioni o altro, metti pure:

```
#action {^1) Entra nel MUD} {1};
```

## Configura altro

Se vuoi, puoi usare `.creds.tt++` anche per configurare altri aspetti della UI, come ad esempio:

```
#variable {screen_right_width} {30};
```

... se vuoi una "parte a destra" piu' stretta.

Non tutto e' ancora configurabile cosi'.

# Tue Modifiche

Puoi modificare di tutto in `actions/`, `ui/` etc. ma le modifiche che fai verranno tracciate da Git.

Se pensi che siano interessanti da avere anche in questo repository e non solamente per le tue preferenze, fai pure una pull request.

# Roadmap

- [ ] muovere parti di configurazione (colori, etc) in modo che possa esser fatto override via `.creds.tt++`
- [ ] nascondere tab "inutili" come `Memo` per non-stregoni
- [ ] tab per missioni/esplorazioni
