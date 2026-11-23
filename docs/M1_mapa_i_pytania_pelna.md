# M1 – materiał do karty projektu (szkic techniczny)

Szkic przygotowany 2026-11-23 na podstawie materiałów pakietu P3. Do przeniesienia do karty projektu i do BUILD_BOOK.md (rozdz. 2 i 14) – z inicjałami autorów i datą przy każdym kroku. Statusy dotyczą stanu eksperymentu `experiment/P3_KLD.psyexp` w tym repozytorium.

## 0. Źródła protokołu (wersja)

| Plik | Co zawiera | Data / wersja |
|---|---|---|
| `Badania_EyeTracking.pptx` | protokół badania głównego: slajdy 3–14 (hipotezy, projekt, grupa, bodźce A–D, ankieta, analiza) i 22 (sprzęt); slajdy 15–21 – badanie drugie | slajd 1: „PROJEKT BADAWCZY · 2025”, brak daty pliku w treści |
| `Badanie_Eyetracking_Qualia_Barwa_i_Subiektywne_Doswiadczenie_2026.jpeg` | plakat rekrutacyjny, kod badania **QBS01**, ok. 35 min, kryteria | 2026 |
| `Bodziec A.PNG` … `Bodziec D.PNG` | podgląd bodźców (ok. 715×476 / 594×476 px) | – |
| `Zalacznik_A/B/D_*.docx`, `Badanie9_*` | dotyczą **badania drugiego** (Badanie 9 – reklama AI/człowiek), nie badania głównego | – |

Bodźce w eksperymencie wzięto z oryginałów w prezentacji (slajdy 9–12, 1536×1024 i ok. 1400×1122 px), bo pliki `Bodziec *.PNG` mają niską rozdzielczość.

## 1. Mapa protokół → PsychoPy (rozdz. 2 Build Booka)

| # | Element protokołu (źródło) | Routine / komponent | Parametry | Status |
|---|---|---|---|---|
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

## 2. Pytania do LBK (rozdz. 14 Build Booka; 14.1–14.5 są już z KL-A)

- **14.6 Struktura par bodźców.** Protokół (sl. 8) mówi, że A/B i C/D są „identyczne strukturalnie (kompozycja, luminancja CIELAB), różnią się wyłącznie tonacją (kanał H w HSL)”. Dostarczone obrazy to różne sceny (A: jesień z drzewem i płotem, B: zima ze świerkami) i **różne osoby (C: kobieta, D: mężczyzna)**; średnia jasność L* różni się: A 29,2 vs B 24,9, C 47,2 vs D 42,5 (policzone na oryginałach ze slajdów 9–12). Płeć twarzy jest więc pomieszana z tonacją. Czy to ostateczne bodźce, czy LBK dostarczy pary z jedną kompozycją przebarwioną w kanale H?
- **14.7 Liczba prób i czas sesji.** „30 prób × 4 s + 1 s ISI” przy 4 bodźcach (+4 achromatycznych) – ile powtórzeń każdego bodźca, w jakim układzie, co jest w 15. i 16. próbie (pauza) i jak długa ma być pauza? Czym wypełnione jest pozostałe ~30 min z deklarowanych ~35 min?
- **14.8 Warunek achromatyczny.** Ile prób achromatycznych, przemieszane z barwnymi czy w osobnym bloku, przed czy po? Kto generuje wersje (skrypt zespołu – jaką metodą: luminancja Rec.709 czy L* CIELAB)?
- **14.9 Kwadraty łacińskie.** Kwadrat 4×4 dla 4 bodźców, czy dla 8 (z achromatycznymi)? Jak przypisywać listy do uczestników (kolejność zgłoszeń, losowanie, w obrębie podgrup)?
- **14.10 Kalibracja i walidacja.** Protokół podaje kalibrację 9-punktową, ale bez kryterium walidacji (badanie 2 ma < 0,5°). Jaki próg błędu walidacji akceptujemy dla EyeLogic i ile prób rekalibracji?
- **14.11 Screening.** Test Ishihary i CSS-15 – na papierze przed sesją, w osobnym narzędziu, czy w eksperymencie PsychoPy? Kto decyduje o wykluczeniu przy wyniku pozytywnym?
- **14.12 Moment i forma SAM.** SAM „po każdym bloku bodźców” (sl. 6) czy po każdym obrazie (sl. 13: „reakcja na obraz”)? Czym jest „blok” w badaniu bez bloków? Piktogramy SAM (manekiny) czy skala z opisami słownymi?
- **14.13 Ankieta post-experimentum (bloki B–D).** Po każdym obrazie czy raz po sesji? Pozycje odnoszą się do „tego obrazu” – którego, jeśli raz na końcu? Format odpowiedzi w bloku D (skala czy pytanie otwarte)?
- **14.14 Dot-probe.** Wymieniony jako miara dodatkowa bez opisu procedury (bodźce, czasy, położenie sondy, liczba prób). Czy jest częścią tego badania i kto dostarczy procedurę?
- **14.15 Szary ekran ISI.** Jaki kolor/luminancja szarego ekranu (np. średnia luminancja bodźców)? Czy przed bodźcem ma być punkt fiksacji (ważne dla miary kolejności pierwszej fiksacji – start wzroku z różnych miejsc)?
- **14.16 Sprzęt.** Protokół zaleca Tobii Pro Fusion / EyeLink 1000 Plus (≥ 120 Hz) i Shimmer3 GSR+. W LBK są EyeLogic i urządzenie GSR LBK – jaka częstotliwość próbkowania i dokładność, czy to akceptowalne odstępstwo?
- **14.17 Treść instrukcji i debriefingu.** Protokół nie podaje tekstu instrukcji ani debriefingu dla badania głównego. Czy używamy własnych (do zatwierdzenia)?
- **14.18 Zgoda.** Załącznik B (formularz zgody) dotyczy Badania 9. Czy jest formularz zgody dla badania głównego (QBS01), czy przygotowujemy go na wzór Zał. B?
- **14.19 AOI.** AOI-1…AOI-4 opisane słownie (sl. 8) bez współrzędnych. Czy LBK dostarczy współrzędne (w pikselach bodźca 1536×1024 / 1400×1122), czy wyznaczamy je sami?
- **14.20 Wielkość bodźca na ekranie.** Bodźce mają różne proporcje (3:2 pejzaże, ok. 5:4 twarze). Pokazujemy je w maksymalnej wysokości 1080 px z szarymi pasami (stan obecny), czy w stałym rozmiarze/kącie widzenia?
- **14.21 Analiza H4.** „Test t-Studenta dla prób niezależnych” przy projekcie wewnątrzgrupowym – które grupy porównujemy (podgrupy ekspertyzy?). Wpływa to na to, jakie zmienne musi zapisać eksperyment.
- **14.22 Wersja protokołu.** Prezentacja ma oznaczenie „2025”, plakat „2026”, kod QBS01. Który plik i data są wersją obowiązującą?

## 3. Mierzalne kryteria odbioru – propozycja

| # | Kryterium | Próg | Jak mierzymy | Stan na 2026-11-23 |
|---|---|---|---|---|
| K1 | Czas ekspozycji bodźca | 4000 ms ± 1 klatka (± 16,7 ms przy 60 Hz) w 100 % prób | różnica `stim:offset` − `stim:onset` (znaczniki wysyłane na odświeżeniu ekranu) w CSV/XDF | 3992–4019 ms na laptopie ~45 kl./s (± 1 klatka ≈ 22 ms) – do powtórzenia w LBK |
| K2 | Reakcja na utratę sygnału EDA | stan `unknown` i komunikat R3 ≤ 2,5 s od ostatniej dobrej próbki | test `sim_to_lsl.py --blackout` → znacznik `state:physio_unknown` vs początek przerwy w XDF | działa (próg w kodzie 2 s) |
| K3 | Reakcja na utratę śledzenia wzroku | znacznik `state:gaze_lost` ≤ 0,6 s od początku utraty | MouseGaze (przytrzymanie przycisku) / zasłonięcie oczu w LBK | działa (próg 0,5 s) |
| K4 | Wyłącznik adaptacji | przy `adaptacja = nie`: 0 znaczników `adaptation:`/`state:`, przerwa przed obrazem ≤ 1 klatka | CSV (`adapt_gate_s`) + `_markers.csv` | spełnione (test `killswitch_test`) |
| K5 | Kompletność danych | 100 % prób ma `stim:onset`, `stim:offset` i 3 oceny SAM; XDF zawiera oba strumienie | skrypt sprawdzający CSV + XDF | spełnione w teście mix |
| K6 | Uruchomienie według Build Booka | osoba spoza zespołu uruchamia sesję (MouseGaze + symulator + LabRecorder) od czystego Windows w ≤ 45 min bez pytania autorów | protokół testu odtworzenia (KL-E) | do zmierzenia |

## 4. Co eksperyment zapisuje (stan obecny)

- **CSV PsychoPy** `data/P3_main_<kod>_<sesja>_<RRRR-MM-DD_GGMM>.csv` – jeden wiersz na próbę: `stim_id, image, kategoria, tonacja`, oceny `sam_val/aro/dom.response` i `.rt`, czasy routine, kolumny adaptacji (`adaptacja, adapt_enabled, adapt_rules, adapt_n, adapt_reason, adapt_gate_s, state_physio, state_gaze, eda_gate_us, eda_base_us, tracking_loss_stim`). Uwaga: wzorzec LBK to `{pakiet}_{badanie}_{kod}_{sesja}_{data}` – obecnie `P3_main_…`; ewentualnie zmienić na `P3_QBS01_…` (do decyzji).
- **`<plik>_markers.csv`** – kopia znaczników (t_lsl, marker).
- **LSL `LBK_Markers`** (Markers, 1 kanał, string, nieregularny): `exp:start|study=P3_main|participant=…|session=…|adaptation=…`, `trial:start`, `stim:onset|stim=A|trial=…`, `stim:offset`, `resp|q=SAM_valence|val=…|rt=…`, `state:…`, `adaptation:<reguła>|rule=R1|phase=start|…`, `artifact:tracking_loss`, `exp:end`.
- **LSL `LBK_Sim`** (lokalnie; Physio, 5 kanałów: hr, eda_us, rr_ms, focus, quality; 4 Hz) – w LBK zastąpiony strumieniem urządzenia GSR.
- **XDF** z LabRecorder (oba strumienie) – `sample_data/…_mix.xdf`.
- **hdf5 ioHub** z danymi wzroku – obecnie wyłączony zapis do pliku (do włączenia w M2/M3 dla EyeLogic).

## 5. Ryzyka dla trafności badania (do sekcji ryzyk)

- Pary bodźców różnią się nie tylko tonacją (14.6) – efekt „barwy” może być efektem sceny/płci/jasności; adaptacja tego nie rozwiąże, potrzebna decyzja LBK.
- Adaptacja R1 wydłuża przerwę przed bodźcem przy wysokim EDA – to zmienia **rozkład odstępów między bodźcami**, co może wpływać na pobudzenie przy kolejnym obrazie. Zabezpieczenie: limit 20 s, zapis `adapt_gate_s` w każdej próbie (można kontrolować w analizie), wyłącznik; adaptacja nie dotyka ekspozycji 4000 ms ani kolejności.
- R2/R4 pokazują tekst między próbami (komunikat) – może przerywać „naiwność” uczestnika; teksty neutralne, bez informacji o hipotezach.
- Brak punktu fiksacji przed bodźcem (14.15) – start wzroku zależy od miejsca po SAM, co zaburza miarę kolejności pierwszej fiksacji.
- Ocena SAM po każdym obrazie (zamiast po bloku) może zmieniać sposób oglądania kolejnych obrazów (uczestnik „ogląda pod ocenę”).
