# Mapa del laberint

Eina web (un sol fitxer, sense dependències) per dibuixar i portar el control d’un laberint mentre el explores. Està pensada per anotar les sales, les sortides, els cofres, les inscripcions i, ara també, el resultat de les **proves** amb el seu efecte sobre els **llums**.

## Com s’obre

Obre `index.html` amb qualsevol navegador (no cal servidor ni connexió). Tot es desa automàticament a `localStorage` del navegador, de manera que pots tancar i tornar a obrir sense perdre’l.

## Configuració

A dalt de tot hi ha l’apartat desplegable **«Configuració (valors del joc)»**. Serveix per ajustar tots els valors del joc:

| Opció | Què fa | Valor per defecte |
| --- | --- | --- |
| Llums inicials | Llums amb què comences | `0` |
| Llums per pas | Llums que costa moure’s d’una sala a una altra | `1` |
| Prova ben feta (+ llums) | Llums que se sumen si la prova surt bé | `2` |
| Prova mal feta (− llums) | Llums que es resten si la prova surt malament | `1` |
| Cofre (+ llums, per defecte) | Valor que se li assigna a un cofre nou | `3` |
| Canvi de sala (+ / −, per defecte) | Valor inicial del camp «Canvi de llums d’aquesta sala» | `0` |

Els canvis s’apliquen a l’instant i es conserven en reiniciar (`Torna a començar` manté la configuració).

## Com funcionen les proves

Quan entres en una sala marcada com a **«Prova obligatòria»** o **«Prova opcional»**, apareix una pregunta:

> **Has fet bé aquesta prova?**

- **Sí, ben feta** → suma els llums configurats a «Prova ben feta».
- **No, mal feta** → resta els llums configurats a «Prova mal feta».
- **Respondre després** → deixa la prova pendent; pots respondre’n quan vulguis després, tocant la sala al mapa o des de la targeta de la sala.

El resultat es registra **un cop per sala** i es pot canviar en qualsevol moment amb els botons `✔ Ben feta` / `✘ Mal feta` de la targeta de la sala. El balanç de proves apareix al comptador de llums (`Proves: +N` o `Proves: −N`) i a l’exportació en PDF.

## Càlcul dels llums

```
llums actuals = inicials + cofres + canvis de sala visitades + proves − (passos × llums per pas)
```

Només compten els canvis de sala i les proves de les sales visitades. Si no tens prous llums per tornar a l’inici, el comptador ho avisa.

## Ús bàsic

- **Nord / Sud / Est / Oest** (o les fletxes del teclat): et mous i el mapa es dibuixa sol.
- Toca una sala del mapa per veure’n els detalls i prem **«Vés-hi»** per desplaçar-t’hi.
- Marca amb els botons **Cofre**, **Final**, **Prova obligatòria** o **Prova opcional** els elements de la sala actual.
- Escriu les **sortides**, els llums del cofre, el **canvi de llums** de la sala, la **inscripció** i una **nota** lliure.
- **Desfés l’últim pas**, **Torna a començar** i **Descarrega l’estat en PDF** (mapa, resum, inscripcions i taula de sales, inclòs l’estat de les proves).

## Contacte

Al peu de pàgina hi ha el botó **«✉ Contacto y sugerencias»**. Obre un formulari per enviar suggerències o reportar errors (nom, correu opcional, motiu i missatge). En prémer **«Abrir correo»** s'obre l'aplicació de correu de l'usuari amb el missatge preparat i els dos destinataris: `marcelbon2008@gmail.com` i `eduardomues2008@gmail.com`. El formulari es pot tancar amb **Cancelar**, amb la **X**, fent clic fora o amb la tecla **Esc**.

## Fitxers

- `index.html` — aplicació completa (HTML, CSS i JavaScript), amb el peu de pàgina del centre i els crèdits de desenvolupament.
- `assets/logo-thos-i-codina.png` — logotip del IES Thos i Codina, desat localment perquè el peu de pàgina funcioni sense connexió.
- `README.md` — aquesta documentació.
