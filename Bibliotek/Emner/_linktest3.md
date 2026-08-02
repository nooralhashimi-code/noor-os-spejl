---
type: test
opdateret: 2026-08-02
---

# Linktest 3 — links til forelæsninger med tidsstempel

Alle peger på **samme klip**: Radiopaedia, Trauma Radiology Course 004,
**12:29** (= 749 sekunder) — dér hvor pseudoaneurisme omtales.
Klik i Obsidian. Notér for hver: *intet · åbner fra start · åbner ved 12:29*.

## Gruppe 1 — afspillere med eget URL-skema

**P. IINA med starttid**

[P — iina + mpv_start](iina://open?url=file%3A%2F%2F%2FVolumes%2FT9%2FDropbox%2FVideo%2520Lectures%2F_Radiopedia%2FCourses%2F080.%2520Trauma%2520Radiology%2520-%2520004%2520-%2520Trauma%2520Radiology%2520Course%2520%257C%2520Radiopaedia.org.mp4&mpv_start=749)

**Q. IINA uden starttid** (kontrol: virker skemaet overhovedet?)

[Q — iina, ingen tid](iina://open?url=file%3A%2F%2F%2FVolumes%2FT9%2FDropbox%2FVideo%2520Lectures%2F_Radiopedia%2FCourses%2F080.%2520Trauma%2520Radiology%2520-%2520004%2520-%2520Trauma%2520Radiology%2520Course%2520%257C%2520Radiopaedia.org.mp4)

**R. VLC med starttid**

[R — vlc + start-time](vlc:///Volumes/T9/Dropbox/Video%20Lectures/_Radiopedia/Courses/080.%20Trauma%20Radiology%20-%20004%20-%20Trauma%20Radiology%20Course%20%7C%20Radiopaedia.org.mp4?start-time=749)

**S. VLC, dokumentationens form**

[S — vlc://file://…](vlc://file:///Volumes/T9/Dropbox/Video%20Lectures/_Radiopedia/Courses/080.%20Trauma%20Radiology%20-%20004%20-%20Trauma%20Radiology%20Course%20%7C%20Radiopaedia.org.mp4?start-time=749)

## Gruppe 2 — QuickTime / standardafspiller

**T. Rå fil, intet tidsstempel** (kontrol)

[T — file://, ingen tid](<file:///Volumes/T9/Dropbox/Video%20Lectures/_Radiopedia/Courses/080.%20Trauma%20Radiology%20-%20004%20-%20Trauma%20Radiology%20Course%20%7C%20Radiopaedia.org.mp4>)

**U. file:// med t-fragment**

[U — file:// #t=749](<file:///Volumes/T9/Dropbox/Video%20Lectures/_Radiopedia/Courses/080.%20Trauma%20Radiology%20-%20004%20-%20Trauma%20Radiology%20Course%20%7C%20Radiopaedia.org.mp4#t=749>)

---

## Hvad jeg gør med svaret

- **Virker P eller R:** tidsstemplerne i "Klip fra forelæsningerne" bliver
  klikbare på samme måde som sidetallene i Kilder — ét link pr. klip.
- **Virker kun Q/S/T:** vi kan linke til forelæsningen, men ikke til
  tidspunktet; tiden står så som tekst ved siden af (som sidetallene gjorde,
  før `skim://` blev fundet).
- **Virker intet:** så er vejen Universal Player — den er netop bygget til
  klikbare tidsstempler i en notefil ved siden af videoen.

**Bemærk:** hvad der åbner, afhænger af hvilke apps du har. Sig gerne om du
har IINA og/eller VLC — så ved jeg, om et dødt link betyder "forkert
syntaks" eller "appen findes ikke".
