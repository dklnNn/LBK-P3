# BUILD BOOK – M1, pakiet P3 „Obraz, ocena, pobudzenie”

**Etap:** M1 – Karta projektu · **Data aktualizacji:** 2026-11-23
**Zakres wydania M1:** metryczka (0), mapa protokół → PsychoPy (2) oraz odstępstwa i pytania do LBK (14).
**Uwaga:** tabela reguł adaptacji **v0** znajduje się w karcie projektu M1; implementacja i dokumentacja późniejszych etapów nie są częścią tego pakietu.

## 0. Metryczka
- **Pakiet:** P3 – Obraz, ocena, pobudzenie (**do potwierdzenia przydziału na forum**).
- **Badanie główne:** „Qualia, barwa i subiektywne doświadczenie”.
- **Badanie drugie:** „Reklama spod ręki człowieka czy algorytmu?”.
- **Protokół badania głównego:** `Badania_EyeTracking.pptx`, slajdy 3–14 oraz 22 (na slajdzie tytułowym oznaczenie „2025”); uzupełniająco plakat `Badanie_Eyetracking_Qualia_Barwa_i_Subiektywne_Doswiadczenie_2026.jpeg` (kod QBS01, „2026”). Obowiązująca wersja i data protokołu wymagają potwierdzenia LBK (pyt. 14.22).
- **Zespół:** DK – Diana Kalinina - 164014; OS - Oleksandr Shamak - 161578
- **Podział pracy i autorstwa w M1:** **DK** – prowadzenie, redakcja i aktualizacja dokumentacji M1/Build Book (rozdz. 0, 2 i 14), opracowanie opisów kroków, tabel oraz zebranie pytań i odstępstw; ponadto instalacja PsychoPy i uruchomienie demonstracji. **OS** – analiza techniczna protokołu i materiałów P3, przygotowanie ustaleń i pytań merytorycznych, uruchomienie symulatora i 60-sekundowego nagrania oraz weryfikacja pól, jakości danych i integracji (pylsl, LabRecorder, MouseGaze, EyeLogic/GSR-EDA).
- **Sposób oznaczania wkładu:** „opracowanie dokumentacji” wskazuje osobę redagującą Build Book, a „analiza / autor pytania” wskazuje wkład merytoryczny. Oba rodzaje pracy są częścią M1; wpisy nie są deklaracją udziału procentowego.
- **Repozytorium:** [TU WPISZ LINK DO PRYWATNEGO REPOZYTORIUM]. **Tag do oddania M1:** `M1` (do utworzenia i weryfikacji).
- **Komputer do wykonania KL-A:** MacBook Air z Apple Silicon; **system:** macOS.
- **PsychoPy:** aplikacja Standalone pobrana jako `StandalonePsychoPy-2025.2.4-macOS-3.10.dmg`; w uruchomionej aplikacji widoczna była wersja **2025.2.4beta**.
- **Uruchomienie aplikacji:** przez Rosetta 2 (wersja instalacji dla procesorów Intel).
- **Python używany w terminalu:** `python3`; dokładna wersja: Python 3.9.6 . Wersja Pythona wewnątrz PsychoPy może być inna.
- **Stanowisko deweloperskie:** MacBook Air 13″ (M5), macOS Tahoe 26.6, wyświetlacz Liquid Retina 13,6″, rozdzielczość 2560 × 1664 px, częstotliwość odświeżania 60 Hz.
- **Stanowisko laboratoryjne LBK:** komputer z systemem Windows. Rozdzielczość ekranu, częstotliwość odświeżania oraz konfiguracja Monitor Center w PsychoPy zostaną sprawdzone i uzupełnione podczas sesji integracyjnej w LBK.
- **Aparatura LBK:** EyeLogic (wzrok), GSR/EDA, ECG, oddech. Wersje sterowników i ustawienia stanowiska zostaną sprawdzone w LBK.


## 2. Mapa protokół → PsychoPy

### Krok 2.1 – Źródła protokołu badania głównego
**Opracowanie dokumentacji:** DK · **Analiza merytoryczna:** OS · **Data:** 2026-11-23
- **Cel:** ustalić, które pliki pakietu P3 są protokołem badania głównego (QBS01).
- **Gdzie:** folder „Pakiet P3 – materiały badań LBK”.

| Plik | Co zawiera | Data / wersja |

| `Badania_EyeTracking.pptx` | protokół badania głównego: slajdy 3–14 (hipotezy, projekt, grupa, bodźce A–D, ankieta, analiza) i 22 (sprzęt); slajdy 15–21 – badanie drugie | slajd 1: „PROJEKT BADAWCZY · 2025”, brak daty pliku w treści |

| `Badanie_Eyetracking_Qualia_Barwa_i_Subiektywne_Doswiadczenie_2026.jpeg` | plakat rekrutacyjny, kod badania **QBS01**, ok. 35 min, kryteria | 2026 |

| `Bodziec A.PNG` … `Bodziec D.PNG` | podgląd bodźców (ok. 715×476 / 594×476 px) | – |

| `Zalacznik_A/B/D_*.docx`, `Badanie9_*` | dotyczą **badania drugiego** (Badanie 9 – reklama AI/człowiek), nie badania głównego | – |


Bodźce w eksperymencie wzięto z oryginałów w prezentacji (slajdy 9–12, 1536×1024 i ok. 1400×1122 px), bo pliki `Bodziec *.PNG` mają niską rozdzielczość.
- **Jak sprawdzić:** slajd 3 prezentacji ma tytuł „BADANIE 1 – Qualia, Barwa i Subiektywne Doświadczenie”; załączniki A, B, D mają w nagłówku „Badanie 9”.

### Krok 2.2 – Mapa element protokołu → routine/komponent → parametry → status
**Opracowanie dokumentacji:** DK · **Analiza merytoryczna:** OS · **Data:** 2026-11-23
- **Cel:** każdy ekran/węzeł protokołu ma odpowiednik w aktualnym szkicu eksperymentu P3 (`experiment/P3_KLD.psyexp` w repozytorium zespołu) albo opisane odstępstwo.
- **Gdzie:** Builder → Flow: `instrukcja` → pętla `trials` [`gate` → `obraz` → `szary` → `sam`] → `koniec`.

| # | Element protokołu (źródło) | Routine / komponent | Parametry | Status |
| 1 | Świadoma zgoda (sl. 7 – kryteria włączenia) | brak | – | **odstępstwo – do dodania**: ekran zgody w eksperymencie (wymóg KL-G); treść zgody dla badania głównego nie jest w pakiecie (Zał. B dotyczy Badania 9) → pyt. 14.18 |

| 2 | Screening: test Ishihary, kwestionariusz CSS-15 (sl. 6) | brak (poza PsychoPy) | – | **do decyzji LBK** – na papierze przed sesją czy w eksperymencie? → pyt. 14.11 |

| 3 | Dane uczestnika: podgrupa Artyści / STEM / Kontrolna (sl. 7) | okno startowe (`Experiment info`) | obecnie: participant, session, adaptacja, warunki | **odstępstwo – do dodania** pole `grupa`; kod osoby tylko pseudonim |

| 4 | Kalibracja eye-trackera 9-punktowa (sl. 6) | brak (MouseGaze nie wymaga) | – | **do dodania** komponent kalibracji ioHub/EyeLogic przed instrukcją; walidacja – kryterium nieokreślone → pyt. 14.10 |

| 5 | Instrukcja: swobodna eksploracja wzrokowa (sl. 6) | `instrukcja` (`instr_text`, `instr_key`) | tekst własny, klawisz `space`; tu liczona linia bazowa EDA (pierwsze 10 s dobrych próbek) | **zgodne** (treść instrukcji nie jest podana w protokole – do zatwierdzenia → pyt. 14.17) |

| 6 | Bodziec, ekspozycja 4 s (sl. 6, 22) | `obraz` / `stim` (Image) | 4000 ms (= 240 klatek przy 60 Hz), `size (1.7778, 1)` w jednostkach `height`, obraz 1920×1080 z szarym tłem; znaczniki `stim:onset`/`stim:offset` na odświeżeniu ekranu | **zgodne** (zmierzone 3992–4019 ms przy ok. 45 kl./s w oknie; w LBK zmierzyć przy 60 Hz) |

| 7 | ISI 1 s, szary ekran (sl. 6) | `szary` / `blank` | 1000 ms, tło `[0,0,0]` rgb (= szary 128) | **zgodne**; jasność/kolor szarego ekranu nie są określone → pyt. 14.15 |

| 8 | Bodźce A–D: pejzaż ciepły/zimny, twarz ciepła/zimna (sl. 8) | plik warunków `conditions/main.csv` | kolumny `stim_id, image, kategoria, tonacja`; pliki `stimuli/P3_A..D_*.png` | **zgodne co do zestawu**; niezgodność z deklaracją „identyczne strukturalnie” → pyt. 14.6 |

| 9 | 30 prób × (4 s + 1 s) (sl. 6) | pętla `trials` (sequential, nReps 1) | obecnie 4 próby (`main.csv`), 12 w `test_mix.csv` (tylko test) | **odstępstwo** – 30 prób przy 4 bodźcach (+4 achromatycznych) nie wynika z protokołu → pyt. 14.7 |

| 10 | Warunek kontrolny: wersje achromatyczne (sl. 6, H4) | brak | – | **do dodania**: skrypt generujący wersje w skali szarości + wiersze w pliku warunków; sposób włączenia do sesji nieokreślony → pyt. 14.8 |

| 11 | Kontrbalansowanie – kwadraty łacińskie (sl. 6) | brak (kolejność z pliku) | – | **do dodania**: 4 listy (kwadrat łaciński 4×4) wybierane w oknie startowym; sposób przypisania list → pyt. 14.9 |

| 12 | Pauza po 15 próbach (sl. 6) | brak | – | **do dodania**: routine `pauza` warunkowo po próbie 15 (tempo uczestnika); długość pauzy nieokreślona → pyt. 14.7 |

| 13 | Ankieta SAM 9-stopniowa: walencja, pobudzenie, dominacja (sl. 6, 13) | `sam` / `sam_val`, `sam_aro`, `sam_dom` (Slider) | ticks 1–9, opisy słowne na końcach, zakończenie spacją po zaznaczeniu 3 skal | **odstępstwo**: SAM po każdym obrazie, a protokół mówi raz „po każdym bloku bodźców” (sl. 6), raz o reakcji „na obraz” (sl. 13); brak piktogramów SAM → pyt. 14.12 |

| 14 | Ankieta post-experimentum – Blok B (Likert 1–7, 4 pozycje) (sl. 13) | brak | – | **do dodania** (Slider 1–7); czy po każdym obrazie, czy raz na końcu → pyt. 14.13 |

| 15 | Blok C – pytania otwarte (2) (sl. 13) | brak | – | **do dodania** (Textbox); j.w. → pyt. 14.13 |

| 16 | Blok D – metapoznanie (2 pytania, bez skali) (sl. 13) | brak | – | **do dodania**; format odpowiedzi nieokreślony → pyt. 14.13 |

| 17 | Sonda uwagowa dot-probe – czas reakcji (sl. 6) | brak | – | **do decyzji LBK**: brak opisu procedury → pyt. 14.14 |

| 18 | GSR – pobudzenie (sl. 6, 22: Shimmer3 GSR+) | `state.py` (LSL `LBK_Sim` lokalnie), LabRecorder → XDF | strumień Physio, 4 Hz w symulatorze | **zgodne lokalnie**; urządzenie, nazwa strumienia i częstotliwość w LBK nieznane → pyt. 14.4 |

| 19 | Eye-tracker ≥ 120 Hz, dokładność < 0,5° (sl. 22: Tobii / EyeLink) | ustawienia eksperymentu → Eyetracking: MouseGaze (lokalnie) / EyeLogic (LBK) | ioHub; `et_start` / `et_stop` (Eyetracker Record) | **odstępstwo** – w LBK jest EyeLogic, nie Tobii/EyeLink → pyt. 14.16 |

| 20 | Monitor 24", 1920×1080, 60 Hz, 60 cm (sl. 22) | ustawienia okna + Monitor Center | okno 1920×1080, pełny ekran, jednostki `height` | **do ustawienia** profilu w Monitor Center na stanowisku LBK |

| 21 | AOI-1…AOI-4: centrum, tło górne, tło dolne, peryferie (sl. 8) | brak (analiza poza eksperymentem / ROI) | – | **do uzupełnienia**: brak współrzędnych AOI dla badania głównego → pyt. 14.19 |

| 22 | Łączny czas ~35 min z przerwami (sl. 6, plakat) | – | sama część bodźcowa: 30 × 5 s = 2,5 min + SAM | **niespójność** – czym wypełnione jest 35 min → pyt. 14.7 |

| 23 | (poza protokołem) planowana warstwa adaptacyjna v0 | `gate` (`gate_code`, `gate_text`) | tylko między próbami; wyłącznik `adaptacja = tak/nie`; R1–R4 | **dodatek zgodny z zasadą nienaruszalności** – nie zmienia ekspozycji, kolejności ani treści |

| 24 | Zakończenie | `koniec` (`end_text`, `et_stop`) | 3 s, tekst własny | **zgodne**; brak treści debriefingu dla badania głównego |


- **Jak sprawdzić:** otwórz `experiment/P3_KLD.psyexp` w Builderze (plik znajduje się w roboczym repozytorium zespołu); każda routine z kolumny 3 istnieje we Flow, a parametry (np. `stim` → Stop: duration 4.0 s, `blank` → 1.0 s) są zgodne z tabelą.
- **Typowe problemy:** status „do dodania” oznacza element protokołu jeszcze niezaimplementowany (plan do M2), nie błąd.

## 14. Odstępstwa i pytania do LBK
W opisie pakietu P3 podano, że obraz jest wyświetlany przez **4000 ms**, a następnie szary ekran przez **1000 ms**; przewidziano oceny SAM i pomiar GSR/EDA. Warstwa adaptacyjna może wydłużać przerwę lub wprowadzać ekran neutralny, ale **nie może zmieniać czasu ekspozycji obrazu ani kolejności bodźców**. Poniższe kwestie wymagają uzgodnienia z LBK i nie zostały samodzielnie rozstrzygnięte. 

**Proponowane rozwiązania zespołu** to nasze warianty robocze do oceny przez prowadzącego, **nie oficjalne odpowiedzi LBK**. Nie wdrażamy zmian ingerujących w protokół bez zatwierdzenia. Każde pytanie pozostaje otwarte do czasu otrzymania decyzji.

### Pytanie 14.1 – Liczba prób i kontrbalansowanie
**Autorka pytania i dokumentacji:** DK · **Data:** 2026-10-12 · **Status:** otwarte
W opisie pojawiają się cztery obrazy, ale nie ma ostatecznej liczby prób. Ile powtórzeń należy zastosować i jak dokładnie ustalić kolejność?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Na potrzeby wersji demonstracyjnej pozostawiamy cztery obrazy A–D i kolejność z pliku `conditions/main.csv`. Dla pełnego badania przyjmujemy **30 prób wskazanych na slajdzie 6** jako wymaganie do doprecyzowania, a nie gotowy rozkład powtórzeń. Proponujemy przygotować osobne listy warunków dla uczestników i kontrbalansować kolejność za pomocą kwadratu łacińskiego. **Nie ustalamy liczby powtórzeń każdego obrazu przed odpowiedzią LBK** (szczegóły w 14.7 i 14.9).
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.2 – Powrót EDA do linii bazowej
**Opracowanie dokumentacji:** DK · **Analiza i przygotowanie pytania:** OS · **Data przydzielenia:** 2026-10-12 · **Status:** propozycja pytania, do sprawdzenia przez OS
Jak wyznaczać linię bazową EDA, jaki przyjąć próg powrotu do niej i maksymalny czas czekania przed kolejnym bodźcem?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W prototypie technicznym proponujemy linię bazową jako medianę EDA z **pierwszych 10 s poprawnych próbek**, wygładzanie EDA w oknie **2 s** i histerezę: wejście w podwyższone pobudzenie, gdy EDA przekracza bazę o `max(0,50 µS; 25% bazy)`, oraz powrót, gdy spadnie poniżej `baza + max(0,20 µS; 10% bazy)`. Neutralny ekran między próbami może trwać **maksymalnie 20 s**; po przekroczeniu limitu zapisujemy znacznik `timeout` i kontynuujemy. Są to parametry **testowe**, wynikające ze szkicu `state.py` i `adaptation.py`, a nie progi zatwierdzone do badań LBK.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.3 – Utrata śledzenia wzroku
**Autorka pytania i dokumentacji:** DK · **Data:** 2026-10-12 · **Status:** otwarte
Jaki czas utraty sygnału powinien wywoływać pauzę? Czy przerwę wolno wprowadzać wyłącznie między próbami, żeby zachować 4000 ms ekspozycji obrazu?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W testach przyjmujemy sygnał `gaze_lost` po **0,5 s** nieważnych próbek, a powrót `gaze_ok` po **1 s** prawidłowego śledzenia. Gdy utrata następuje w trakcie obrazu, **nie zatrzymujemy ani nie wydłużamy jego 4000 ms**; zapisujemy zdarzenie i ewentualną pauzę realizujemy dopiero przed kolejną próbą. Eksperymentator może wznowić przebieg w sytuacji awaryjnej, a przyczyna decyzji trafia do logu.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.4 – Aparatura i synchronizacja
**Opracowanie dokumentacji:** DK · **Analiza i przygotowanie pytania:** OS · **Data przydzielenia:** 2026-10-12 · **Status:** propozycja pytania, do sprawdzenia przez OS
Jakie są nazwy, typy, częstotliwości strumieni LSL dla EDA i EyeLogic na stanowisku LBK? Jakie są wymagania dotyczące kalibracji?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W domu korzystamy ze strumienia symulatora `LBK_Sim` (typ `Physio`, **4 Hz**) i z `LBK_Markers` dla znaczników zdarzeń. Podczas sesji w LBK sprawdzimy rzeczywiste nazwy, liczbę kanałów, typ, częstotliwość oraz znaczniki czasu EyeLogic i GSR/EDA; zapiszemy je w rozdziałach 1, 5 i 6. Wykonamy 9-punktową kalibrację oka, jeśli obsługuje ją użyty sterownik, i jednoczesny zapis strumieni do XDF. **Nazw i parametrów aparatury laboratoryjnej nie zakładamy z góry.**
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.5 – Wersja PsychoPy
**Autorka pytania i dokumentacji:** DK · **Data:** 2026-10-12 · **Status:** otwarte
Na Macu uruchomiono instalator 2025.2.4, a aplikacja pokazała oznaczenie 2025.2.4beta. Jaką dokładną wspólną wersję należy przyjąć dla zespołu i stanowiska LBK?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Na czas rozwoju projektu zapisujemy dokładną wersję uruchamianej aplikacji (obecnie pokazuje `2025.2.4beta`) oraz osobno wersję Pythona w jej środowisku. Proponujemy przetestować i przyjąć jedną stabilną wersję PsychoPy wspólną dla zespołu i stanowiska LBK przed M2, następnie utrwalić ją w `README` i Build Booku. Nie uznajemy numeru pliku instalatora za wystarczające potwierdzenie wersji programu.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.6 – Struktura par bodźców
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Protokół (sl. 8) mówi, że A/B i C/D są „identyczne strukturalnie (kompozycja, luminancja CIELAB), różnią się wyłącznie tonacją (kanał H w HSL)”. Dostarczone obrazy to różne sceny (A: jesień z drzewem i płotem, B: zima ze świerkami) i **różne osoby (C: kobieta, D: mężczyzna)**; średnia jasność L* różni się: A 29,2 vs B 24,9, C 47,2 vs D 42,5 (policzone na oryginałach ze slajdów 9–12). Płeć twarzy jest więc pomieszana z tonacją. Czy to ostateczne bodźce, czy LBK dostarczy pary z jedną kompozycją przebarwioną w kanale H?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Do czasu decyzji LBK zachowujemy **oryginalne dostarczone obrazy A–D**, oznaczając je jako materiał do demonstracji, a nie potwierdzone pary różniące się wyłącznie barwą. Przed badaniem właściwym proponujemy przygotować lub otrzymać od LBK pary z **tą samą kompozycją i osobą**, różniące się kontrolowaną tonacją; porównać luminancję i sposób wyświetlania. Samodzielne podmienienie obrazów zmieniłoby bodźce i wymaga zatwierdzenia przez LBK.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.7 – Liczba prób i czas sesji
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
„30 prób × 4 s + 1 s ISI” przy 4 bodźcach (+4 achromatycznych) – ile powtórzeń każdego bodźca, w jakim układzie, co jest w 15. i 16. próbie (pauza) i jak długa ma być pauza? Czym wypełnione jest pozostałe ~30 min z deklarowanych ~35 min?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Przyjmujemy, że **30 prób** z protokołu jest celem wersji M2/M3; cztery próby w `main.csv` i dwanaście w `test_mix.csv` pozostają **wyłącznie testami technicznymi**. Przygotujemy listę z identyfikatorem obrazu, warunkiem, numerem próby i miejscem pauzy po 15. próbie. Liczby powtórzeń, włączenie achromatów, długość przerwy oraz czynności składające się na około 35 minut muszą zostać podane przez LBK; do tego czasu nie deklarujemy, że demonstracja odtwarza pełny protokół.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.8 – Warunek achromatyczny
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Ile prób achromatycznych, przemieszane z barwnymi czy w osobnym bloku, przed czy po? Kto generuje wersje (skrypt zespołu – jaką metodą: luminancja Rec.709 czy L* CIELAB)?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Proponujemy przygotować kontrolne kopie obrazów w skali szarości **w osobnych plikach**, pozostawiając barwne oryginały bez zmian. Każdą wersję oznaczymy kolumnami `stim_id` i `warunek` w pliku CSV oraz sprawdzimy jednakowe rozmiary i poprawne przypisanie. Wybór metody konwersji i sposobu wplecenia achromatów (blok czy losowanie między próbami) pozostaje do zatwierdzenia przez LBK, ponieważ wpływa na porównanie warunków.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.9 – Kwadraty łacińskie
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Kwadrat 4×4 dla 4 bodźców, czy dla 8 (z achromatycznymi)? Jak przypisywać listy do uczestników (kolejność zgłoszeń, losowanie, w obrębie podgrup)?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Dla **czterech barwnych bodźców A–D** proponujemy cztery listy z kolejnością z kwadratu łacińskiego `ABCD / BCDA / CDAB / DABC` jako **wstępny przykład techniczny**, nie ostateczny plan 30 prób. Każdy uczestnik otrzymałby listę według ustalonej rotacji w obrębie grupy, a numer listy zapisujemy w CSV. Jeśli obowiązuje osiem obrazów z achromatami, trzeba zaprojektować nowe kontrbalansowanie i potwierdzić je z LBK.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.10 – Kalibracja i walidacja
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Protokół podaje kalibrację 9-punktową, ale bez kryterium walidacji (badanie 2 ma < 0,5°). Jaki próg błędu walidacji akceptujemy dla EyeLogic i ile prób rekalibracji?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Proponujemy wykonać **kalibrację 9-punktową** i po niej osobną walidację, zapisując błąd, wynik `akceptacja/ponowna kalibracja` oraz liczbę podejść. Progu **0,5°** z opisu innego badania nie przenosimy automatycznie na EyeLogic; ostateczne kryterium i dopuszczalną liczbę powtórzeń uzgodnimy na stanowisku LBK. MouseGaze traktujemy jedynie jako symulację do testów interfejsu.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.11 – Screening
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Test Ishihary i CSS-15 – na papierze przed sesją, w osobnym narzędziu, czy w eksperymencie PsychoPy? Kto decyduje o wykluczeniu przy wyniku pozytywnym?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Proponujemy przeprowadzać test Ishihary i kwestionariusz CSS-15 **przed właściwą sesją** w osobnym kroku screeningu, bez wpisywania danych osobowych w wyniki PsychoPy. Do eksperymentu trafiałby wyłącznie pseudonim i dopuszczona grupa uczestnika. Zasady kwalifikacji i wykluczenia, interpretację wyników oraz osobę podejmującą decyzję musi określić LBK; nie tworzymy własnych kryteriów medycznych.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.12 – Moment i forma SAM
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
SAM „po każdym bloku bodźców” (sl. 6) czy po każdym obrazie (sl. 13: „reakcja na obraz”)? Czym jest „blok” w badaniu bez bloków? Piktogramy SAM (manekiny) czy skala z opisami słownymi?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Jako rozwiązanie techniczne przewidujemy w PsychoPy **trzy skale SAM 1–9** (walencja, pobudzenie, dominacja) i zapis odpowiedzi z czasem reakcji. W obecnym prototypie ekran `sam` występuje **po pojedynczym obrazie**, jednak przed zamknięciem M2 należy ustalić, czy w badaniu właściwym ma być **po każdym bloku**. Proponujemy użyć oryginalnych piktogramów SAM, o ile LBK ma do nich odpowiednie materiały i prawa; do tego czasu skale opisowe są rozwiązaniem demonstracyjnym.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.13 – Ankieta post-experimentum (bloki B–D)
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Po każdym obrazie czy raz po sesji? Pozycje odnoszą się do „tego obrazu” – którego, jeśli raz na końcu? Format odpowiedzi w bloku D (skala czy pytanie otwarte)?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Proponujemy potraktować bloki **B–D** jako oddzielną ankietę końcową, ponieważ protokół nazywa ją *post-experimentum*. Pytania odwołujące się do „tego obrazu” powinny jednak wskazywać konkretny `stim_id` (np. miniatura i identyfikator) albo zostać odpowiednio przeredagowane **po zgodzie LBK**. W bloku B użyjemy skali 1–7, w C pól tekstowych; w D format pozostawiamy do rozstrzygnięcia. Nie zmieniamy treści pytań samodzielnie.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.14 – Dot-probe
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Wymieniony jako miara dodatkowa bez opisu procedury (bodźce, czasy, położenie sondy, liczba prób). Czy jest częścią tego badania i kto dostarczy procedurę?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Nie dodajemy `dot-probe` do głównego przebiegu bez kompletnej procedury, ponieważ mogłoby to zmienić uwagę i pobudzenie uczestnika, a więc zakłócić badanie. Przygotujemy miejsce na osobną routine dopiero po otrzymaniu od LBK materiałów, czasu prezentacji, mapy klawiszy i liczby prób. Na etapie M1 oznaczamy tę miarę jako **niezaimplementowaną / wymaga decyzji**.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.15 – Szary ekran ISI
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Jaki kolor/luminancja szarego ekranu (np. średnia luminancja bodźców)? Czy przed bodźcem ma być punkt fiksacji (ważne dla miary kolejności pierwszej fiksacji – start wzroku z różnych miejsc)?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W wersji demonstracyjnej pozostawiamy **szary ekran 1000 ms** (`rgb [0,0,0]` w PsychoPy) i stałe ustawienia wyświetlacza. Proponujemy, by LBK podało dokładną wartość szarości lub luminancji oraz zdecydowało, czy punkt fiksacji jest częścią protokołu. **Nie wprowadzamy punktu fiksacji na własną rękę**, ponieważ zmienia pozycję początkową wzroku i może wpłynąć na wskaźniki AOI.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.16 – Sprzęt
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Protokół zaleca Tobii Pro Fusion / EyeLink 1000 Plus (≥ 120 Hz) i Shimmer3 GSR+. W LBK są EyeLogic i urządzenie GSR LBK – jaka częstotliwość próbkowania i dokładność, czy to akceptowalne odstępstwo?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Wersję lokalną testujemy na MouseGaze i symulatorze. W LBK użyjemy **EyeLogic i dostępnego czujnika GSR/EDA**, jeśli prowadzący zatwierdzi odstępstwo od aparatury wymienionej w prezentacji. Przed integracją zbierzemy parametry: częstotliwość próbkowania, deklarowaną dokładność wzroku, format strumienia LSL i synchronizację czasową. Różnice między sprzętem protokołu a wyposażeniem LBK opisujemy jawnie w Build Booku.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.17 – Treść instrukcji i debriefingu
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Protokół nie podaje tekstu instrukcji ani debriefingu dla badania głównego. Czy używamy własnych (do zatwierdzenia)?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Przygotujemy krótką neutralną instrukcję: uczestnik ogląda obraz swobodnie, nie musi szukać określonych elementów i odpowiada na pytania zgodnie z własnym odczuciem. Debriefing poda cel ogólny, sposób wykorzystania danych i kontakt do LBK, bez ujawniania hipotezy przed sesją. Ostateczną treść obu ekranów prześlemy do **zatwierdzenia przez LBK** przed sesją z uczestnikami.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.18 – Zgoda
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Załącznik B (formularz zgody) dotyczy Badania 9. Czy jest formularz zgody dla badania głównego (QBS01), czy przygotowujemy go na wzór Zał. B?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Przygotujemy **oddzielny formularz zgody dla QBS01** z zakresem danych (wzrok, EDA i odpowiedzi), celem, zasadą dobrowolności, możliwością wycofania oraz miejscem i okresem przechowywania. Ekran w PsychoPy powinien umożliwić odmowę, która kończy sesję bez pomiaru. Formularza dotyczącego Badania 9 nie będziemy przedstawiać jako zgody na QBS01; ostateczny wzór i procedurę ochrony danych zatwierdzi LBK.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.19 – AOI
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
AOI-1…AOI-4 opisane słownie (sl. 8) bez współrzędnych. Czy LBK dostarczy współrzędne (w pikselach bodźca 1536×1024 / 1400×1122), czy wyznaczamy je sami?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Proponujemy przygotować definicje **AOI-1…AOI-4 osobno dla każdego obrazu** na podstawie zatwierdzonych plików źródłowych, w układzie współrzędnych obrazu. W analizie przeliczymy je na współrzędne ekranu z uwzględnieniem skalowania i szarych pasów, a definicje zapiszemy do plików pomocniczych. Granice AOI i zasadę zaliczania fiksacji powinien potwierdzić LBK przed analizą wyników.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.20 – Wielkość bodźca na ekranie
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Bodźce mają różne proporcje (3:2 pejzaże, ok. 5:4 twarze). Pokazujemy je w maksymalnej wysokości 1080 px z szarymi pasami (stan obecny), czy w stałym rozmiarze/kącie widzenia?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W prototypie wyświetlamy obrazy **bez rozciągania**, centralnie i z zachowaniem proporcji; wolne miejsce wypełnia szare tło. Dokumentujemy rozmiar prezentacji, jednostki PsychoPy `height`, rozdzielczość oraz odległość uczestnika. Przed badaniem LBK musi zatwierdzić, czy ważniejsza jest stała wysokość w pikselach, czy stały kąt widzenia — nie możemy samodzielnie zmienić wielkości bodźca między warunkami.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.21 – Analiza H4
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
„Test t-Studenta dla prób niezależnych” przy projekcie wewnątrzgrupowym – które grupy porównujemy (podgrupy ekspertyzy?). Wpływa to na to, jakie zmienne musi zapisać eksperyment.

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** W CSV zachowamy dla **każdej próby** kod uczestnika, grupę, `stim_id`, wariant barwny/achromatyczny, kolejność, trzy odpowiedzi SAM i czasy reakcji, aby później dobrać poprawną metodę analizy. Jeśli porównywane są **te same osoby w różnych warunkach**, proponujemy analizę dla pomiarów zależnych lub model z powtarzanymi pomiarami; test dla prób niezależnych byłby odpowiedni tylko przy porównaniu niezależnych grup. Wybór testu i hipotezy H4 uzgadniamy z LBK, bez samodzielnej zmiany planu statystycznego.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.

### Pytanie 14.22 – Wersja protokołu
**Opracowanie dokumentacji:** DK · **Analiza i autor pytania:** OS · **Data:** 2026-11-23 · **Status:** otwarte
Prezentacja ma oznaczenie „2025”, plakat „2026”, kod QBS01. Który plik i data są wersją obowiązującą?

**Proponowane rozwiązanie zespołu (do zatwierdzenia przez LBK):** Do prac M1 przyjmujemy roboczo **prezentację `Badania_EyeTracking.pptx` (oznaczenie 2025)** jako źródło szczegółów procedury, a plakat z 2026 r. jedynie jako materiał informacyjny. Prosimy LBK o wskazanie obowiązującej wersji, jej daty i plików bodźców; po potwierdzeniu wpiszemy identyfikator wersji do `BUILD_BOOK.md`, plików warunków i dziennika zmian. Do tego czasu status protokołu pozostaje **niepotwierdzony**.
**Odpowiedź LBK:** oczekuje na odpowiedź prowadzącego.
**Status rozstrzygnięcia:** otwarte – do potwierdzenia przez LBK.
