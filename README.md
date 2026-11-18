# ML-SpeedDatingExperiment

Projekt z przedmiotu *Zaawansowane metody uczenia maszynowego* (PK, DS1).
Cel: przewidzieć, czy spotkanie w eksperymencie speed dating zakończy się **matchem**
(obie osoby chcą się spotkać ponownie), na podstawie informacji dostępnych **przed** rozmową.

Raport z etapu 1: [`raport/raport_etap1.pdf`](raport/raport_etap1.pdf).

## Dane

Dane nie są przechowywane w repozytorium. Pochodzą z Kaggle:
[Speed Dating Experiment](https://www.kaggle.com/datasets/annavictoria/speed-dating-experiment)
(Fisman i in., 2006).

Pobranie:
- automatycznie – notatnik 1 pobiera zbiór przez `kagglehub`, albo
- ręcznie – pobierz archiwum ze strony Kaggle i rozpakuj `Speed Dating Data.csv` do katalogu `data/`.

## Uruchomienie

Środowisko: Python 3.12+ (testowane na 3.13 i 3.14), biblioteki z `requirements.txt`.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Notatniki uruchamiaj po kolei:

| Notatnik | Co robi | Wynik |
|---|---|---|
| `1_speed_dating_experiment-primary_analysis.ipynb` | pobranie danych, pierwszy przegląd: rozmiar, braki, błędne wartości, warianty zapisu tekstu | – |
| `2_preparing_data.ipynb` | połączenie wierszy kobiety i mężczyzny w jedno spotkanie, cel `outcome`, usunięcie cech zapisanych po decyzji, poprawki tekstu i liczb | `data/meetings.csv` |
| `3_data_analysis.ipynb` | EDA: braki, błędy, typy kolumn, wartości odstające, rozkłady, korelacje; **podział grupowy train/test po falach** | `data/meetings_train.csv`, `data/meetings_test.csv`, `data/test_waves.txt` |
| `4_etap1_model.ipynb` | etap 1: selekcja cech, korekta skal, 5 metod imputacji z kontrolą rozkładów, potok przetwarzania, model bazowy na 10 ziarnach, wpływ rozmiaru zbioru treningowego, wykres 4 zmiennych, ocena na teście | `out/*.png`, `out/wyniki_etap1.json`, `raport/wyniki.tex`, `raport/tabela_walidacja.tex` |

Cały notatnik 4 wykonuje się w ok. 3–4 minuty na CPU.

## Raport

Źródło w LaTeX (szablon prowadzącego): `raport/raport_etap1.tex`.
Liczby w raporcie pochodzą z plików generowanych przez notatnik 4 (`raport/wyniki.tex`, `raport/tabela_walidacja.tex`).

```bash
cd raport
latexmk -pdf raport_etap1.tex
```

## Najważniejsze decyzje (etap 1)

- **Jednostka obserwacji:** spotkanie (para kobieta–mężczyzna), 4184 spotkania; match w ok. 16% z nich.
- **Bez przecieku celu:** usunięte oceny wystawione w trakcie rozmowy i ankiety z kolejnych tygodni.
- **Podział grupowy po falach:** ta sama osoba nie występuje w train i test.
- **Wszystkie uczone przekształcenia** (imputacja, skalowanie, one-hot) dopasowywane tylko na części treningowej, wewnątrz `Pipeline`.
- **Metryka główna:** ROC AUC; pomocnicze: average precision, balanced accuracy, F1 klasy match.
