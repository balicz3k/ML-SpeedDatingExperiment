# Co znaczą cechy

80 kolumn używanych jako cechy. Zmienna zależna `dec` (czy osoba chce kolejnego spotkania) nie jest na tej liście.

Litera `o` w nazwie oznacza partnera (other), na przykład `age_o` to wiek partnera.

Końcówka `_1` oznacza ankietę rejestracyjną, sprzed wieczoru speed-datingu.

## Jak czytać preferencje

Sześć cech partnera:


| skrót | znaczenie                  |
| ----- | -------------------------- |
| attr  | atrakcyjność               |
| sinc  | szczerość                  |
| intel | inteligencja               |
| fun   | poczucie humoru, „fajność” |
| amb   | ambicja                    |
| shar  | wspólne zainteresowania    |


Cyfra w środku nazwy mówi, o czyje zdanie chodzi:


| wzór      | pytanie                                    |
| --------- | ------------------------------------------ |
| `attr1_1` | czego sam szukam u partnera                |
| `attr2_1` | czego według mnie szuka płeć przeciwna     |
| `attr3_1` | jak oceniam siebie                         |
| `attr4_1` | czego według mnie szukają osoby mojej płci |
| `attr5_1` | jak myślę, że widzą mnie inni              |


`attr1_1` … `shar1_1` oraz bloki `2` i `4`: w większości fal rozdział 100 punktów. W falach 6–9 pytanie było w skali 1–10, a w pliku te odpowiedzi są już przeliczone na sumę 100.

`attr3_1` … `amb3_1` i `attr5_1` … `amb5_1`: skala 1–10. W samoocenie nie ma „wspólnych zainteresowań”.

## Przebieg wieczoru


| kolumna  | znaczenie                                                                                |
| -------- | ---------------------------------------------------------------------------------------- |
| condtn   | wariant wydarzenia: 1 = mały wybór partnerów, 2 = duży wybór                             |
| round    | ile osób ta osoba spotkała na swojej fali                                                |
| position | numer stanowiska, przy którym odbyła się ta rozmowa                                      |
| positin1 | numer stanowiska, od którego ta osoba zaczynała wieczór (literówka w oryginalnej nazwie) |
| order    | która z kolei randka tego wieczoru (1 = pierwsza, 2 = druga, …)                          |




## Partner, znany z ankiety przed spotkaniem


| kolumna  | znaczenie                                                |
| -------- | -------------------------------------------------------- |
| int_corr | korelacja zainteresowań tej osoby i partnera, od −1 do 1 |
| samerace | 1 = ta sama rasa albo pochodzenie, 0 = różne             |
| age_o    | wiek partnera                                            |
| race_o   | rasa partnera, te same kody co `race`                    |
| pf_o_att | jak ważna jest dla partnera atrakcyjność                 |
| pf_o_sin | jak ważna jest dla partnera szczerość                    |
| pf_o_int | jak ważna jest dla partnera inteligencja                 |
| pf_o_fun | jak ważne jest dla partnera poczucie humoru              |
| pf_o_amb | jak ważna jest dla partnera ambicja                      |
| pf_o_sha | jak ważne są dla partnera wspólne zainteresowania        |


`pf` = preference, czyli preferencja partnera z jego ankiety rejestracyjnej.

## Profil uczestnika


| kolumna  | znaczenie                                                               |
| -------- | ----------------------------------------------------------------------- |
| age      | wiek                                                                    |
| gender   | 0 = kobieta, 1 = mężczyzna                                              |
| field    | kierunek studiów, tekst                                                 |
| field_cd | kierunek studiów, kod 1–18 (tabela niżej)                               |
| undergra | uczelnia licencjacka, tekst                                             |
| mn_sat   | mediana wyniku SAT tej uczelni, przybliżenie poziomu szkoły             |
| tuition  | czesne tej uczelni                                                      |
| race     | rasa albo pochodzenie, kod 1–6                                          |
| imprace  | jak ważne jest, żeby partner był tej samej rasy, skala 1–10             |
| imprelig | jak ważne jest, żeby partner był tego samego wyznania, skala 1–10       |
| from     | skąd osoba pochodzi, tekst                                              |
| zipcode  | kod pocztowy miejsca, w którym dorastała                                |
| income   | mediana dochodu gospodarstw w tym kodzie pocztowym                      |
| goal     | po co przyszła na speed dating, kod 1–6                                 |
| date     | jak często chodzi na randki, kod 1–7; to nie jest data kalendarzowa     |
| go_out   | jak często wychodzi z domu, kod 1–7                                     |
| career   | planowany zawód, tekst                                                  |
| career_c | planowany zawód, kod 1–17                                               |
| exphappy | jak bardzo liczy na udany wieczór, skala 1–10                           |
| expnum   | ilu z około 20 partnerów według niej będzie chciało kolejnego spotkania |




### field_cd

1 prawo, 2 matematyka, 3 nauki społeczne / psychologia, 4 medycyna / biotechnologia, 5 inżynieria, 6 anglistyka / pisanie / dziennikarstwo, 7 historia / religia / filozofia, 8 biznes / ekonomia / finanse, 9 edukacja, 10 biologia / chemia / fizyka, 11 praca socjalna, 12 studia licencjackie / brak decyzji, 13 politologia / stosunki międzynarodowe, 14 film, 15 sztuka, 16 języki, 17 architektura, 18 inne.

### race

1 czarnoskóry / Afroamerykanin, 2 biały / Europejczyk, 3 latynoski, 4 azjatycki / wyspy Pacyfiku, 5 rdzenny Amerykanin, 6 inne.

### goal

1 fajny wieczór, 2 poznać nowych ludzi, 3 zdobyć randkę, 4 poważny związek, 5 żeby móc powiedzieć, że byłem, 6 inne.

### date i go_out

1 kilka razy w tygodniu, 2 dwa razy w tygodniu, 3 raz w tygodniu, 4 dwa razy w miesiącu, 5 raz w miesiącu, 6 kilka razy w roku, 7 prawie nigdy.

### career_c

1 prawnik, 2 nauka / badania, 3 psycholog, 4 lekarz, 5 inżynier, 6 sztuka / rozrywka, 7 bankowość / konsulting / biznes, 8 nieruchomości, 9 sprawy międzynarodowe / pomoc humanitarna, 10 brak decyzji, 11 praca socjalna, 12 logopedia, 13 polityka, 14 sport, 15 inne, 16 dziennikarstwo, 17 architektura.

## Zainteresowania

Każda kolumna to ocena 1–10, jak bardzo osoba lubi daną rzecz.


| kolumna  | znaczenie           |
| -------- | ------------------- |
| sports   | uprawianie sportu   |
| tvsports | oglądanie sportu    |
| exercise | ćwiczenia, siłownia |
| dining   | jedzenie na mieście |
| museums  | muzea, galerie      |
| art      | sztuka              |
| hiking   | wędrówki, biwak     |
| gaming   | gry                 |
| clubbing | taniec, kluby       |
| reading  | czytanie            |
| tv       | oglądanie telewizji |
| theater  | teatr               |
| movies   | filmy               |
| concerts | koncerty            |
| music    | muzyka              |
| shopping | zakupy              |
| yoga     | joga, medytacja     |




## Preferencje i samoocena z rejestracji


| kolumna  | znaczenie                                                                        |
| -------- | -------------------------------------------------------------------------------- |
| attr1_1  | ile punktów daje atrakcyjności u partnera                                        |
| sinc1_1  | ile punktów daje szczerości u partnera                                           |
| intel1_1 | ile punktów daje inteligencji u partnera                                         |
| fun1_1   | ile punktów daje poczuciu humoru u partnera                                      |
| amb1_1   | ile punktów daje ambicji u partnera                                              |
| shar1_1  | ile punktów daje wspólnym zainteresowaniom                                       |
| attr2_1  | ile punktów płeć przeciwna daje według tej osoby atrakcyjności                   |
| sinc2_1  | ile punktów płeć przeciwna daje według tej osoby szczerości                      |
| intel2_1 | ile punktów płeć przeciwna daje według tej osoby inteligencji                    |
| fun2_1   | ile punktów płeć przeciwna daje według tej osoby poczuciu humoru                 |
| amb2_1   | ile punktów płeć przeciwna daje według tej osoby ambicji                         |
| shar2_1  | ile punktów płeć przeciwna daje według tej osoby wspólnym zainteresowaniom       |
| attr4_1  | ile punktów osoby tej samej płci dają według tej osoby atrakcyjności             |
| sinc4_1  | ile punktów osoby tej samej płci dają według tej osoby szczerości                |
| intel4_1 | ile punktów osoby tej samej płci dają według tej osoby inteligencji              |
| fun4_1   | ile punktów osoby tej samej płci dają według tej osoby poczuciu humoru           |
| amb4_1   | ile punktów osoby tej samej płci dają według tej osoby ambicji                   |
| shar4_1  | ile punktów osoby tej samej płci dają według tej osoby wspólnym zainteresowaniom |
| attr3_1  | własna ocena swojej atrakcyjności, 1–10                                          |
| sinc3_1  | własna ocena swojej szczerości, 1–10                                             |
| intel3_1 | własna ocena swojej inteligencji, 1–10                                           |
| fun3_1   | własna ocena swojego poczucia humoru, 1–10                                       |
| amb3_1   | własna ocena swojej ambicji, 1–10                                                |
| attr5_1  | jak atrakcyjnego widzą mnie inni, 1–10                                           |
| sinc5_1  | jak szczerego widzą mnie inni, 1–10                                              |
| intel5_1 | jak inteligentnego widzą mnie inni, 1–10                                         |
| fun5_1   | jak zabawnego widzą mnie inni, 1–10                                              |
| amb5_1   | jak ambitnego widzą mnie inni, 1–10                                              |


