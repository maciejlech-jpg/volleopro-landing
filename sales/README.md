# VolleoPro — system sprzedaży

Ten katalog to cały „dział sprzedaży” VolleoPro. Jest tak zaprojektowany, żeby Maciej robił tylko dwie rzeczy: **prowadził 20-minutowe demo** i **podpisywał umowy**. Resztę (research, pisanie maili, follow-upy, aktualizacja pipeline'u, raport tygodniowy) wykonuje Claude w cotygodniowej rutynie.

## Struktura

| Plik | Co to jest |
|---|---|
| `leads/kluby.csv` | Baza wszystkich klubów i organizacji siatkarskich w Polsce z kontaktami publicznymi. Źródło prawdy o tym, **do kogo** pisać. |
| `pipeline.csv` | Stan każdego leada: etap, data ostatniego kontaktu, następny krok. Źródło prawdy o tym, **co dalej**. |
| `outreach/sekwencja-email.md` | 4-mailowa sekwencja cold outreach w dwóch ścieżkach (sztab / decydent) + LinkedIn + odpowiedzi na reakcje. |
| `materialy/cennik.md` | Pakiety, ceny, matematyka do 30 000 zł MRR i harmonogram. **Wymaga zatwierdzenia.** |
| `materialy/skrypt-demo.md` | Scenariusz prezentacji minuta po minucie. |
| `materialy/obiekcje.md` | Tabela obiekcji i odpowiedzi. |
| `materialy/one-pager.md` | Podsumowanie do wysłania po demo. |

## Etapy w pipeline.csv

`nowy` → `mail1` → `mail2` → `mail3` → `mail4` → `uspiony` (wraca za 90 dni)
lub z dowolnego etapu → `odpowiedz` → `demo_umowione` → `demo_odbyte` → `pilotaz` → `klient` / `stracony`

## Cotygodniowy cykl (rutyna Claude, poniedziałek rano)

1. Odczytaj `pipeline.csv`. Dla każdego leada, któremu minął termin następnego kroku, przygotuj mail z sekwencji (właściwa ścieżka, właściwy numer maila, wypełnione zmienne).
2. Wybierz 30–40 nowych leadów z `leads/kluby.csv` (priorytet: PlusLiga/Tauron Liga, potem 1 Liga, potem reszta), przygotuj mail 1.
3. Zapisz wszystkie maile jako **wersje robocze w Gmailu** Macieja (nie wysyłaj). Maciej rano przegląda i wysyła jednym kliknięciem każdy, ok. 15 minut.
4. Sprawdź skrzynkę pod kątem odpowiedzi od klubów. Odpowiedzi z zainteresowaniem: przygotuj propozycję dwóch terminów demo i wersję roboczą odpowiedzi. Odmowy: oznacz `stracony` z powodem.
5. Zaktualizuj `pipeline.csv`, zrób commit i push na gałąź.
6. Wyślij Maciejowi krótki raport: ile maili do wysłania, ile odpowiedzi, ile demo umówionych, MRR.

## Co robi Maciej (cel: poniżej 3 godzin tygodniowo)

- Poniedziałek: 15 minut, wysłanie przygotowanych wersji roboczych.
- W tygodniu: demo (20 minut każde, zwykle 1–4 tygodniowo).
- Po demo: podpisanie umowy, wystawienie faktury (do zautomatyzowania w kolejnym kroku).

## Następne kroki do zbudowania (kolejne sesje)

1. **Samodzielny onboarding klubu** w aplikacji (formularz: lista zawodników, sztab, role), żeby wdrożenie nie wymagało ręcznej pracy.
2. **Płatności**: faktury cykliczne (Fakturownia / inFakt API) + Stripe dla pakietu Akademia.
3. **Booking demo** na landingu zamiast mailto (Google Calendar Appointment Schedules lub Cal.com), CTA prowadzi bezpośrednio do kalendarza.
4. **Baza wiedzy i chatbot wsparcia** dla klubów, żeby pytania „jak dodać zawodnika” nie trafiały do Macieja.
5. **Case study Necko Augustów** (liczby: wypełnialność ankiet, wykryte przeciążenia), najsilniejszy materiał sprzedażowy.
