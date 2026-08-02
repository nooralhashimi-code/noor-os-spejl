---
type: test
status: AFSLUTTET — konklusion: skim:// (se CLAUDE.md)
opdateret: 2026-08-02
---

# Linktest — afsluttet 2026-08-02

**Endelig konklusion: `skim://` med `#page=N` og fuldt procent-kodet sti.**
Hookmark blev afprøvet grundigt (runde 3) og fravalgt: den åbner filen, men
videresender ikke sidetallet. Skrevet ind i `CLAUDE.md` under *Vis links
til sidst*. Denne fil dokumenterer, hvordan vi kom dertil — testene behøver
ikke køres igen.

## Resultaterne

| Variant | Form | Resultat |
|---|---|---|
| A | `file://` rå sti, vinkelparenteser, `#page=609` | intet |
| B | `file://` fuldt kodet, `#page=609` | intet |
| C | `file://` delvist kodet, `#page=609` | intet |
| D | `computer://` fuldt kodet, `#page=609` | dialog i Cowork, derefter intet |
| E | `file://` rå sti, vinkelparenteser, **intet fragment** | **åbner i Skim** (side 1) |
| F | `file://` fuldt kodet, **intet fragment** | **åbner i Skim** (side 1) |
| G | `file://` `#609` (Skim-notation) | intet |
| H | `file://` `%23page=609` | intet |
| I | `file://` `?page=609` | intet |
| **J** | **`skim://` fuldt kodet, `#page=609`** | **✅ åbner Skim på side 609** |
| K | `file://` `%23609` | intet |

## Hvad testen lærte

1. **Obsidian videresender ikke fragmentet på `file://`-links.** A/B/C var
   identiske med E/F fraset `#page=` — og kun de fragmentløse virkede.
   Fejlen lå altså i Obsidian-leddet, ikke i stien og ikke i PDF-appen.
2. **`skim://` går uden om problemet**, fordi hele URL'en overdrages til
   Skim, som selv tolker fragmentet. Forudsætter naturligvis, at Skim er
   installeret — det er den eneste afhængighed i løsningen.
3. **`computer://` er Cowork-internt.** macOS har ingen handler; skemaet kan
   pr. definition ikke virke uden for chatten. Bekræfter den stående regel om
   aldrig at antage, at et skema bæres fra én overflade til en anden.
4. **PDF-side ≠ trykt side.** Noors fund ved J: PDF-side 609 er trykt side
   597 i Core Radiology — 12 siders forskel fra forsatspapir og forord.
   Korpussets markører er PDF-sider, så det er dem, der skal bruges; det står
   nu i CLAUDE.md.

## Runde 3 — Hookmark (afgjort samme dag)

`skim://` løste sidespringet, men **hook://** blev alligevel valgt, fordi
det som det eneste **overlever filflytninger og omdøbninger**. Broen måtte
bygges fra bunden (`Skills/generators/hookmark/hookmark-bridge.sh`) —
den installerede skill er dokumentation til en ældre Hook-version og
foreskriver en kommando, der ikke findes i Hookmark 7.

**Resultat: FRAVALGT.** Alle fire fragment-former (ID alene eller fuld URL,
`#page=` eller `?page=`) åbner bogen — men **ingen af dem springer til
siden**. Hookmark videresender ikke sidetallet til Skim for et bogmærke,
der er skabt fra en ren filsti. Testet også med bogen allerede åben og
efter genstart af både Obsidian og Skim: samme resultat.

**Broen består alligevel** (`Skills/generators/hookmark/hookmark-bridge.sh`)
— hook-links er stadig den eneste form, der overlever filflytning, så de er
brugbare, hvor filidentitet betyder mere end sidespring.

**To lærdomme om selve fejlsøgningen:**

1. **Bekræftelser skal være specifikke.** "Alle fire virker" blev læst som
   "alle fire springer til siden", men betød "alle fire åbner bogen" — og
   den fejllæsning kostede en hel runde. Spørg til det, der faktisk skal
   afgøres: *"åbner den på side 609, eller på forsiden?"*
2. **Dropbox-forsinkelse ligner en linkfejl.** Redigeres noten fra Cowork,
   kan man nå at klikke på den gamle udgave. Ved tvivl: se på selve linket i
   Obsidian, før linkformen mistænkes.
