# Co znaczą cechy

Słownik kolumn z surowego pliku `Speed Dating Data.csv` (jeden wiersz = jedna osoba na jednym spotkaniu).

W CSV prawie zawsze są **liczby**, nie zdania. Liczba to odpowiedź na pytanie z ankiety albo kod z legendy. Ten plik mówi, **co ta liczba znaczy** i **jaki ma zakres**.

Po przygotowaniu danych (`meetings.csv`) te same cechy mają końcówki `_woman` / `_man` (np. `age_woman`). Sens i zakres zostają takie same.

Etykieta w surowym pliku: `dec` (0/1 — czy ta osoba chce kolejnego spotkania).  
Etykieta po merge: `outcome` (1–4 — decyzje obu stron razem). Żadna z nich nie jest „cechą wejściową” do modelu.

---

## Ważne skróty w nazwach

| element | znaczenie |
| ------- | --------- |
| `o` na końcu / w środku (`age_o`, `pf_o_att`) | partner (other) na tym spotkaniu |
| końcówka `_1` | ankieta **rejestracyjna przed** wieczorem |
| `attr`, `sinc`, `intel`, `fun`, `amb`, `shar` | atrakcyjność, szczerość, inteligencja, humor, ambicja, wspólne zainteresowania |

---

## Jak czytać bloki preferencji (`attr1_1`, `attr2_1`, …)

To **nie** są oceny partnera po rozmowie. To odpowiedzi z rejestracji.

Cyfra w środku nazwy = **o czyje zdanie chodzi**:

| wzór | pytanie w ankiecie |
| ---- | ------------------ |
| `…1_1` | czego **sam** szukam u partnera |
| `…2_1` | czego według mnie szuka **płeć przeciwna** |
| `…3_1` | jak oceniam **siebie** |
| `…4_1` | czego według mnie szukają osoby **mojej płci** |
| `…5_1` | jak myślę, że **widzą mnie inni** |

**Zakres w CSV:**

| blok | co jest w komórce | zakres w pliku | uwagi |
| ---- | ----------------- | -------------- | ----- |
| `1_1`, `2_1`, `4_1` | punkty przyznane danej cesze | zwykle 0–100; suma sześciu cech ≈ 100 | fale 6–9 były pytane 1–10, w pliku już przeliczone na ~100 |
| `3_1`, `5_1` | ocena na skali | 1–10 (w danych bywa od 2) | w samoocenie **nie ma** `shar3_1` / `shar5_1` |

Przykład: `attr1_1 = 25` oznacza „z 100 punktów na cechy partnera dałam 25 na atrakcyjność”, a nie tekstową odpowiedź.

---

## Przebieg wieczoru

| kolumna | co znaczy | typ / zakres w danych |
| ------- | --------- | --------------------- |
| `condtn` | wariant wydarzenia | kod **1** = mały wybór partnerów, **2** = duży wybór |
| `round` | ile osób ta osoba spotkała na swojej fali | liczba całkowita **5–22** |
| `position` | numer stanowiska tej rozmowy | **1–22** |
| `positin1` | stanowisko startowe wieczoru (literówka w nazwie) | **1–22**, bywa NaN |
| `order` | która z kolei randka tego wieczoru | **1–22** (1 = pierwsza) |

---

## Partner (znany z ankiety przed spotkaniem)

| kolumna | co znaczy | typ / zakres w danych |
| ------- | --------- | --------------------- |
| `int_corr` | korelacja wektorów zainteresowań tej osoby i partnera (policzona przez autorów zbioru, nie przy merge) | liczba rzeczywista ok. **−0.83 … 0.91** (teoretycznie −1…1) |
| `samerace` | czy ta sama rasa / pochodzenie | **0** = różne, **1** = ta sama |
| `age_o` | wiek partnera | **18–55** |
| `race_o` | rasa partnera | kod **1–6**, legenda jak `race` |
| `pf_o_att` | ile punktów partner dał atrakcyjności w swoim `attr1_1` | punkty, suma preferencji partnera ≈ 100 |
| `pf_o_sin` | to samo dla szczerości | j.w. |
| `pf_o_int` | inteligencja | j.w. |
| `pf_o_fun` | poczucie humoru | j.w. |
| `pf_o_amb` | ambicja | j.w. |
| `pf_o_sha` | wspólne zainteresowania | j.w. |

`pf` = preference partnera z jego rejestracji (to samo co blok `1_1` u partnera).

---

## Profil uczestnika

| kolumna | co znaczy | typ / zakres w danych |
| ------- | --------- | --------------------- |
| `gender` | płeć | **0** = kobieta, **1** = mężczyzna |
| `age` | wiek | **18–55** |
| `field` | kierunek studiów | **tekst** (po czyszczeniu ujednolicony) |
| `field_cd` | ten sam kierunek jako kod | kod całkowity **1–18** (legenda niżej) |
| `undergra` | uczelnia licencjacka | **tekst** |
| `mn_sat` | mediana wyniku SAT **tej uczelni** (nie wynik tej osoby) | ok. **914–1490**; w surowym CSV bywa z przecinkiem jako tekst |
| `tuition` | czesne **tej uczelni** (nie „ile ja płaciłem”) | ok. **2406–34300**; j.w. |
| `race` | rasa / pochodzenie | kod **1–6** |
| `imprace` | jak ważne, by partner był tej samej rasy | skala **0–10** (w danych bywa 0) |
| `imprelig` | jak ważne, by partner był tego samego wyznania | skala **1–10** |
| `from` | skąd pochodzi | **tekst** |
| `zipcode` | kod pocztowy miejsca, w którym dorastała | tekst/liczba; to kod, nie wielkość do logu |
| `income` | mediana dochodu gospodarstw w tym ZIP (nie pensja osoby) | ok. **8607–109031** USD |
| `goal` | po co przyszła na speed dating | kod **1–6** |
| `date` | jak często chodzi na randki | kod **1–7**; **to nie jest data kalendarzowa** |
| `go_out` | jak często wychodzi towarzysko | kod **1–7** |
| `career` | planowany zawód | **tekst** |
| `career_c` | planowany zawód jako kod | kod **1–17** |
| `exphappy` | jak bardzo liczy na udany wieczór | skala **1–10** |
| `expnum` | ilu z ~20 partnerów według niej powie „tak” | **0–20**; dużo braków (NaN) |

### Legendy kodów

**`field_cd`:**  
1 prawo, 2 matematyka, 3 nauki społeczne / psychologia, 4 medycyna / biotechnologia, 5 inżynieria, 6 anglistyka / pisanie / dziennikarstwo, 7 historia / religia / filozofia, 8 biznes / ekonomia / finanse, 9 edukacja, 10 biologia / chemia / fizyka, 11 praca socjalna, 12 studia licencjackie / brak decyzji, 13 politologia / stosunki międzynarodowe, 14 film, 15 sztuka, 16 języki, 17 architektura, 18 inne.

**`race` / `race_o`:**  
1 czarnoskóry / Afroamerykanin, 2 biały / Europejczyk, 3 latynoski, 4 azjatycki / wyspy Pacyfiku, 5 rdzenny Amerykanin, 6 inne.

**`goal`:**  
1 fajny wieczór, 2 poznać nowych ludzi, 3 zdobyć randkę, 4 poważny związek, 5 żeby móc powiedzieć, że byłem, 6 inne.

**`date` i `go_out`:**  
1 kilka razy w tygodniu, 2 dwa razy w tygodniu, 3 raz w tygodniu, 4 dwa razy w miesiącu, 5 raz w miesiącu, 6 kilka razy w roku, 7 prawie nigdy.

**`career_c`:**  
1 prawnik, 2 nauka / badania, 3 psycholog, 4 lekarz, 5 inżynier, 6 sztuka / rozrywka, 7 bankowość / konsulting / biznes, 8 nieruchomości, 9 sprawy międzynarodowe / pomoc humanitarna, 10 brak decyzji, 11 praca socjalna, 12 logopedia, 13 polityka, 14 sport, 15 inne, 16 dziennikarstwo, 17 architektura.

---

## Zainteresowania

Każda kolumna = „jak bardzo lubię X”.

| kolumna | znaczenie | zakres |
| ------- | --------- | ------ |
| `sports` | uprawianie sportu | **1–10** |
| `tvsports` | oglądanie sportu | **1–10** |
| `exercise` | ćwiczenia, siłownia | **1–10** |
| `dining` | jedzenie na mieście | **1–10** |
| `museums` | muzea, galerie | **1–10** |
| `art` | sztuka | **1–10** |
| `hiking` | wędrówki, biwak | **1–10** |
| `gaming` | gry | **1–10** |
| `clubbing` | taniec, kluby | **1–10** |
| `reading` | czytanie | **1–10** |
| `tv` | telewizja | **1–10** |
| `theater` | teatr | **1–10** |
| `movies` | filmy | **1–10** |
| `concerts` | koncerty | **1–10** |
| `music` | muzyka | **1–10** |
| `shopping` | zakupy | **1–10** |
| `yoga` | joga, medytacja | **1–10** |

Z tych ocen autorzy zbioru liczą `int_corr` dla każdej pary. Same oceny zostają w tabeli jako cechy osoby.

---

## Preferencje i samoocena z rejestracji (pełna lista)

### Blok 1 — czego szukam u partnera (punkty, suma ≈ 100)

| kolumna | co jest w komórce | zakres typowy |
| ------- | ----------------- | ------------- |
| `attr1_1` | punkty na atrakcyjność | 0–100 |
| `sinc1_1` | punkty na szczerość | 0–60 (w danych) |
| `intel1_1` | punkty na inteligencję | 0–50 |
| `fun1_1` | punkty na humor | 0–50 |
| `amb1_1` | punkty na ambicję | 0–53 |
| `shar1_1` | punkty na wspólne zainteresowania | 0–30 |

### Blok 2 — czego według mnie szuka płeć przeciwna (punkty, suma ≈ 100)

| kolumna | znaczenie | zakres typowy |
| ------- | --------- | ------------- |
| `attr2_1` … `shar2_1` | jak wyżej, ale „według mnie oni/one tak punktują” | 0–100 (attr), pozostałe zwykle ≤ 50 |

### Blok 4 — czego według mnie szuka moja płeć (punkty, suma ≈ 100)

| kolumna | znaczenie | zakres typowy |
| ------- | --------- | ------------- |
| `attr4_1` … `shar4_1` | jak wyżej dla własnej płci | zwykle 0–95; więcej braków niż w bloku 1 |

### Blok 3 — samoocena (skala 1–10, bez `shar`)

| kolumna | znaczenie | zakres w danych |
| ------- | --------- | --------------- |
| `attr3_1` | jak atrakcyjna/y jestem | 2–10 |
| `sinc3_1` | jak szczera/y | 2–10 |
| `intel3_1` | jak inteligentna/y | 3–10 |
| `fun3_1` | jak zabawna/y | 2–10 |
| `amb3_1` | jak ambitna/y | 2–10 |

### Blok 5 — jak myślę, że widzą mnie inni (skala 1–10, bez `shar`)

| kolumna | znaczenie | zakres w danych |
| ------- | --------- | --------------- |
| `attr5_1` | jak atrakcyjnego widzą mnie inni | 2–10 |
| `sinc5_1` | jak szczerego | 1–10 |
| `intel5_1` | jak inteligentnego | 3–10 |
| `fun5_1` | jak zabawnego | 2–10 |
| `amb5_1` | jak ambitnego | 1–10 |

---

## Czego tu nie ma (świadomie)

Oceny z karty po rozmowie (`attr`, `like`, `dec` jako cecha, `match`…) oraz ankiety `_s` / `_2` / `_3` nie są na liście cech wejściowych: powstają wraz z decyzją albo później i wyciekają do etykiety.
