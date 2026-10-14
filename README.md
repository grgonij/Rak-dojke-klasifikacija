# Predviđanje malignosti tumora dojke strojnim učenjem

Projekt iz kolegija **Uvod u umjetnu inteligenciju** (Veleučilište u Bjelovaru).
Binarna klasifikacija tumora dojke (zloćudan / dobroćudan) na temelju mjerenja staničnih jezgri.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KORISNIK/REPOZITORIJ/blob/main/Projekt_UUI_Rak_dojke.ipynb)

## Opis

Cilj je na temelju 30 numeričkih značajki izračunatih iz digitaliziranih slika tankoigličnog aspirata (radijus, tekstura, opseg, površina, glatkoća...) predvidjeti je li tumor zloćudan ili dobroćudan. Uspoređuju se tri klasifikacijska modela, a najbolji se bira prema F1-mjeri.

## Skup podataka

**Breast Cancer Wisconsin (Diagnostic)**, UCI Machine Learning Repository, učitan putem `sklearn.datasets.load_breast_cancer`.
569 uzoraka, 30 značajki, bez nedostajućih vrijednosti.

## Tijek rada

1. **Obrada podataka** – provjera nedostajućih vrijednosti, kodiranje dijagnoze, podjela 80/20 (stratificirano), standardizacija (`StandardScaler`)
2. **Analiza značajki** – distribucije, korelacijska matrica, odabir 10 najboljih značajki (`SelectKBest`, ANOVA F-test)
3. **Modeli** – Logistička regresija, SVM (RBF kernel), Random Forest
4. **Kros-validacija** – 5-struka stratificirana (`StratifiedKFold`)
5. **Evaluacija** – accuracy, precision, recall, F1-score, matrica zabune

## Rezultati (testni skup, 114 uzoraka)

| Model | Accuracy | Precision | Recall | F1-score |
|---|---|---|---|---|
| **SVM (RBF)** | **0.9561** | 0.9589 | **0.9722** | **0.9655** |
| Random Forest | 0.9474 | 0.9583 | 0.9583 | 0.9583 |
| Logistička regresija | 0.9474 | 0.9714 | 0.9444 | 0.9577 |

Najbolji model prema F1-mjeri: **SVM (RBF)**.

## Pokretanje

**Google Colab:** otvori `Projekt_UUI_Rak_dojke.ipynb` (gumb gore ili *File → Upload notebook*) i odaberi *Runtime → Run all*.

**Lokalno:**

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook Projekt_UUI_Rak_dojke.ipynb
```

## Tehnologije

Python, pandas, NumPy, scikit-learn, matplotlib, seaborn

## Napomena

Edukativni prototip izrađen u sklopu kolegija. Nije medicinski alat i ne smije zamijeniti stvarnu dijagnozu.
